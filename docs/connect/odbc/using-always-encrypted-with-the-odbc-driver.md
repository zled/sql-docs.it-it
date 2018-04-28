---
title: Utilizzo di Always Encrypted con il Driver ODBC per SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 10/01/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02e306b8-9dde-4846-8d64-c528e2ffe479
caps.latest.revision: 3
ms.author: v-chojas
manager: craigg
author: MightyPen
ms.workload: On Demand
ms.openlocfilehash: 653e9680cdaac667f0a00fd84700f07210fffb5d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-always-encrypted-with-the-odbc-driver-for-sql-server"></a>Utilizzo di Always Encrypted con il Driver ODBC per SQL Server
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

### <a name="applicable-to"></a>Applicabile a

- ODBC Driver 13.1 for SQL Server
- Driver ODBC 17 per SQL Server

### <a name="introduction"></a>Introduzione

Questo articolo fornisce informazioni su come sviluppare applicazioni ODBC che utilizzano [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) e [ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

Always Encrypted consente alle applicazioni client di eseguire la crittografia dei dati sensibili senza mai rivelare i dati o le chiavi di crittografia a SQL Server o al database SQL di Azure. Un Always Encrypted abilitato driver, ad esempio il Driver ODBC per SQL Server, a tale scopo in modo trasparente la crittografia e decrittografia dei dati sensibili nell'applicazione client. Il driver determina automaticamente i parametri di query corrispondenti alle colonne di database con dati sensibili (protette mediante Always Encrypted) e crittografa i valori di tali parametri prima di passare i dati a SQL Server o al database SQL di Azure. Analogamente, il driver esegue in modo trasparente la decrittografia dei dati, recuperati dalle colonne di database crittografate nei risultati delle query. Per altre informazioni, vedere [Always Encrypted (motore di database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md).

### <a name="prerequisites"></a>Prerequisiti

Configurare Always Encrypted nel database. Ciò implica il provisioning di chiavi Always Encrypted e l'impostazione della crittografia per le colonne di database selezionate. Se non è presente un database in cui Always Encrypted è configurato, seguire le istruzioni fornite nel blog di [introduzione a Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). In particolare, il database deve contenere le definizioni dei metadati per una tabella contenente uno o più colonne crittografate con tale CEK Column Master Key (CMK) e una chiave di crittografia di colonna (CEK).

### <a name="enabling-always-encrypted-in-an-odbc-application"></a>Abilitazione di Always Encrypted in un'applicazione ODBC

È il modo più semplice per abilitare la crittografia di parametro e la decrittografia di colonna crittografata resultset impostando il valore di `ColumnEncryption` parola chiave della stringa di connessione **abilitato**. Di seguito è riportato un esempio di una stringa di connessione che abilita Always Encrypted:

```
SQLWCHAR *connString = L"Driver={ODBC Driver 13 for SQL Server};Server={myServer};Trusted_Connection=yes;ColumnEncryption=Enabled;";
```

Always Encrypted può anche essere abilitato nella configurazione di DSN, usando la stessa chiave e il valore (che verrà sostituito con l'impostazione stringa di connessione, se presente), o a livello di codice con il `SQL_COPT_SS_COLUMN_ENCRYPTION` attributo pre-connessione. Impostazione in questo modo esegue l'override del valore impostato nella stringa di connessione o DSN:

```
 SQLSetConnectAttr(hdbc, SQL_COPT_SS_COLUMN_ENCRYPTION, (SQLPOINTER)SQL_COLUMN_ENCRYPTION_ENABLE, 0);
```

Dopo aver abilitato per la connessione, è possibile modificare il comportamento di Always Encrypted per le singole query. Vedere [controllare le prestazioni impatto di Always Encrypted](#controlling-the-performance-impact-of-always-encrypted) seguito per ulteriori informazioni.

Si noti che l'abilitazione di Always Encrypted non è sufficiente per la crittografia o decrittografia riesca. è inoltre necessario assicurarsi che:

- L'applicazione abbia le autorizzazioni di database *VIEW ANY COLUMN MASTER KEY DEFINITION* e *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* , necessarie per accedere ai metadati sulle chiavi Always Encrypted nel database. Per informazioni dettagliate, vedere [autorizzazioni Database](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).

- L'applicazione può accedere la CMK che protegge delle chiavi Cek per eseguire query su tali colonne crittografate. Ciò dipende tuttavia il provider dell'archivio chiavi che archivia la chiave CMK. Vedere [utilizzo di archivi chiavi Master della colonna](#working-with-column-master-key-stores) per ulteriori informazioni.

### <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Recupero e modifica di dati nelle colonne crittografate

Dopo aver abilitato Always Encrypted in una connessione, è possibile utilizzare le API ODBC standard (vedere [codice di esempio ODBC](https://code.msdn.microsoft.com/windowsapps/ODBC-sample-191624ae/sourcecode?fileId=51137&pathId=1980325953) o [riferimento per programmatori ODBC](https://msdn.microsoft.com/library/ms714177(v=vs.85).aspx)) per recuperare o modificare i dati in colonne crittografate del database. Presupponendo che l'applicazione ha richiesto le autorizzazioni del database e può accedere alla chiave master di colonna, il driver consente di crittografare i parametri di query che interessano le colonne crittografate e decrittografare i dati recuperati dalle colonne crittografate, si comporta in modo trasparente per la applicazione come se le colonne non sono state crittografate.

Se non è abilitato crittografia sempre attiva, query con parametri che interessano le colonne crittografate avranno esito negativo. Ancora i dati possono essere recuperati dalle colonne crittografate, purché la query non ha parametri destinati alle colonne crittografate. Tuttavia, il driver non tenterà di qualsiasi decrittografia e l'applicazione riceverà i dati crittografati binari (come matrici di byte).

Nella tabella seguente viene riepilogato il comportamento delle query, a seconda se Always Encrypted è abilitato o meno:

|Caratteristica della query | Always Encrypted è abilitato e l'applicazione può accedere alle chiavi e ai metadati delle chiavi|Always Encrypted è abilitato e l'applicazione non può accedere alle chiavi o ai metadati delle chiavi | Always Encrypted è disabilitato|
|:---|:---|:---|:---|
| Parametri destinati alle colonne crittografate. | I valori dei parametri vengono crittografati in modo trasparente. | Errore | Errore|
| Il recupero dei dati dalle colonne crittografate, senza parametri destinati alle colonne crittografate.| I risultati delle colonne vengono decrittografati in modo trasparente. L'applicazione riceve valori di colonna in testo normale. | Errore | I risultati delle colonne crittografate non vengono decrittografate. L'applicazione riceve valori crittografati come matrici di byte.

Gli esempi seguenti illustrano il recupero e la modifica dei dati nelle colonne crittografate. Negli esempi si presuppone una tabella con lo schema seguente. Si noti che le colonne SSN e BirthDate nascita sono crittografate.

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
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY] )
 GO
```

#### <a name="data-insertion-example"></a>Esempio di inserimento dei dati

Questo esempio illustra come inserire una riga nella tabella Patients. Si noti quanto segue:

- Il codice di esempio non contiene alcun elemento specifico per la crittografia. Automaticamente, il driver rileva e crittografa i valori dei parametri SSN e data, che interessano le colonne crittografate. In questo modo la crittografia diventa trasparente per l'applicazione.

- I valori inseriti nelle colonne di database, incluse le colonne crittografate, vengono passati come parametri associati (vedere [funzione SQLBindParameter](https://msdn.microsoft.com/library/ms710963(v=vs.85).aspx)). Durante l'utilizzo di parametri è facoltativa quando si inviano i valori alle colonne non crittografate (anche se è consigliata perché consente di impedire attacchi SQL injection), è necessario per i valori destinati alle colonne crittografate. Se i valori inseriti nelle colonne SSN o BirthDate sono stati passati come valori letterali incorporati nell'istruzione della query, la query avrà esito negativo poiché il driver non tenta di crittografare o elaborare valori letterali nelle query. Di conseguenza, il server li rifiuterà come incompatibili con le colonne crittografate.

- Il tipo SQL del parametro inserito nella colonna SSN è impostato su SQL_CHAR, che esegue il mapping per il **char** il tipo di dati di SQL Server (`rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);`). Se il tipo del parametro è stato impostato su SQL_WCHAR, che esegue il mapping a **nchar**, la query avrà esito negativo perché Always Encrypted non supporta conversioni sul lato server da valori nchar crittografato ai valori crittografati char. Vedere [riferimento per programmatori ODBC: Appendice d: i tipi di dati](https://msdn.microsoft.com/library/ms713607.aspx) per informazioni sui mapping dei tipi di dati.

```
    SQL_DATE_STRUCT date;
    SQLLEN cbdate;   // size of date structure  

    SQLCHAR SSN[12];
    strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

    SQLWCHAR* firstName = L"Catherine";
    SQLWCHAR* lastName = L"Abel";
    SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

    // Initialize the date structure  
    date.day = 10;
    date.month = 9;
    date.year = 1996;

    // Size of structures   
    cbdate = sizeof(SQL_DATE_STRUCT);

    SQLRETURN rc = 0;

    string queryText = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?) ";

    rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

    //SSN
    rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);
    //FirstName
    rc = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)firstName, 0, &cbFirstName);
    //LastName
    rc = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)lastName, 0, &cbLastName);
    //BirthDate
    rc = SQLBindParameter(hstmt, 4, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 10, 0, (SQLPOINTER)&date, 0, &cbdate);

    rc = SQLExecute(hstmt);
```

#### <a name="plaintext-data-retrieval-example"></a>Esempio di recupero dei dati di testo normale

L'esempio seguente illustra come filtrare i dati in base ai valori crittografati e recuperare i dati in testo non crittografato dalle colonne crittografate. Si noti quanto segue:

- Il valore utilizzato nella clausola WHERE per filtrare la colonna SSN deve essere passato usando SQLBindParameter, in modo che il driver possibile codificarli in modo trasparente prima dell'invio al server.

- Tutti i valori stampati dal programma sarà in testo non crittografato, poiché il driver decrittografa in modo trasparente i dati recuperati dalle colonne SSN e BirthDate.

> [!NOTE]
> Le query possono eseguire confronti di uguaglianza nelle colonne crittografate solo se la crittografia deterministica. Per ulteriori informazioni, vedere [crittografia selezionando deterministica o casuale](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```
SQLCHAR SSN[12];
strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

SQLWCHAR* firstName = L"Catherine";
SQLWCHAR* lastName = L"Abel";
SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

SQLRETURN rc = 0;
string empty = "";
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] " + empty +
    "FROM  [dbo].[Patients]" +
    "WHERE " +
    "[SSN] = ? ";

rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

//SSN
rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);

rc = SQLExecute(hstmt);
HandleDiagnosticRecord(hstmt, SQL_HANDLE_STMT, rc);

SQL_DATE_STRUCT dateVal;
SQLWCHAR firstNameVal[50];
SQLWCHAR lastNameVal[50];
SQLCHAR SSNVal[12];
SQLLEN cbdate;   // size of date structure  

int rowcount = 0;
while (SQL_SUCCEEDED(SQLFetch(hstmt)))
{
    rowcount++;
    SQLGetData(hstmt, 1, SQL_C_CHAR, &SSNVal, 11, &cbSSN);
    SQLGetData(hstmt, 2, SQL_C_WCHAR, &firstNameVal, 50, &cbFirstName);
    SQLGetData(hstmt, 3, SQL_C_WCHAR, &lastNameVal, 50, &cbLastName);
    SQLGetData(hstmt, 4, SQL_C_TYPE_DATE, &dateVal, 10, &cbdate);        
}
```

#### <a name="ciphertext-data-retrieval-example"></a>Esempio di recupero dei dati di testo crittografato

Se Always Encrypted non è abilitato, una query può comunque recuperare dati dalle colonne crittografate, a condizione che non presenti parametri destinati alle colonne crittografate.

Nell'esempio seguente viene illustrato il recupero dei dati crittografati binari dalle colonne crittografate. Si noti quanto segue:

- Considerato che Always Encrypted non è abilitato nella stringa di connessione, la query restituirà i valori crittografati di SSN e BirthDate come matrici di byte (il programma converte i valori in stringhe).
- Una query che recupera dati dalle colonne crittografate con Always Encrypted disabilitato può avere parametri, a condizione che nessuno dei parametri sia destinato a una colonna crittografata. La query precedente filtra in base alla colonna LastName, non è crittografata nel database. Se la query avesse filtrato per SSN o data di nascita, avrebbe avuto esito negativo.


```
SQLCHAR SSN[12];
strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

SQLWCHAR* firstName = L"Catherine";
SQLWCHAR* lastName = L"Abel";
SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

SQLRETURN rc = 0;
string empty = "";
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] " + empty +
    "FROM  [dbo].[Patients]" +
    "WHERE " +
    "[LastName] = ?";

rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

//LastName
rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)lastName, 0, &cbLastName);

rc = SQLExecute(hstmt);
HandleDiagnosticRecord(hstmt, SQL_HANDLE_STMT, rc);

SQL_DATE_STRUCT dateVal;
SQLWCHAR firstNameVal[50];
SQLWCHAR lastNameVal[50];
SQLCHAR SSNVal[12];
SQLLEN cbdate;   // size of date structure  

int rowcount = 0;
while (SQL_SUCCEEDED(SQLFetch(hstmt)))
{
    rowcount++;
    SQLGetData(hstmt, 1, SQL_C_CHAR, &SSNVal, 11, &cbSSN);
    SQLGetData(hstmt, 2, SQL_C_WCHAR, &firstNameVal, 50, &cbFirstName);
    SQLGetData(hstmt, 3, SQL_C_WCHAR, &lastNameVal, 50, &cbLastName);
    SQLGetData(hstmt, 4, SQL_C_TYPE_DATE, &dateVal, 10, &cbdate);        
}
```

#### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Come evitare i problemi comuni quando si eseguono query su colonne crittografate

Questa sezione vengono descritte le categorie di errori durante l'esecuzione di query su colonne crittografate da applicazioni ODBC e alcune indicazioni su come evitare il problema.

##### <a name="unsupported-data-type-conversion-errors"></a>Errori di conversione dei tipi di dati non supportati

Always Encrypted supporta alcune conversioni per i tipi di dati crittografati. Vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) per un elenco dettagliato delle conversioni di tipo supportato. Per evitare errori di conversione di tipo di dati, assicurarsi di osservare i seguenti punti quando si utilizza la funzione SQLBindParameter con parametri destinati alle colonne crittografate:

- Il tipo SQL del parametro è esattamente uguale al tipo della colonna di destinazione o la conversione dal tipo di SQL per il tipo della colonna è supportata.

- La precisione e scala dei parametri destinati alle colonne di `decimal` e `numeric` tipi di dati di SQL Server è identico a quello la precisione e scala configurato per la colonna di destinazione.

- La precisione dei parametri destinati alle colonne di `datetime2`, `datetimeoffset`, o `time` tipi di dati di SQL Server non è maggiore della precisione per la colonna di destinazione, nella query che modificano la colonna di destinazione.  

##### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Errori causati dal passaggio di testo non crittografato anziché di valori crittografati

Qualsiasi valore destinato a una colonna crittografata deve essere crittografato prima dell'invio al server. Tenta di inserire, modificare o filtra in base a un valore di testo normale su una colonna crittografata comporterà un errore. Per evitare tali errori, verificare quanto segue:

- Always Encrypted è abilitato (nel DSN, la stringa di connessione prima che la connessione mediante l'impostazione di `SQL_COPT_SS_COLUMN_ENCRYPTION` attributo di connessione per una connessione specifica, o `SQL_SOPT_SS_COLUMN_ENCRYPTION` attributo dell'istruzione per un'istruzione specifica).

- Utilizzare la funzione SQLBindParameter per inviare dati destinati alle colonne crittografate. Nell'esempio seguente viene illustrata una query che filtra in modo errato una valore letterale/una costante in una colonna crittografata (SSN), anziché passare il valore letterale come argomento al SQLBindParameter.

```
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

### <a name="precautions-when-using-sqlsetpos-and-sqlmoreresults"></a>Precauzioni quando si utilizza SQLSetPos e SQLMoreResults

#### <a name="sqlsetpos"></a>SQLSetPos

Il `SQLSetPos` API consente a un'applicazione aggiornare le righe nel buffer, che sono stati associati SQLBindCol e in quale riga è stata precedentemente recuperati dati usando un set di risultati. A causa del comportamento di riempimento asimmetrica dei tipi a lunghezza fissa crittografati, è possibile modificare in modo imprevisto i dati di tali colonne durante l'esecuzione di aggiornamenti su altre colonne nella riga. Con AE, verranno inseriti i valori di caratteri di lunghezza fissa se il valore è inferiore alla dimensione del buffer.

Per attenuare questo problema, utilizzare il `SQL_COLUMN_IGNORE` flag per ignorare le colonne che non verranno aggiornate come parte di `SQLBulkOperations` e quando si utilizza `SQLSetPos` cursori basati su aggiornamenti.  Tutte le colonne che non vengono modificate direttamente dall'applicazione devono essere ignorate, sia per le prestazioni e per evitare il troncamento delle colonne che sono associati a un buffer *più piccoli* più le dimensioni effettive di (DB). Per ulteriori informazioni, vedere [riferimento alla funzione SQLSetPos](https://msdn.microsoft.com/library/ms713507(v=vs.85).aspx).

#### <a name="sqlmoreresults--sqldescribecol"></a>SQLMoreResults & SQLDescribeCol

Le applicazioni possono chiamare [SQLDescribeCol](https://msdn.microsoft.com/library/ms716289(v=vs.85).aspx) per restituire i metadati sulle colonne nelle istruzioni preparate.  Se Always Encrypted è abilitato, la chiamata `SQLMoreResults` *prima* chiamata `SQLDescribeCol` causa [sp_describe_first_result_set](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) da chiamare, che non restituisce il testo non crittografato metadati per le colonne crittografate. Per evitare questo problema, chiamare `SQLDescribeCol` su istruzioni preparate *prima* chiamata `SQLMoreResults`.

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Controllare l'impatto sulle prestazioni di crittografia sempre attiva

Poiché Always Encrypted è una tecnologia di crittografia lato client, si osserva la maggior parte dell'overhead delle prestazioni sul lato client, non nel database. A parte il costo delle operazioni di crittografia e decrittografia, le altre origini di overhead delle prestazioni nelle lato client sono:

- Round trip aggiuntivi al database per recuperare i metadati per i parametri di query.

- Chiamate a un archivio delle chiavi master delle colonne per accedere alla chiave master di una colonna.

Questa sezione descrive le ottimizzazioni delle prestazioni predefinite nel Driver ODBC per SQL Server e come sia possibile controllare l'impatto dei fattori sopra due sulle prestazioni.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Il controllo di round trip per recuperare i metadati per i parametri di Query

Se Always Encrypted è abilitato per una connessione, il driver, per impostazione predefinita, chiama [sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) per ogni query con parametri, passando l'istruzione di query (senza i valori dei parametri) a SQL Server. Questa stored procedure consente di analizzare l'istruzione di query per scoprire se i parametri devono essere crittografati e in tal caso, restituisce le informazioni relative alla crittografia per ogni parametro per consentire al driver di crittografarli. Il comportamento descritto garantisce un elevato livello di trasparenza per l'applicazione client: l'applicazione (e lo sviluppatore dell'applicazione) non è necessario essere a conoscenza di quali query accedono alle colonne crittografate, purché i valori destinati alle colonne crittografate vengano passati per il driver nei parametri.

### <a name="per-statement-always-encrypted-behavior"></a>Per ogni istruzione Always Encrypted comportamento

Per controllare l'impatto sulle prestazioni di recupero dei metadati di crittografia per le query con parametri, è possibile modificare il comportamento di Always Encrypted per singole query, se è stata abilitata per la connessione. In questo modo, è possibile assicurarsi che `sys.sp_describe_parameter_encryption` viene richiamato solo per le query con parametri destinati alle colonne crittografate. Si noti, tuttavia, che in questo modo, si riduce la trasparenza della crittografia: se si crittografano colonne aggiuntive nel database, potrebbe essere necessario modificare il codice dell'applicazione per allinearlo alle modifiche dello schema.

Per controllare il comportamento di un'istruzione Always Encrypted, chiamare la funzione SQLSetStmtAttr per impostare il `SQL_SOPT_SS_COLUMN_ENCRYPTION` attributo dell'istruzione a uno dei valori seguenti:

|Value|Description|
|-|-|
|`SQL_CE_DISABLED` (0)|Always Encrypted è disabilitato per l'istruzione|
|`SQL_CE_RESULTSETONLY` (1)|Solo la decrittografia. Set di risultati e i valori restituiti vengono decrittografati e parametri non vengono crittografati.|
|`SQL_CE_ENABLED` (3) | Always Encrypted sia abilitata e utilizzato per i parametri e i risultati|

Nuovo handle di istruzione creati da una connessione con crittografia sempre attiva è abilitata per impostazione predefinita a SQL_CE_ENABLED. Quelli creati da una connessione è disabilitata per impostazione predefinita a SQL_CE_DISABLED (e non è possibile abilitare crittografia sempre attiva su di essi).

Se la maggior parte delle query di un'applicazione client di accedere alle colonne crittografate, si consiglia quanto segue:

- Impostare il `ColumnEncryption` parola chiave della stringa di connessione `Enabled`.

- Impostare il `SQL_SOPT_SS_COLUMN_ENCRYPTION` attributo `SQL_CE_DISABLED` nelle istruzioni che non accedono a tutte le colonne crittografate. Consente di disabilitare sia la chiamata `sys.sp_describe_parameter_encryption` nonché tenta di decrittografare tutti i valori nel risultato impostato.
    
- Impostare il `SQL_SOPT_SS_COLUMN_ENCRYPTION` attributo `SQL_CE_RESULTSETONLY` nelle istruzioni che non dispone di parametri che richiedono la crittografia, ma che recuperano dati dalle colonne crittografate. Consente di disabilitare la chiamata `sys.sp_describe_parameter_encryption` e crittografia dei parametri. Risultati contenenti colonne crittografate continueranno a essere decrittografato.

## <a name="always-encrypted-security-settings"></a>Crittografia sempre attiva le impostazioni di sicurezza

### <a name="force-column-encryption"></a>Crittografia di colonna

Per applicare la crittografia di un parametro, impostare il `SQL_CA_SS_FORCE_ENCRYPT` campo Descrizione del parametro di implementazione (IPD) tramite una chiamata alla funzione SQLSetDescField. Un valore diverso da zero, il driver restituire un errore quando non viene restituito metadati di crittografia per il parametro associato.

```
SQLHDESC ipd;
SQLGetStmtAttr(hStmt, SQL_ATTR_IMP_PARAM_DESC, &ipd, 0, 0);
SQLSetDescField(ipd, paramNum, SQL_CA_SS_FORCE_ENCRYPT, (SQLPOINTER)TRUE, SQL_IS_SMALLINT);   
```

Se SQL Server indica al driver che il parametro non deve essere crittografato, le query che utilizzano il parametro avrà esito negativo. Questo fornisce protezione aggiuntiva contro attacchi alla sicurezza in cui un SQL Server compromesso fornisce al client, che potrebbe causare la divulgazione di dati di metadati di crittografia non corretti.

### <a name="column-encryption-key-caching"></a>Chiave di crittografia di colonna la memorizzazione nella cache

Per ridurre il numero di chiamate a un archivio chiavi master della colonna per decrittografare le chiavi di crittografia di colonna, il driver memorizza nella cache il testo non crittografato delle chiavi Cek in memoria. La cache CEK è globale per il driver e non sono associati a qualsiasi un'unica connessione. Dopo aver ricevuto la chiave ECEK dai metadati del database, il driver tenta innanzitutto di trovare CEK crittografato corrispondente al valore della chiave crittografato nella cache. Il driver chiama l'archivio chiavi contenente la chiave CMK solo se non si trova il testo non crittografato corrispondente CEK nella cache.

> [!NOTE]
> Nel Driver ODBC per SQL Server, le voci nella cache vengono rimossi dopo un timeout di due ore. Ciò significa che per una determinata chiave ECEK, il driver contatta l'archivio chiavi una sola volta durante il ciclo di vita dell'applicazione o ogni due ore, a seconda del valore è minore.

A partire da 17.1 il Driver ODBC per SQL Server, il timeout della cache CEK può essere regolato usando il `SQL_COPT_SS_CEKCACHETTL` attributo di connessione, che specifica il numero di secondi una CEK rimarrà nella cache. A causa della natura globale della cache, questo attributo può essere modificato da un handle di connessione valido per il driver. Quando la cache viene diminuito durata (TTL), eseguono esistente che supererebbe la nuova durata (TTL) inoltre vengono rimossi. Se è 0, non viene memorizzati nella cache eseguono.

### <a name="trusted-key-paths"></a>Percorsi principali attendibili

A partire 17.1 il Driver ODBC per SQL Server, il `SQL_COPT_SS_TRUSTEDCMKPATHS` attributo di connessione consente a un'applicazione richiedere che le operazioni di crittografia sempre attiva utilizzano solo un elenco di CMK, identificato dal relativo percorso di chiave specificato. Per impostazione predefinita, questo attributo è NULL, che indica che il driver accetta qualsiasi percorso della chiave. Per utilizzare questa funzionalità, impostare `SQL_COPT_SS_TRUSTEDCMKPATHS` in modo che punti a una stringa di caratteri wide delimitato da null, con terminazione null che elenca i percorsi di chiave consentiti. La memoria a cui fa riferimento questo attributo deve rimanere valida durante le operazioni di crittografia o decrittografia utilizzando l'handle di connessione in cui è impostato---su cui il driver viene verificato se il percorso CMK come specificato dai metadati del server soggetti in questo elenco. Se il percorso CMK non è presente nell'elenco, l'operazione ha esito negativo. L'applicazione può modificare il contenuto della memoria che punta questo attributo, per modificare l'elenco di CMK attendibile, senza impostare l'attributo nuovamente.

## <a name="working-with-column-master-key-stores"></a>Uso degli archivi delle chiavi master delle colonne

Per crittografare o decrittografare i dati, il driver deve ottenere una CEK configurato per la colonna di destinazione. Delle chiavi Cek vengono archiviate in formato crittografato (ECEKs) nei metadati del database. Ogni CEK dispone di una CMK corrispondente che è stata usata per crittografarlo. Il [dei metadati del database](../../t-sql/statements/create-column-master-key-transact-sql.md) non archivia la chiave CMK. contiene solo il nome dell'archivio chiavi e le informazioni che il file keystore è possibile utilizzare per individuare la chiave CMK.

Per ottenere il valore di testo normale di una chiave ECEK, il driver ottiene innanzitutto i metadati relativi a CEK sia la CMK corrispondente e quindi utilizza queste informazioni per contattare l'archivio chiavi contenente la chiave CMK e richiesta per decrittografare la chiave ECEK. Il driver comunica con un keystore utilizzando un provider dell'archivio chiavi.

### <a name="built-in-keystore-providers"></a>Provider di archivio chiavi predefinite

Il Driver ODBC per SQL Server viene fornito con i provider di archivio chiavi predefinite seguenti:

| Nome | Description | Nome del provider (metadati) |Disponibilità|
|:---|:---|:---|:---|
|Insieme di credenziali chiave di Azure |CMK archivi in un insieme di credenziali chiave di Azure | `AZURE_KEY_VAULT` |Windows, macOS, Linux|
|Archivio certificati Windows|Archivia CMK localmente nell'archivio di Windows| `MSSQL_CERTIFICATE_STORE`|Windows|

- È necessario assicurarsi che il nome del provider, configurato nei metadati della chiave master della colonna, sia corretto e che il percorso della chiave master di colonna conformi al formato del percorso della chiave per il provider è (o l'amministratore del database). È consigliabile configurare le chiavi usando strumenti come SQL Server Management Studio, che genera automaticamente i nomi di provider e i percorsi di chiave validi quando viene eseguita l'istruzione [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md) .

- È necessario verificare che l'applicazione può accedere alla chiave nell'archivio. Questa operazione potrebbe comportare concedendo l'accesso dell'applicazione per la chiave e/o dell'archivio chiavi, a seconda dell'archivio chiavi, o eseguire altri passaggi di configurazione specifica dell'archivio chiavi. Ad esempio, per accedere a un insieme di credenziali chiave di Azure, è necessario fornire le credenziali corrette per il file keystore.

### <a name="using-the-azure-key-vault-provider"></a>Utilizzo del Provider di Azure dell'insieme di credenziali chiave

L'insieme di credenziali delle chiavi di Azure rappresenta una scelta valida per archiviare e gestire le chiavi master delle colonne per Always Encrypted, soprattutto se le applicazioni sono ospitate in Azure. Il Driver ODBC per SQL Server in Linux, macOS e Windows include un provider di archivio chiavi master di colonna predefinito per insieme credenziali chiavi Azure. Vedere [insieme credenziali chiavi Azure - Step by Step](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/), [Guida introduttiva a insieme di credenziali chiave](https://azure.microsoft.com/documentation/articles/key-vault-get-started/), e [la creazione di chiavi Master della colonna nell'insieme di credenziali chiave di Azure](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2) per ulteriori informazioni sulla configurazione di una chiave di Azure Insieme di credenziali per crittografia sempre attiva.

Il driver supporta l'autenticazione a insieme di credenziali chiave di Azure usando i seguenti tipi di credenziali:

- Nome utente e Password: con questo metodo, le credenziali sono il nome di un utente di Azure Active Directory e la relativa password.

- ID client/segreto: con questo metodo, le credenziali sono un ID client dell'applicazione e un segreto dell'applicazione.

Per consentire al driver di utilizzare una CMK archiviati nell'insieme per la crittografia di colonna, utilizzare le parole chiave solo nella stringa di connessione seguenti:

|Tipo di credenziali| `KeyStoreAuthentication` |`KeyStorePrincipalId`| `KeyStoreSecret` |
|-|-|-|-|
|Username/password| `KeyVaultPassword`|Nome dell'entità utente|Password|
|ID/chiave privata client| `KeyVaultClientSecret`|ID client|Segreto|

#### <a name="example-connection-strings"></a>Stringhe di connessione di esempio

Le stringhe di connessione seguente viene illustrato come l'autenticazione a insieme di credenziali chiave di Azure con i due tipi di credenziali:

**ClientID/segreto**:

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultClientSecret;KeyStorePrincipalId=<clientId>;KeyStoreSecret=<secret>
```

**Username/Password**

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultPassword;KeyStorePrincipalId=<username>;KeyStoreSecret=<password>
```

Nessun altre modifiche all'applicazione ODBC devono utilizzare insieme per la memorizzazione CMK.

### <a name="using-the-windows-certificate-store-provider"></a>Utilizzo del Provider dell'archivio certificati di Windows

Il Driver ODBC per SQL Server in Windows include un provider di archivio chiavi master di colonna predefinito per l'archivio certificati di Windows, denominato `MSSQL_CERTIFICATE_STORE`. (Questo provider è disponibile in macOS o Linux). Con questo provider, la chiave CMK archiviata localmente nel computer client e alcuna configurazione aggiuntiva per l'applicazione non è necessario utilizzarlo con il driver. Tuttavia, l'applicazione deve poter accedere al certificato e la relativa chiave privata nell'archivio. Vedere [creare e archiviare chiavi Master della colonna (Always Encrypted)](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted) per ulteriori informazioni.

### <a name="using-custom-keystore-providers"></a>Utilizzo di provider di archivio chiavi personalizzato

Il Driver ODBC per SQL Server supporta anche i provider di archivio chiavi personalizzati di terze parti tramite l'interfaccia CEKeystoreProvider. In questo modo un'applicazione caricare, query e configurare i provider di archivio chiavi in modo che possono essere utilizzati dal driver per accedere alle colonne crittografate. Applicazioni possono interagire direttamente con un provider dell'archivio chiavi per crittografia delle chiavi Cek per l'archiviazione in SQL Server ed eseguire attività oltre che accedono a colonne crittografate con ODBC. Per ulteriori informazioni, vedere [provider archivio chiavi personalizzati](../../connect/odbc/custom-keystore-providers.md).

Due attributi di connessione vengono utilizzati per interagire con i provider di archivio chiavi personalizzato. ovvero:

- `SQL_COPT_SS_CEKEYSTOREPROVIDER`

- `SQL_COPT_SS_CEKEYSTOREDATA`

Il primo viene utilizzato per caricare ed enumerare i provider di archivio chiavi caricato, mentre quest'ultimo consente le comunicazioni di provider dell'applicazione. Questi attributi di connessione possono essere utilizzati in qualsiasi momento prima o dopo aver stabilito una connessione, poiché l'interazione del provider di applicazione non comporta la comunicazione con SQL Server. Tuttavia, poiché il driver non è stato ancora caricato, impostazione e recupero di questi attributi prima della connessione causerà essere elaborato da Gestione Driver e non può produrre i risultati previsti.

#### <a name="loading-a-keystore-provider"></a>Il caricamento di un Provider dell'archivio chiavi

L'impostazione di `SQL_COPT_SS_CEKEYSTOREPROVIDER` attributo di connessione consente a un'applicazione client caricare una libreria del provider, rendendo disponibili per utilizzare i provider di archivio chiavi in esso contenuti.

```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```
| Argomento | Description |
|:---|:---|
|`ConnectionHandle`|[Input] Handle di connessione. Deve essere un handle di connessione valida, ma caricati tramite l'handle di connessione di un provider sono accessibili da qualsiasi altro nello stesso processo.|
|`Attribute`|[Input] Attributo da impostare: il `SQL_COPT_SS_CEKEYSTOREPROVIDER` costante.|
|`ValuePtr`|[Input] Puntatore a una stringa di caratteri con terminazione null che specifica il nome del file della libreria del provider. Per SQLSetConnectAttrA, si tratta di una stringa (multibyte) ANSI. Per SQLSetConnectAttrW, questa è una stringa Unicode (wchar_t).|
|`StringLength`|[Input] La lunghezza della stringa ValuePtr o SQL_NTS.|

Il driver tenta di caricare la libreria identificata dal parametro ValuePtr utilizzando la libreria dinamica definita dalla piattaforma meccanismo di caricamento (`dlopen()` su Linux e macOS, `LoadLibrary()` in Windows), e aggiunge tutti i provider definiti al suo interno all'elenco di provider noto al driver. Potrebbero verificarsi i seguenti errori:

| Errore | Description |
|:--|:--|
|`CE203`|Impossibile caricare la libreria dinamica.|
|`CE203`|Il simbolo "CEKeyStoreProvider" esportato non è stato trovato nella libreria.|
|`CE203`|Uno o più provider nella raccolta sono già caricati.|

`SQLSetConnectAttr` Restituisce l'errore normale o valori di esito positivo e informazioni aggiuntive disponibili per gli eventuali errori che si sono verificati tramite il meccanismo di diagnostica ODBC standard.

> [!NOTE]
> Il programmatore di applicazioni è necessario assicurarsi che tutti i provider personalizzati vengono caricati prima di qualsiasi query richiesta viene inviata tramite qualsiasi connessione. In caso contrario, genera l'errore:

| Errore | Description |
|:--|:--|
|`CE200`|Provider dell'archivio chiavi %1 non trovato. Verificare che la libreria del provider appropriato keystore è stata caricata.|

> [!NOTE]
> Gli implementatori di provider di archivio chiavi devono evitare di utilizzare `MSSQL` nel nome dei provider personalizzati. Il termine è riservato esclusivamente per l'utilizzo di Microsoft e può causare conflitti con i provider predefiniti future. Utilizzando questo termine nel nome di un provider personalizzato può comportare un avviso di ODBC.

#### <a name="getting-the-list-of-loaded-providers"></a>Recupero dell'elenco dei provider caricato

Recupero di questo attributo di connessione consente a un'applicazione client determinare i provider di archivio chiavi attualmente caricati nel driver (incluse quelle compilate). Questa operazione può essere eseguita solo dopo la connessione.

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```
| Argomento | Description |
|:---|:---|
|`ConnectionHandle`|[Input] Handle di connessione. Deve essere un handle di connessione valida, ma caricati tramite l'handle di connessione di un provider sono accessibili da qualsiasi altro nello stesso processo.|
|`Attribute`|[Input] Attributo da recuperare: il `SQL_COPT_SS_CEKEYSTOREPROVIDER` costante.|
|`ValuePtr`|[Output] Puntatore alla memoria in cui restituire il nome del provider caricato successivo.|
|`BufferLength`|[Input] La lunghezza del buffer ValuePtr.|
|`StringLengthPtr`|[Output] Un puntatore a un buffer in cui restituire il numero totale di byte (escluso il carattere di terminazione null) disponibile per restituire \*ValuePtr. Se l'opzione ValuePtr è un puntatore null, non viene restituito lunghezza. Se il valore dell'attributo è una stringa di caratteri e il numero di byte disponibili da restituire è maggiore di BufferLength meno la lunghezza della terminazione null di caratteri, i dati in \*ValuePtr viene troncato a BufferLength meno la lunghezza del carattere di terminazione null ed è con terminazione null dal driver.|

Per consentire il recupero dell'intero elenco, ogni operazione Get restituisce il nome del provider corrente e incrementa un contatore interno a quello successivo. Quando questo contatore raggiunge la fine dell'elenco, una stringa vuota ("") viene restituito, e il contatore viene reimpostato; le operazioni Get successive quindi procedere nuovamente dall'inizio dell'elenco.

### <a name="communicating-with-keystore-providers"></a>La comunicazione con i provider di archivio chiavi

Il `SQL_COPT_SS_CEKEYSTOREDATA` attributo di connessione consente a un'applicazione client comunicare con i provider di archivio chiavi caricato per la configurazione di parametri aggiuntivi, trasparenza materiale e così via. La comunicazione tra un'applicazione client e un provider segue un protocollo di richiesta-risposta semplice, basato su Get e Set di richieste che utilizzano questo attributo di connessione. La comunicazione viene avviata solo dall'applicazione client.

> [!NOTE]
> A causa della natura di ODBC chiama rispondono del CEKeyStoreProvider a (SQLGet/SetConnectAttr) supporta solo il ODBC interfaccia impostazione dei dati con la risoluzione del contesto di connessione.

L'applicazione comunica con i provider di archivio chiavi tramite il driver tramite la struttura CEKeystoreData:

```
typedef struct CEKeystoreData {
wchar_t *name;
unsigned int dataSize;
char data[];
} CEKEYSTOREDATA;
```
| Argomento | Description |
|:---|:---|
|`name`|[Input] Al momento di Set, il nome del provider per cui i dati vengono inviati. Ignorato al momento Get. Stringa con terminazione null, i caratteri "wide".|
|`dataSize`|[Input] Le dimensioni della matrice di dati secondo la struttura.|
|`data`|[InOut] Al momento di Set, i dati da inviare al provider. Può trattarsi di dati arbitrari. il driver esegue alcun tentativo di interpretarlo. Su Get, il buffer per ricevere i dati letti dal provider.|

#### <a name="writing-data-to-a-provider"></a>Scrittura di un provider di dati

Oggetto `SQLSetConnectAttr` chiamare usando il `SQL_COPT_SS_CEKEYSTOREDATA` attributo scrive un "pacchetto" di dati per il provider dell'archivio chiavi specificato.
```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```
| Argomento | Description |
|:---|:---|
|`ConnectionHandle`| [Input] Handle di connessione. Deve essere un handle di connessione valida, ma caricati tramite l'handle di connessione di un provider sono accessibili da qualsiasi altro nello stesso processo.|
|`Attribute`|[Input] Attributo da impostare: il `SQL_COPT_SS_CEKEYSTOREDATA` costante.|
|`ValuePtr`|[Input] Puntatore a una struttura CEKeystoreData. Il campo nome della struttura identifica il provider a cui è destinato il tipo di dati.|
|`StringLength`|[Input] Costante SQL_IS_POINTER|

Ulteriori informazioni dettagliate sull'errore possono essere ottenute tramite [SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx).

> [!NOTE]
> Il provider può utilizzare l'handle di connessione per associare i dati scritti in una determinata connessione, se lo desidera. Ciò è utile per l'implementazione di configurazione per ogni connessione. Può anche ignorare il contesto di connessione e trattare i dati in modo identico, indipendentemente dalla connessione utilizzata per inviare i dati. Vedere [contesto di associazione](../../connect/odbc/custom-keystore-providers.md#context-association) per ulteriori informazioni.

#### <a name="reading-data-from-a-provider"></a>Lettura di dati da un provider

Una chiamata a `SQLGetConnectAttr` utilizzando il `SQL_COPT_SS_CEKEYSTOREDATA` attributo legge un "pacchetto" di dati da *l'ultima scritto-a-* provider. Se è presente nessuno, verrà generato un errore di sequenza della funzione. Gli implementatori del provider di archivio chiavi sono invitati a supportare "fittizio scrive" di 0 byte come modalità di selezione del provider per le operazioni di lettura senza causare effetti collaterali, se è consigliabile eseguire questa operazione.

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```
| Argomento | Description |
|:---|:---|
|`ConnectionHandle`|[Input] Handle di connessione. Deve essere un handle di connessione valida, ma caricati tramite l'handle di connessione di un provider sono accessibili da qualsiasi altro nello stesso processo.|
|`Attribute`|[Input] Attributo da recuperare: il `SQL_COPT_SS_CEKEYSTOREDATA` costante.|
|`ValuePtr`|[Output] Un puntatore a una struttura CEKeystoreData in cui sono stati inseriti i dati letti dal provider.|
|`BufferLength`|[Input] Costante SQL_IS_POINTER|
|`StringLengthPtr`|[Output] Un puntatore a un buffer in cui si desidera restituire BufferLength. Se * ValuePtr non è un puntatore null, viene restituita alcuna lunghezza.|

Il chiamante deve garantire che un buffer di lunghezza sufficiente seguendo la struttura CEKEYSTOREDATA viene allocato per il provider di scrivere in. Al momento della restituzione, il campo dataSize viene aggiornato con la lunghezza effettiva dei dati letti dal provider. Ulteriori informazioni dettagliate sull'errore possono essere ottenute tramite [SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx).

Questa interfaccia non inserito nessun requisito aggiuntivo sul formato dei dati trasferiti tra un'applicazione e un provider dell'archivio chiavi. Ogni provider è possibile definire il proprio formato di dati/protocollo, a seconda delle esigenze.

Per un esempio di implementazione di provider di archivio chiavi personalizzato, vedere [provider archivio chiavi personalizzati](../../connect/odbc/custom-keystore-providers.md)

## <a name="limitations-of-the-odbc-driver-when-using-always-encrypted"></a>Limitazioni del driver ODBC quando si Usa crittografia sempre attiva

### <a name="asynchronous-operations"></a>Operazioni asincrone
Mentre il driver ODBC consentirà l'utilizzo di [operazioni asincrone](../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md) con crittografia sempre attiva, è un impatto sulle prestazioni delle operazioni quando Always Encrypted è abilitato. La chiamata a `sys.sp_describe_parameter_encryption` per determinare i metadati di crittografia per l'istruzione blocca e causerà il driver di attesa per il server restituire i metadati prima della restituzione `SQL_STILL_EXECUTING`.

### <a name="retrieve-data-in-parts-with-sqlgetdata"></a>Recuperare i dati in parti con SQLGetData
Prima crittografato 17 Driver ODBC per SQL Server, caratteri e colonne binarie non possono essere recuperate in parti con SQLGetData. Solo una chiamata di SQLGetData può essere effettuata, con un buffer di lunghezza sufficiente per contenere dati dell'intera colonna.

### <a name="send-data-in-parts-with-sqlputdata"></a>Inviare i dati in parti con SQLPutData
Impossibile inviare i dati per l'inserimento o di confronto nelle parti con SQLPutData. Solo una chiamata a SQLPutData può essere effettuata, con un buffer che contiene tutti i dati. Per l'inserimento di dati long in colonne crittografate, utilizzare l'API della copia Bulk, descritto nella sezione successiva, con un file di dati di input.

### <a name="encrypted-money-and-smallmoney"></a>Smallmoney e money crittografati
Crittografati **money** o **smallmoney** colonne non possono essere assegnate dai parametri, poiché non è specifico del tipo di dati ODBC che esegue il mapping di questi tipi, gli errori di conflitto di tipo di operando.

## <a name="bulk-copy-of-encrypted-columns"></a>Copia bulk di colonne crittografate

Utilizzare il [funzioni di copia Bulk SQL](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md) e **bcp** utilità è supportata con crittografia sempre attiva perché 17 Driver ODBC per SQL Server. Testo normale (crittografato in inserimento e recupero decrittografato nel) sia testo crittografato (trasferiti verbatim) possono essere inseriti e recuperati utilizzando la copia di massa (bcp_ *) le API e **bcp** utilità.

- Per recuperare testo crittografato in formato varbinary (max) (ad esempio per il caricamento bulk in un database diverso), connettersi senza il `ColumnEncryption` opzione (o impostarlo su `Disabled`) ed eseguire un'operazione BCP OUT.

- Per inserire e recuperare in testo normale e consente di eseguire in modo trasparente la crittografia e decrittografia come impostazione obbligatoria, il driver `ColumnEncryption` a `Enabled` è sufficiente. In caso contrario, la funzionalità dell'API BCP è invariata.

- Per inserire testo crittografato in formato varbinary (max) (ad esempio come recuperato sopra), impostare il `BCPMODIFYENCRYPTED` opzione su TRUE e di eseguire un'operazione BCP IN. Affinché i dati risultanti da decryptable, verificare che la destinazione CEK della colonna è uguale a quello da cui il testo crittografato è stato ottenuto in origine.

Quando si utilizza il **bcp** utilità: controllo di `ColumnEncryption` impostazione, utilizzare l'opzione -D e specificare un DSN che contiene il valore desiderato. Per inserire testo crittografato, verificare che il `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` è abilitata l'impostazione dell'utente.

Nella tabella seguente fornisce un riepilogo delle azioni quando si opera su una colonna crittografata:

|`ColumnEncryption`|Direzione BCP|Description|
|----------------|-------------|-----------|
|`Disabled`|OUT (client)|Recupera testo crittografato. Il tipo di dati osservati **varbinary (max)**.|
|`Enabled`|OUT (client)|Recupera in testo normale. Il driver per decrittografare i dati della colonna.|
|`Disabled`|IN (per server)|Inserisce testo crittografato. Questo deve essere opaca lo spostamento dei dati crittografati senza siano decrittografati. L'operazione avrà esito negativo se il `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` per l'utente non è impostata l'opzione o BCPMODIFYENCRYPTED non impostato per l'handle di connessione. Per ulteriori informazioni, vedere di seguito.|
|`Enabled`|IN (per server)|Inserisce testo normale. Il driver crittograferà i dati della colonna.|

### <a name="the-bcpmodifyencrypted-option"></a>L'opzione BCPMODIFYENCRYPTED

Per evitare il danneggiamento dei dati, il server in genere non consente l'inserimento di testo crittografato direttamente in una colonna crittografata e quindi tenta di eseguire questa operazione avrà esito negativo; Tuttavia, per il caricamento bulk dei dati crittografati mediante l'API BCP, l'impostazione la `BCPMODIFYENCRYPTED` [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) opzione su TRUE consente testo crittografato da inserire direttamente e riduce il rischio di danneggiamento dei dati crittografati sull'impostazione di `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` opzione sull'account utente. Ciononostante, le chiavi devono corrispondere i dati ed è consigliabile eseguire alcuni controlli di sola lettura dei dati inseriti dopo l'inserimento bulk e prima dell'uso di altre.

Vedere [migrare dati sensibili protetti da crittografia sempre attiva](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md) per ulteriori informazioni.

## <a name="always-encrypted-api-summary"></a>Riepilogo delle API crittografia sempre attiva

### <a name="connection-string-keywords"></a>Parole chiave per le stringhe di connessione

|Nome|Description|  
|----------|-----------------|  
|`ColumnEncryption`|I valori accettati sono `Enabled` / `Disabled`.<br>`Enabled` -Abilita la funzionalità crittografia sempre attiva per la connessione.<br>`Disabled` -disabilitare la funzionalità crittografia sempre attiva per la connessione. <br><br>Il valore predefinito è `Disabled`.|  
|`KeyStoreAuthentication` | I valori validi: `KeyVaultPassword`, `KeyVaultClientSecret` |
|`KeyStorePrincipalId` | Quando `KeyStoreAuthentication`  =  `KeyVaultPassword`, impostare questo valore su un nome entità utente di Active Directory di Azure valido. <br>Quando `KeyStoreAuthetication`  =  `KeyVaultClientSecret` impostare questo valore su un valido ID Azure Active Directory dell'applicazione Client |
|`KeyStoreSecret` | Quando `KeyStoreAuthentication`  =  `KeyVaultPassword` impostare questo valore per la password per il nome utente corrispondente. <br>Quando `KeyStoreAuthentication`  =  `KeyVaultClientSecret` impostare questo valore per il segreto dell'applicazione associata a una Azure Active Directory dell'applicazione Client ID valido|

### <a name="connection-attributes"></a>Attributi di connessione

|Nome|Tipo|Description|  
|----------|-------|----------|  
|`SQL_COPT_SS_COLUMN_ENCRYPTION`|Pre-connessione|`SQL_COLUMN_ENCRYPTION_DISABLE` (0) - disable crittografia sempre attiva <br>`SQL_COLUMN_ENCRYPTION_ENABLE` (1) - abilitare crittografia sempre attiva|
|`SQL_COPT_SS_CEKEYSTOREPROVIDER`|Post-connessione|[Set] Tentativo di caricamento CEKeystoreProvider<br>[Get] Restituisce un nome di CEKeystoreProvider|
|`SQL_COPT_SS_CEKEYSTOREDATA`|Post-connessione|[Set] Scrivere dati CEKeystoreProvider<br>[Get] Leggere i dati da CEKeystoreProvider|
|`SQL_COPT_SS_CEKCACHETTL`|Post-connessione|[Impostato] Impostare la durata (TTL) della cache CEK<br>[Get] Ottenere la durata (TTL) di cache CEK corrente|
|`SQL_COPT_SS_TRUSTEDCMKPATHS`|Post-connessione|[Impostato] Impostare il puntatore di percorsi attendibile CMK<br>[Get] Ottenere il puntatore di percorsi attendibile CMK corrente|

### <a name="statement-attributes"></a>Attributi di istruzione

|Nome|Description|  
|----------|-----------------|  
|`SQL_SOPT_SS_COLUMN_ENCRYPTION`|`SQL_CE_DISABLED` (0) - always Encrypted è disabilitato per l'istruzione <br>`SQL_CE_RESULTSETONLY` (1) - solo la decrittografia. Set di risultati e i valori restituiti vengono decrittografati e parametri non vengono crittografati. <br>`SQL_CE_ENABLED` (3) - always Encrypted è abilitato e usato per entrambi i parametri e i risultati|

### <a name="descriptor-fields"></a>Campi di descrizione

|Campo IPD|Tipo di dimensione /|Valore predefinito|Description|
|-|-|-|-|  
|`SQL_CA_SS_FORCE_ENCRYPT` (1236)|WORD (2 byte)|0|Quando 0 (impostazione predefinita): decisione per crittografare il parametro è determinato dalla disponibilità dei metadati di crittografia.<br><br>Quando è diverso da zero: se i metadati di crittografia sono disponibili per questo parametro, viene crittografato. In caso contrario, la richiesta ha esito negativo con errore [CE300] la crittografia obbligatoria [Microsoft] [ODBC Driver 13 for SQL Server] è stata specificata per un parametro, ma i metadati di crittografia non è stato fornito dal server.|

### <a name="bcpcontrol-options"></a>Opzioni bcp_control

|Nome opzione|Valore predefinito|Description|
|-|-|-|
|`BCPMODIFYENCRYPTED` (21)|FALSE|Se è TRUE, consente i valori da inserire nella colonna crittografata varbinary (max). Se è FALSE, impedisce l'inserimento, a meno che i metadati corretti di tipo e la crittografia viene fornito.|

## <a name="see-also"></a>Vedere anche

- [Always Encrypted (motore di database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Blog sulla Crittografia sempre attiva](http://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)

