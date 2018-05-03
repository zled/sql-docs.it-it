---
title: Uso di Always Encrypted con driver PHP per SQL Server | Documenti Microsoft
ms.date: 01/08/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
manager: mbarwin
ms.openlocfilehash: cc5ccc20d4a1a4324933ea64b9126f10df66dd26
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-always-encrypted-with-the-php-drivers-for-sql-server"></a>Uso di Always Encrypted con driver PHP per SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="applicable-to"></a>Applicabile a
 -   5.2 del driver Microsoft per PHP per SQL Server
 
## <a name="introduction"></a>Introduzione

In questo articolo vengono fornite informazioni su come sviluppare applicazioni PHP usando [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) e il [driver PHP per SQL Server](../../connect/php/Microsoft-php-driver-for-sql-server.md).

Always Encrypted consente alle applicazioni client di eseguire la crittografia dei dati sensibili senza mai rivelare i dati o le chiavi di crittografia a SQL Server o al database SQL di Azure. Un Always Encrypted abilitato driver, ad esempio il Driver ODBC per SQL Server, in modo trasparente esegue la crittografia e decrittografia dei dati sensibili nell'applicazione client. Il driver determina automaticamente i parametri di query corrispondenti alle colonne di database con dati sensibili (protette mediante Always Encrypted) e crittografa i valori di tali parametri prima di passare i dati a SQL Server o al database SQL di Azure. Analogamente, il driver esegue in modo trasparente la decrittografia dei dati, recuperati dalle colonne di database crittografate nei risultati delle query. Per altre informazioni, vedere [Always Encrypted (motore di database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). I driver di PHP per SQL Server utilizzano il Driver ODBC per SQL Server crittografare dati sensibili.

## <a name="prerequisites"></a>Prerequisiti

 -   Configurare Always Encrypted nel database. Questa configurazione implica il provisioning delle chiavi Always Encrypted e la configurazione delle crittografia per le colonne di database selezionato. Se non è presente un database in cui Always Encrypted è configurato, seguire le istruzioni fornite nel blog di [introduzione a Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). In particolare, il database deve contenere le definizioni dei metadati per una tabella contenente uno o più colonne crittografate con tale CEK Column Master Key (CMK) e una chiave di crittografia di colonna (CEK).
 -   Verificare che il Driver ODBC per SQL Server versione 17 o successiva sia installato nel computer di sviluppo. Per informazioni dettagliate, vedere [ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="enabling-always-encrypted-in-a-php-application"></a>Come abilitare Always Encrypted in un'applicazione PHP

È il modo più semplice per abilitare la crittografia dei parametri destinati alle colonne crittografate e la decrittografia dei risultati della query impostando il valore di `ColumnEncryption` parola chiave di stringa di connessione da `Enabled`. Di seguito è riportati esempi di abilitazione di Always Encrypted nel driver PDO_SQLSRV e SQLSRV:

SQLSRV:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled");
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

Abilitazione di Always Encrypted non è sufficiente per la crittografia o decrittografia riesca. è inoltre necessario assicurarsi che:
 -   L'applicazione ha le autorizzazioni di database VIEW ANY COLUMN MASTER KEY DEFINITION e VIEW ANY COLUMN ENCRYPTION KEY DEFINITION, necessarie per accedere ai metadati sulle chiavi Always Encrypted nel database. Per informazioni dettagliate, vedere [del Database l'autorizzazione](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
 -   L'applicazione può accedere la CMK che protegge l'eseguono per eseguire query su tali colonne crittografate. Questo requisito dipende dal provider dell'archivio chiavi contenente la chiave CMK. Per altre informazioni, vedere [utilizzo di archivi chiavi Master della colonna](#working-with-column-master-key-stores).

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Recupero e modifica di dati nelle colonne crittografate

Dopo aver abilitato Always Encrypted in una connessione, è possibile usare le API SQLSRV standard (vedere [riferimento all'API del Driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)) o le API PDO_SQLSRV (vedere [riferimento all'API del Driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)) per recuperare o modificare i dati nelle colonne crittografate del database. Presupponendo che l'applicazione ha le autorizzazioni di database necessari e possa accedere alla chiave master di colonna, il driver esegue la crittografia eventuali parametri di query che fanno riferimento alle colonne crittografate e decrittografare i dati recuperati dalle colonne crittografate, un comportamento in modo trasparente al applicazione come se le colonne non sono state crittografate.

Se Always Encrypted non è abilitato, le query con parametri destinati alle colonne crittografate non riuscire. Ancora i dati possono essere recuperati dalle colonne crittografate, purché la query non ha parametri destinati alle colonne crittografate. Tuttavia, il driver non tenta qualsiasi decrittografia e l'applicazione riceve i dati crittografati binari (come matrici di byte).

Nella tabella seguente viene riepilogato il comportamento delle query, a seconda se Always Encrypted è abilitato o meno:

| Caratteristica query | Always Encrypted è abilitato e l'applicazione può accedere le chiavi e i metadati della chiave | Always Encrypted è abilitato e non può accedere a chiavi o i metadati della chiave | Always Encrypted è disabilitato | | Parametri destinati alle colonne crittografate. | I valori dei parametri vengono crittografati in modo trasparente. | Errore | Errore | | Il recupero dei dati dalle colonne crittografate, senza parametri destinati alle colonne crittografate. | I risultati dalle colonne crittografate vengono decrittografati in modo trasparente. L'applicazione riceve valori di colonna in testo normale. | Errore | I risultati dalle colonne crittografate non vengono decrittografati. L'applicazione riceve valori crittografati come matrici di byte. |
 
Gli esempi seguenti illustrano il recupero e la modifica dei dati nelle colonne crittografate. Negli esempi si presuppone una tabella con lo schema seguente. Le colonne SSN e Birthdate nascita sono crittografate.
```
CREATE TABLE [dbo].[Patients](
 [PatientId] [int] IDENTITY(1,1),
 [SSN] [char](11) COLLATE Latin1_General_BIN2
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL,
 [BirthDate] [date]
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

### <a name="data-insertion-example"></a>Esempio di inserimento dei dati

Gli esempi seguenti illustrano come utilizzare il driver SQLSRV e PDO_SQLSRV per inserire una riga nella tabella dei pazienti. Si noti quanto segue:
 -   Il codice di esempio non contiene alcun elemento specifico per la crittografia. Il driver rileva automaticamente e crittografa i valori dei parametri SSN e BirthDate, che interessano le colonne crittografate. Questo meccanismo esegue la crittografia trasparente all'applicazione.
 -   I valori inseriti nelle colonne di database, incluse le colonne crittografate, vengono passati come parametri associati. Durante l'utilizzo di parametri è facoltativa quando si inviano i valori alle colonne non crittografate (anche se è consigliata perché consente di impedire attacchi SQL injection), è necessario per i valori destinati alle colonne crittografate. Se i valori inseriti nelle colonne SSN o BirthDate sono stati passati come valori letterali incorporati nell'istruzione della query, la query avrà esito negativo poiché il driver non tenta di crittografare o elaborare valori letterali nelle query. Di conseguenza, il server li rifiuterà come incompatibili con le colonne crittografate.
 -   Quando si inseriscono valori utilizzando i parametri di associazione, un tipo SQL che è identico al tipo di dati della colonna di destinazione o la cui conversione al tipo di dati della colonna di destinazione è supportata deve essere passato al database. Questo è un requisito perché Always Encrypted supporta alcune conversioni di tipo (per informazioni dettagliate, vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)). I due driver PHP, SQLSRV e PDO_SQLSRV, ognuno presenta un meccanismo per consentire all'utente di determinare il tipo SQL del valore. Pertanto, l'utente non dovrà fornire in modo esplicito il tipo SQL.
  -   Per il driver SQLSRV, l'utente è disponibili due opzioni:
   -   Si basano su PHP driver per determinare e impostare il tipo SQL a destra. In questo caso, l'utente deve utilizzare `sqlsrv_prepare` e `sqlsrv_execute` per eseguire una query con parametri.
   -   Impostare in modo esplicito il tipo SQL.
  -   Per il driver PDO_SQLSRV, l'utente non hanno la possibilità di impostare in modo esplicito il tipo SQL di un parametro. Il driver PDO_SQLSRV automaticamente illustrano come determinare il tipo SQL quando si associa un parametro.
 -   Per i driver determinare il tipo SQL, esistono alcune limitazioni:
  -   Driver SQLSRV:
   -   Se si desidera ottenere il driver per determinare i tipi SQL per le colonne crittografate, l'utente deve utilizzare `sqlsrv_prepare` e `sqlsrv_execute`.
   -   Se `sqlsrv_query` è si preferisce, l'utente è responsabile per specificare i tipi SQL per tutti i parametri. Il tipo SQL specificato deve includere la lunghezza della stringa per i tipi di stringa e la scala e precisione per i tipi decimali.
  -   PDO_SQLSRV Driver:
   -   L'attributo di istruzione `PDO::SQLSRV_ATTR_DIRECT_QUERY` non è supportato in una query con parametri.
   -   L'attributo di istruzione `PDO::ATTR_EMULATE_PREPARES` non è supportato in una query con parametri.
   
Driver SQLSRV e [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel;
$birthDate = "1996-10-19";
$params = array($ssn, $firstName, $lastName, $birthDate);
// during sqlsrv_prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = sqlsrv_prepare($conn, $query, $params);
sqlsrv_execute($stmt);
```

Driver SQLSRV e [sqlsrv_query](../../connect/php/sqlsrv-query.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel";
$birthDate = "1996-10-19";
// need to provide the SQL types for ALL parameters  
// note the SQL types (including the string length) have to be the same at the column definition
$params = array(array(&$ssn, null, null, SQLSRV_SQLTYPE_CHAR(11)),
                array(&$firstName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$lastName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$birthDate, null, null, SQLSRV_SQLTYPE_DATE));
sqlsrv_query($conn, $query, $params);
```

Driver PDO_SQLSRV e [PDO:: Prepare](../../connect/php/pdo-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Able";
$birthDate = "1996-10-19";
// during PDO::prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
$stmt->bindParam(2, $firstName);
$stmt->bindParam(3, $lastName);
$stmt->bindParam(4, $birthDate);
$stmt->execute();
```

### <a name="plaintext-data-retrieval-example"></a>Esempio di recupero dei dati di testo normale

Gli esempi seguenti illustrano il filtraggio dei dati in base a valori crittografati e il recupero dei dati di testo normale dalle colonne crittografate usando il driver SQLSRV e PDO_SQLSRV. Si noti quanto segue:
 -   Il valore utilizzato nella clausola WHERE per filtrare la colonna SSN deve essere passato usando il parametro di associazione, in modo che il driver possibile codificarli in modo trasparente prima dell'invio al server.
 -   Quando si esegue una query con parametri associati, i driver PHP determina automaticamente il tipo SQL per l'utente, a meno che l'utente specifica in modo esplicito il tipo SQL quando si usa il driver SQLSRV.
 -   Tutti i valori stampati dal programma sono in testo non crittografato, poiché il driver decrittografa in modo trasparente i dati recuperati dalle colonne SSN e BirthDate.
 
Nota: Le query possono eseguire confronti di uguaglianza nelle colonne crittografate a solo se la crittografia deterministica. Per ulteriori informazioni, vedere [crittografia selezionando deterministica o casuale](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = sqlsrv_prepare($conn, $query, array(&$ssn));
// during sqlsrv_execute, the driver encrypts the ssn value and passes it to the database
sqlsrv_execute($stmt);
// fetch like usual
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
// during PDOStatement::execute, the driver encrypts the ssn value and passes it to the database
$stmt->execute();
// fetch like usual
$row = $stmt->fetch();
```

### <a name="ciphertext-data-retrieval-example"></a>Esempio di recupero dei dati di testo crittografato

Se Always Encrypted non è abilitato, una query può comunque recuperare dati dalle colonne crittografate, a condizione che non presenti parametri destinati alle colonne crittografate.

Gli esempi seguenti illustrano il recupero dei dati crittografati binari dalle colonne crittografate usando il driver SQLSRV e PDO_SQLSRV. Si noti quanto segue:
 -   Come Always Encrypted non è abilitato nella stringa di connessione, la query restituisce i valori crittografati di SSN e BirthDate come matrici di byte (il programma converte i valori in stringhe).
 -   Una query che recupera dati dalle colonne crittografate con Always Encrypted disabilitato può avere parametri, a condizione che nessuno dei parametri sia destinato a una colonna crittografata. Il seguente query per i filtri LastName, non è crittografata nel database. Se la query filtrerà per SSN o BirthDate, la query avrà esito negativo.
 
SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = sqlsrv_prepare($conn, $query, array(&$lastName));
sqlsrv_execute($stmt);
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $lastName);
$stmt->execute();
$row = $stmt->fetch();
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Come evitare i problemi comuni quando si eseguono query su colonne crittografate

In questa sezione descrive le categorie di errori quando si eseguono query su colonne crittografate da applicazioni PHP e alcune indicazioni su come evitare il problema.

#### <a name="unsupported-data-type-conversion-errors"></a>Errori di conversione dei tipi di dati non supportati

Always Encrypted supporta alcune conversioni per i tipi di dati crittografati. Vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) per un elenco dettagliato delle conversioni di tipo supportato. Per evitare errori di conversione dei tipi di dati, eseguire le operazioni seguenti:
 -   Quando si utilizza il driver SQLSRV con `sqlsrv_prepare` e `sqlsrv_execute` il tipo SQL, la dimensione della colonna e il numero di cifre decimali del parametro viene determinato automaticamente.
 -   Quando si utilizza il driver PDO_SQLSRV per eseguire una query, il tipo SQL con la dimensione della colonna e il numero di cifre decimali del parametro è determinato automaticamente anche
 -   Quando si utilizza il driver SQLSRV con `sqlsrv_query` per eseguire una query:
  -   Il tipo SQL del parametro è esattamente uguale al tipo della colonna di destinazione o la conversione dal tipo di SQL per il tipo della colonna è supportata.
  -   La precisione e la scala dei parametri destinati alle colonne del `decimal` e `numeric` tipi di dati di SQL Server è lo stesso di precisione e scala configurare per la colonna di destinazione.
  -   La precisione dei parametri destinati alle colonne di `datetime2`, `datetimeoffset`, o `time` tipi di dati di SQL Server non è maggiore della precisione per la colonna di destinazione, nella query che modificano la colonna di destinazione.
 -   Non utilizzare gli attributi di istruzione PDO_SQLSRV `PDO::SQLSRV_ATTR_DIRECT_QUERY` o `PDO::ATTR_EMULATE_PREPARES` in una query con parametri
 
#### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Errori causati dal passaggio di testo non crittografato anziché di valori crittografati

Qualsiasi valore destinato a una colonna crittografata deve essere crittografato prima dell'invio al server. Tenta di inserire, modificare o filtrare in base al valore di testo normale su un errore, viene generata una colonna crittografata. Per evitare tali errori, verificare quanto segue:
 -   Always Encrypted è abilitato (nella stringa di connessione, impostare il `ColumnEncryption` parola chiave da `Enabled`).
 -   Utilizzare il parametro di associazione per inviare dati destinati alle colonne crittografate. Nell'esempio seguente viene illustrata una query che filtra in modo errato una valore letterale/una costante in una colonna crittografata (SSN):
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

## <a name="controlling-performance-impact-of-always-encrypted"></a>Controllo dell'impatto di Always Encrypted sulle prestazioni

Poiché Always Encrypted è una tecnologia di crittografia lato client, si osserva la maggior parte dell'overhead delle prestazioni sul lato client, non nel database. A parte il costo delle operazioni di crittografia e decrittografia, le altre origini di overhead delle prestazioni nelle lato client sono:
 -   Round trip aggiuntivi al database per recuperare i metadati per i parametri di query.
 -   Chiamate a un archivio delle chiavi master delle colonne per accedere alla chiave master di una colonna.
 
### <a name="round-trips-to-retrieve-metadata-for-query-parameters"></a>Round trip per recuperare i metadati per i parametri di Query

Se Always Encrypted è abilitato per una connessione, il Driver ODBC, per impostazione predefinita, chiamerà [Sys. sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) per ogni query con parametri, passando l'istruzione di query (senza i valori dei parametri) a SQL Server . Questa stored procedure consente di analizzare l'istruzione di query per scoprire se i parametri devono essere crittografati e in tal caso, restituisce le informazioni relative alla crittografia per ogni parametro per consentire al driver di crittografarli.

Poiché i driver PHP consentono all'utente di associare un parametro in un'istruzione preparata senza fornire il codice SQL digitare, quando si associano un parametro in una connessione abilitato a Always Encrypted, chiamare i driver di PHP [SQLDescribeParam](../../odbc/reference/syntax/sqldescribeparam-function.md) di parametro per ottenere il tipo SQL, le dimensioni di colonna e cifre decimali. I metadati vengono quindi utilizzati per chiamare [SQLBindParameter]( ../../odbc/reference/syntax/sqlbindparameter-function.md). Questi aggiuntiva `SQLDescribeParam` chiamate non richiedono round trip aggiuntivi al database come il Driver ODBC ha già archiviate le informazioni sul lato client quando `sys.sp_describe_parameter_encryption` è stato chiamato.

I comportamenti precedenti garantiscono un elevato livello di trasparenza per l'applicazione client (e lo sviluppatore dell'applicazione) non è necessario essere a conoscenza di quali query accedono alle colonne crittografate, purché i valori destinati alle colonne crittografate vengono passati al driver in parametri.

A differenza di ODBC Driver for SQL Server, abilitazione di Always Encrypted a livello di istruzione/query non è ancora supportata dei driver PHP. 

### <a name="column-encryption-key-caching"></a>Chiave di crittografia di colonna la memorizzazione nella cache

Per ridurre il numero di chiamate a un archivio chiavi master della colonna per decrittografare le chiavi di crittografia di colonna (CEK), il driver memorizza nella cache il testo non crittografato eseguono in memoria. Dopo aver ricevuto la CEK che lo crittografati (chiave ECEK) dai metadati del database, il driver ODBC tenta innanzitutto di trovare CEK crittografato corrispondente al valore della chiave crittografato nella cache. Il driver chiama l'archivio chiavi contenente la chiave CMK solo se non si trova il testo non crittografato corrispondente CEK nella cache.

Nota: Nel Driver ODBC per SQL Server, le voci nella cache vengono rimossi dopo un timeout di due ore. Questo comportamento significa che per una determinata chiave ECEK, il driver contatta l'archivio chiavi una sola volta nel corso della durata dell'applicazione o ogni due ore, a seconda del valore è minore.

## <a name="working-with-column-master-key-stores"></a>Uso degli archivi delle chiavi master delle colonne

Per crittografare o decrittografare i dati, il driver deve ottenere una CEK configurato per la colonna di destinazione. Delle chiavi Cek vengono archiviate in formato crittografato (ECEKs) nei metadati del database. Ogni CEK dispone di una CMK corrispondente che è stata usata per crittografarlo. Il [dei metadati del database](../../t-sql/statements/create-column-master-key-transact-sql.md) non archivia la chiave CMK. contiene solo il nome dell'archivio chiavi e le informazioni che l'archivio delle chiavi è possibile utilizzare per individuare la chiave CMK.

Per ottenere il valore di testo normale di una chiave ECEK, il driver ottiene innanzitutto i metadati relativi sia la CEK e relativo CMK corrispondente e quindi utilizza queste informazioni per contattare l'archivio chiavi contenente la chiave CMK e lo richiede, per decrittografare la chiave ECEK. Il driver comunica con un archivio chiavi usando un provider dell'archivio chiavi.

Per il Driver Microsoft 5.2.0 per PHP per SQL Server, è supportato solo Provider dell'archivio certificati Windows. I due altri Keystore provider supportati dal Driver ODBC (insieme di credenziali chiave di Azure e Provider dell'archivio chiavi personalizzato) non sono ancora supportati.

### <a name="using-the-windows-certificate-store-provider"></a>Utilizzo del Provider dell'archivio certificati di Windows

Il Driver ODBC per SQL Server in Windows include un provider di archivio chiavi master di colonna predefinito per l'archivio certificati Windows, denominato `MSSQL_CERTIFICATE_STORE`. (Questo provider è disponibile in macOS o Linux). Con questo provider, la chiave CMK archiviata localmente nel computer client e alcuna configurazione aggiuntiva per l'applicazione non è necessario utilizzarlo con il driver. Tuttavia, l'applicazione deve poter accedere al certificato e la relativa chiave privata nell'archivio. Per altre informazioni, vedere [Creare e archiviare chiavi master della colonna (Always Encrypted)](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

## <a name="limitations-of-the-php-drivers-when-using-always-encrypted"></a>Limitazioni dei driver PHP quando si usa Always Encrypted

SQLSRV e PDO_SQLSRV:
 -   Supporto Linux/MacOS
  -   Linux/MacOS non supportano Provider dell'archivio certificati Windows e che è l'unico Provider di archivio chiavi attualmente supportato dai driver di PHP
 -   Forzare la crittografia parametro
 -   Abilitazione di Always Encrypted a livello di istruzione 
 
SQLSRV:
 -   Utilizzo `sqlsrv_query` per il parametro di associazione senza specificare il tipo SQL
 -   Utilizzo `sqlsrv_prepare` per l'associazione di parametri in un batch di istruzioni SQL  
 
PDO_SQLSRV solo:
 -   `PDO::SQLSRV_ATTR_DIRECT_QUERY` attributo di istruzione specificato in una query con parametri
 -   `PDO::ATTR_EMULATE_PREPARE` attributo di istruzione specificato in una query con parametri
 -   associazione dei parametri in un batch di istruzioni SQL
 
I driver PHP ereditano inoltre le limitazioni imposte dal Driver ODBC per SQL Server e il database. Vedere [limitazioni del driver ODBC quando si usa Always Encrypted](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) e [sempre crittografato dettagli delle funzionalità di](../../relational-databases/security/encryption/always-encrypted-database-engine.md#feature-details).  
  
## <a name="see-also"></a>Vedere anche  
[Guida di programmazione per il driver SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Riferimento all'API del Driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
