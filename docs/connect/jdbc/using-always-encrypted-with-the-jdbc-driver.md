---
title: Utilizzo di Always Encrypted con il Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: 64
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: fffb61c4c3dfa58edaf684f103046d1029895e7c
ms.openlocfilehash: cee7f5dbcf66a5357ae68192703d841ae1601a35
ms.contentlocale: it-it
ms.lasthandoff: 10/19/2017

---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Utilizzo di Always Encrypted con il JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Questo articolo fornisce informazioni su come sviluppare applicazioni Java con [Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7) e Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server.

Always Encrypted consente ai client di crittografare dati sensibili senza mai rivelare le chiavi di crittografia a SQL Server o Database SQL di Azure. Un Always Encrypted abilitato driver, ad esempio Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server, a tale scopo in modo trasparente la crittografia e decrittografia dei dati sensibili nell'applicazione client. Il driver determina automaticamente una query in cui parametri corrispondono alle colonne di database con dati sensibili (protette usando Always Encrypted) e crittografa i valori dei parametri prima di passare i valori in SQL Server o Database SQL di Azure. Analogamente, il driver esegue in modo trasparente la decrittografia dei dati, recuperati dalle colonne di database crittografate nei risultati delle query. Per ulteriori informazioni, visitare [Always Encrypted (motore di Database)](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7) e [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  


## <a name="prerequisites"></a>Prerequisiti

- Configurare Always Encrypted nel database. Ciò implica il provisioning di chiavi Always Encrypted e l'impostazione della crittografia per le colonne di database selezionate. Se non è presente un database in cui Always Encrypted è configurato, seguire le istruzioni fornite nel blog di [introduzione a Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_5).
- Verificare che Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server è installato nel computer di sviluppo. 
-   Scaricare e installare Java Cryptography Extension (JCE) Unlimited Strenght Jurisdiction Policy Files.  Assicurarsi di leggere il file Readme incluso nel file zip per istruzioni sull'installazione e dettagli sui possibili problemi di importazione/esportazione.  
  
    -   Se si utilizza sqljdbc41.jar, i file dei criteri possono essere scaricati da [scaricare i file dei criteri di Java Cryptography Extension (JCE) Unlimited forza giurisdizione 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)  
  
    -   Se si utilizza sqljdbc42.jar, i file dei criteri possono essere scaricati da [scaricare i file dei criteri di Java Cryptography Extension (JCE) Unlimited forza giurisdizione 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)   
    
## <a name="enabling-always-encrypted-for-application-queries"></a>Abilitazione di Always Encrypted per le query dell'applicazione  
È il modo più semplice per abilitare la crittografia dei parametri e la decrittografia dei risultati di query per le colonne crittografate, impostando il valore di **columnEncryptionSetting** parola chiave della stringa di connessione  **Abilitato**.

Di seguito è riportato un esempio di una stringa di connessione che abilita Always Encrypted nel driver JDBC:
  
```  
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;"; 
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);
     
```  
  
E, di seguito è un esempio equivalente che usa l'oggetto SQLServerDataSource.  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setServerName("localhost");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");  
SQLServerConnection con = (SQLServerConnection) ds.getConnection(); 
```    

Always Encrypted può anche essere abilitato per le singole query. Vedere il **controllo prestazioni impatto di Always Encrypted** sezione riportata di seguito. Si noti che l'abilitazione di Always Encrypted non è sufficiente per l'esito positivo della crittografia o della decrittografia. È necessario anche assicurarsi che:
- L'applicazione abbia le autorizzazioni di database *VIEW ANY COLUMN MASTER KEY DEFINITION* e *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* , necessarie per accedere ai metadati sulle chiavi Always Encrypted nel database. Per informazioni dettagliate, vedere la [sezione Autorizzazioni in Always Encrypted (motore di database)](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7).
- L'applicazione può accedere alla chiave master della colonna che protegge le chiavi di crittografia di colonna, crittografando le colonne di database sottoposte a query. Si noti che, per utilizzare il provider di archivio di chiavi di Java che è necessario fornire ulteriori credenziali nella stringa di connessione. Vedere **provider di archivio di chiavi di Java Using** sezione per ulteriori dettagli.

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Configurare la modalità di invio dei valori Java.SQL. Time al Server

Il **sendTimeAsDatetime** proprietà di connessione viene utilizzata per configurare come il valore Java.SQL. Time viene inviato al server. Quando sendTimeAsDatetime = false, l'ora di valore viene inviato come tipi in fase di SQL Server e quando sendTimeAsDatetime = true, all'invio di valore come tipo datetime. Si noti che, se una colonna time è crittografata, la proprietà sendTimeAsDatetime deve essere false come colonne crittografate non supportano la conversione da ora in datetime. Si noti inoltre che questa proprietà è per valore predefinito true, pertanto quando si utilizzano colonne ora crittografati, è necessario impostarlo su false. In caso contrario, il driver genererà come eccezione. La classe SQLServerConnection dispone di due metodi, a partire dalla versione 6.0 del driver per configurare il valore di questa proprietà a livello di codice:
 
* pubblica setSendTimeAsDatetime void (sendTimeAsDateTimeValue booleano)
* public boolean getSendTimeAsDatetime()

Per ulteriori informazioni su questa proprietà visitare [Java.SQL configurazione come i valori vengono inviati al Server](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx). 

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>La configurazione come valori stringa vengono inviati al Server

Il **sendStringParametersAsUnicode** proprietà di connessione viene utilizzata per configurare come valori stringa vengono inviati a SQL Server. Se impostato su "true", i parametri String viene inviato al server in formato Unicode. Se impostato su "false", parametri di stringa viene inviato in formato non Unicode, ad esempio ASCII/MBCS invece di Unicode. Il valore predefinito per questa proprietà è "true". Quando Always Encrypted è abilitato e una colonna char/varchar/varchar(max) è crittografata, il valore di **sendStringParametersAsUnicode** deve essere impostato su true (o essere lasciato come impostazione predefinita). Microsoft JDBC Driver per SQL Server verrà generata un'eccezione durante l'inserimento di dati a una colonna crittografata char/varchar/varchar(max) se questa proprietà è impostata su false. Per ulteriori informazioni su questa proprietà, visitare [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md). 
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Recupero e modifica di dati nelle colonne crittografate

Dopo aver abilitato Always Encrypted per le query dell'applicazione, è possibile utilizzare le API JDBC standard per recuperare o modificare i dati in colonne crittografate del database. Presupponendo che l'applicazione dispone di autorizzazioni per il database richiesto e può accedere la chiave master della colonna, il Driver JDBC di Microsoft per SQL Server consente di crittografare eventuali parametri di query che interessano le colonne crittografate e per decrittografare i dati recuperati dalle colonne crittografate restituzione di valori di testo normale di tipi di JDBC, corrispondente al Server SQL da tipi di dati impostati per le colonne nello schema del database.
Se Always Encrypted non è abilitato, le query con parametri destinati alle colonne crittografate avranno esito negativo. Le query possono comunque recuperare dati dalle colonne crittografate, a condizione che non presentino parametri destinati alle colonne crittografate. Tuttavia, il Driver JDBC di Microsoft per SQL Server non proverà a decrittografare tutti i valori recuperati dalle colonne crittografate e l'applicazione riceverà dati crittografati binari (come matrici di byte).

La tabella seguente riepiloga il comportamento delle query, a seconda che Always Encrypted sia abilitato o meno:

|Caratteristica della query | Always Encrypted è abilitato e l'applicazione può accedere alle chiavi e ai metadati delle chiavi|Always Encrypted è abilitato e l'applicazione non può accedere alle chiavi o ai metadati delle chiavi | Always Encrypted è disabilitato|
|:---|:---|:---|:---|
| Query con parametri destinati alle colonne crittografate. | I valori dei parametri vengono crittografati in modo trasparente. | Errore | Errore|
| Query che recuperano dati dalle colonne crittografate, senza parametri destinati alle colonne crittografate.| I risultati delle colonne vengono decrittografati in modo trasparente. L'applicazione riceve valori di testo normale dei tipi di dati JDBC corrispondenti per i tipi di SQL Server configurato per le colonne crittografate. | Errore | I risultati delle colonne crittografate non vengono decrittografate. L'applicazione riceve i valori crittografati come matrici di byte (byte[]).
      
 
### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Inserimento e recupero di esempi di dati crittografati 
Gli esempi seguenti illustrano il recupero e la modifica dei dati nelle colonne crittografate. Negli esempi si presuppone la presenza della tabella di destinazione con lo schema seguente. Si noti che le colonne SSN e BirthDate nascita sono crittografate.

```
CREATE TABLE [dbo].[Patients]([PatientId] [int] IDENTITY(1,1), 
 [SSN] [char](11) COLLATE Latin1_General_BIN2 
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL, 
 [BirthDate] [date] 
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```
 
### <a name="inserting-data-example"></a>Esempio di inserimento di dati

Questo esempio illustra come inserire una riga nella tabella Patients. Si noti quanto segue:
- Il codice di esempio non contiene alcun elemento specifico per la crittografia. Automaticamente, il Driver JDBC di Microsoft per SQL Server rileva e consente di crittografare i parametri destinati alle colonne crittografate. In questo modo la crittografia diventa trasparente per l'applicazione. 
- I valori inseriti nelle colonne di database, incluse le colonne crittografate, vengono passati come parametri utilizzando SQLServerPreparedStatement. Durante l'utilizzo di parametri è facoltativa quando si inviano i valori alle colonne non crittografate (anche se è consigliata perché consente di impedire attacchi SQL injection), è necessario per i valori destinati alle colonne crittografate. Se i valori inseriti nelle colonne crittografate vengono passati come valori letterali incorporati nell'istruzione della query, la query avrà esito negativo poiché il Driver JDBC di Microsoft per SQL Server non sarà in grado di determinare i valori delle colonne di destinazione crittografate, in modo che non verrebbe crittografare i valori. Di conseguenza, il server li rifiuterà come incompatibili con le colonne crittografate.
- Tutti i valori stampati dal programma saranno in testo non crittografato, come Microsoft JDBC Driver per SQL Server decrittografa in modo trasparente i dati recuperati dalle colonne crittografate.
- Se si sta eseguendo una ricerca usando dove clausola, il valore utilizzato nella clausola WHERE deve essere passato come parametro, in modo che il Driver JDBC di Microsoft per SQL Server è stato possibile in modo trasparente crittografarlo prima di inviarlo al database. Nell'esempio seguente, si noti che SSN viene passato come parametro, ma il cognome viene passato come un valore letterale come LastName non crittografata.
- Il metodo di impostazione utilizzato per il parametro destinato alla colonna SSN è setString(), che esegue il mapping al tipo di dati di SQL Server char/varchar. Se, per questo parametro, il metodo di impostazione utilizzato setNString(), che esegue il mapping a nchar/nvarchar, la query avrà esito negativo, come Always Encrypted non supporta le conversioni da valori nchar/nvarchar crittografati a valori char/varchar crittografati.  

```
String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
try  
{           
     Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
     try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
     {                  
        String insertRecord="INSERT INTO [dbo].[Patients] VALUES (?, ?, ?, ?)";        
        try (PreparedStatement insertStatement = sourceConnection.prepareStatement(insertRecord))  
        {
            insertStatement.setString(1, "795-73-9838");  
            insertStatement.setString(2, "Catherine");   
            insertStatement.setString(3, "Abel");                   
            insertStatement.setDate(4, Date.valueOf("1996-09-10"));  
            insertStatement.executeUpdate();  
            System.out.println("1 record inserted.\n");  
        }         
     }  
}  
catch (Exception e)  
{  
    e.printStackTrace();  
}
```

### <a name="retrieving-plaintext-data-example"></a>Esempio di recupero di dati di testo non crittografato

L'esempio seguente illustra come filtrare i dati in base ai valori crittografati e recuperare i dati in testo non crittografato dalle colonne crittografate. Si noti quanto segue:
- Il valore utilizzato nella clausola WHERE per filtrare la colonna SSN deve essere passata come parametro, in modo che il Driver JDBC di Microsoft per SQL Server possibile codificarli in modo trasparente prima dell'invio al database.
- Tutti i valori stampati dal programma saranno in testo non crittografato, come Microsoft JDBC Driver per SQL Server decrittografa in modo trasparente i dati recuperati dalle colonne SSN e BirthDate.

> [!NOTE]  
>  Le query possono eseguire confronti di uguaglianza nelle colonne se sono crittografate tramite crittografia deterministica. Per ulteriori informazioni, vedere il **crittografia selezionando deterministica o casuale** sezione la [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) argomento.  

```
String connectionString =  "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;" ;
String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN = ?;";  

try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))  
{  
    selectStatement.setString(1, "795-73-9838");  
    ResultSet rs = selectStatement.executeQuery();   
    while(rs.next()) 
    {  
    System.out.println("SSN: " +rs.getString("SSN") + 
    ", FirstName: " + rs.getString("FirstName") + 
    ", LastName:"+ rs.getString("LastName")+
     ", Date of Birth: " + rs.getString("BirthDate"));  
          }  
}
catch (Exception e)  
{  
    e.printStackTrace();  
}
```
  
### <a name="retrieving-encrypted-data-example"></a>Esempio di recupero di dati crittografati

Se Always Encrypted non è abilitato, una query può comunque recuperare dati dalle colonne crittografate, a condizione che non presenti parametri destinati alle colonne crittografate.

Gli esempi seguenti illustrano come recuperare i dati crittografati binari dalle colonne crittografate. Si noti quanto segue:

- Considerato che Always Encrypted non è abilitato nella stringa di connessione, la query restituirà i valori crittografati di SSN e BirthDate come matrici di byte (il programma converte i valori in stringhe).
- Una query che recupera dati dalle colonne crittografate con Always Encrypted disabilitato può avere parametri, a condizione che nessuno dei parametri sia destinato a una colonna crittografata. La query precedente filtra in base alla colonna LastName, non è crittografata nel database. Se la query avesse filtrato per SSN o data di nascita, avrebbe avuto esito negativo.

```
String connectionString  = "jdbc:sqlserver://localhost:1433;" + "databaseName=Clinic;user=sa;password=******";

String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;"; 
 
try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))  
{  
    selectStatement.setString(1, "Abel");  
    ResultSet rs = selectStatement.executeQuery();   
    while(rs.next())
    {  
        System.out.println("SSN: " + rs.getString("SSN") +
         ", FirstName: " + rs.getString("FirstName") + 
        ", LastName:"+ rs.getString("LastName")+ 
        ", Date of Birth: " + rs.getString("BirthDate"));  
    } 
}  
catch (Exception e)  
{  
    e.printStackTrace();  
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Come evitare i problemi comuni quando si eseguono query su colonne crittografate

Questa sezione vengono descritte le categorie di errori durante l'esecuzione di query su colonne crittografate da applicazioni Java e alcune indicazioni su come evitare il problema.

### <a name="unsupported-data-type-conversion-errors"></a>Errori di conversione di tipo di dati non supportato

Always Encrypted supporta alcune conversioni per i tipi di dati crittografati. Vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) per un elenco dettagliato delle conversioni di tipo supportato. Per evitare errori di conversione di tipo di dati, verificare quanto segue:

- Utilizzare i metodi di impostazione appropriato quando si passa i valori per i parametri destinati alle colonne crittografate, in modo che il tipo di dati di SQL Server del parametro è esattamente come il tipo di colonna di destinazione o una conversione del tipo di dati di SQL Server del parametro alla destinazione del tipo della colonna è supportato. Si noti che siano stati aggiunti nuovi metodi API per le classi SQLServerPreparedStatement e SQLServerCallableStatement SQLServerResultSet per passare i parametri corrispondenti a specifici tipi di dati di SQL Server. Ad esempio, se una colonna non crittografata setTimestamp() metodo consente di passare un parametro a un datetime2 o a una colonna datetime. Tuttavia, quando una colonna è crittografata è necessario utilizzare il metodo esatto che rappresenta il tipo della colonna nel database. Ad esempio, utilizzare setTimestamp() per passare i valori a una colonna crittografata datetime2 e utilizzare setDateTime() per passare valori a una colonna datetime crittografati. Vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) per un elenco completo delle nuove API. 
- La precisione e la scala dei parametri destinati alle colonne dei tipi di dati di SQL Server decimali e numerici sono uguali a quelle configurate per la colonna di destinazione. Si noti che siano stati aggiunti nuovi metodi API per le classi SQLServerPreparedStatement e SQLServerCallableStatement SQLServerResultSet per accettare precisione e scala insieme ai valori di dati per i parametri o colonne che rappresentano i tipi di dati decimali e numerici. Vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) per un elenco completo di API/nuovo di overload.  
- la precisione/scala di frazioni di parametri destinati alle colonne dei tipi di dati di SQL Server ora, datetime2 o datetimeoffset non è maggiore di quello per la colonna di destinazione, nelle query che modificano i valori della colonna di destinazione. Si noti che siano stati aggiunti nuovi metodi API per le classi SQLServerPreparedStatement e SQLServerCallableStatement SQLServerResultSet per accettare i secondi frazionari scala/precisione insieme ai valori di dati per i parametri che rappresentano i tipi di dati. Vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) per un elenco completo di API/nuovo di overload.   

### <a name="errors-due-to-incorrect-connection-properties"></a>Errori a causa di proprietà di connessione non corrette
In questa sezione viene descritto come configurare le impostazioni di connessione in modo corretto per l'utilizzo di dati Always Encrypted. Poiché i tipi di dati crittografati supportano conversioni limitate, le impostazioni di connessione 'sendTimeAsDatetime' e 'sendStringParametersAsUnicode' richiedano una configurazione appropriata quando si utilizzano colonne crittografate. Assicurarsi che: 
- [sendTimeAsDatetime](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx) quando si inseriscono dati in tempo colonne con crittografia, l'impostazione di connessione è impostata su false. Per ulteriori informazioni, vedere la sezione 'Configurare la modalità di invio dei valori Java.SQL. Time al Server'.
- [sendStringParametersAsUnicode](../../connect/jdbc/setting-the-connection-properties.md) connessione è impostata su true (o viene lasciato come impostazione predefinita) quando si inseriscono dati in colonne char/varchar/varchar(max) con crittografia. Per ulteriori informazioni, vedere la sezione 'Configurazione come valori stringa vengono inviati al Server'.

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Errori a causa il passaggio di testo normale anziché i valori crittografati

Qualsiasi valore destinato a una colonna crittografata deve essere crittografato all'interno dell'applicazione. Il tentativo di inserire, modificare o filtrare in base a un valore di testo non crittografato su una colonna crittografata comporterà un errore simile al seguente:


```
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Per evitare tali errori, verificare che:
- Always Encrypted è abilitato per le query dell'applicazione destinati alle colonne crittografate (per la stringa di connessione o per una query specifica).
- usare le istruzioni preparate e parametri da inviare dati destinati alle colonne crittografate. L'esempio seguente viene illustrata una query che filtra in modo errato una valore letterale/una costante in una colonna crittografata (SSN), invece di passare all'interno del valore letterale come parametro. Questa query avrà esito negativo.

```
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");  
```

## <a name="working-with-column-master-key-stores"></a>Uso degli archivi delle chiavi master delle colonne
Per crittografare un valore di parametro o decrittografare i dati nei risultati della query, il Driver JDBC di Microsoft per SQL Server deve ottenere una colonna chiave di crittografia che è configurata per la colonna di destinazione. Chiavi di crittografia di colonna vengono archiviate in forma crittografata nei metadati del database. Ogni chiave di crittografia di colonna ha una chiave master corrispondente che è stata usata per crittografare la chiave di crittografia. I metadati del database non archiviano le chiavi master delle colonne, ma contengono solo le informazioni su un archivio delle chiavi contenente una specifica chiave master di colonna e il percorso della chiave nell'archivio.

Per ottenere un valore di testo normale di una chiave di crittografia di colonna, il Driver JDBC di Microsoft per SQL Server ottiene innanzitutto i metadati relativi sia la chiave di crittografia di colonna e la chiave master della colonna corrispondente e quindi utilizza le informazioni nei metadati per contattare la chiave archivio, che contiene la chiave master della colonna e decrittografare la chiave di crittografia di colonna crittografata. Microsoft JDBC Driver per SQL Server comunica con un archivio delle chiavi usando un provider di archivio chiavi master di colonna: è un'istanza di una classe derivato da **SQLServerColumnEncryptionKeyStoreProvider** classe.


### <a name="using-built-in-column-master-key-store-providers"></a>Uso di provider di archivi di chiavi master della colonna predefiniti
  
Microsoft JDBC Driver per SQL Server viene fornito con i seguenti provider di archivio chiave master di colonna predefinito. Si noti che alcuni di questi provider sono pre-registrati con i nomi di provider specifico (utilizzati per cercare il provider) e alcune richiedono ulteriori credenziali o alla registrazione esplicita.

| Classe | Descrizione | Nome del provider (ricerca) |Pre-registrato?|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Un provider di archivi di chiavi per l'insieme di credenziali chiave di Azure.| AZURE_KEY_VAULT|No|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Un provider per l'archivio certificati di Windows.|MSSQL_CERTIFICATE_STORE|Sì
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Un provider per il file keystore Java|MSSQL_JAVA_KEYSTORE|Sì|

Per il provider dell'archivio di chiavi già registrati non è necessario apportare alcuna modifica al codice dell'applicazione per utilizzare questi provider, ma tenere presente quanto segue:

- È necessario che l'utente (o l'amministratore del database) verifichi che il nome del provider, configurato nei metadati della chiave master della colonna, sia corretto e che il percorso della chiave master sia conforme al formato del percorso della chiave valido per un determinato provider. È consigliabile configurare le chiavi usando strumenti come SQL Server Management Studio, che genera automaticamente i nomi di provider e i percorsi delle chiavi validi quando si esegue l'istruzione CREATE COLUMN MASTER KEY (Transact-SQL).
- È necessario verificare che l'applicazione possa accedere alla chiave nell'archivio chiavi. Questa operazione potrebbe comportare l'accesso da parte dell'applicazione alla chiave e/o all'archivio delle chiavi, a seconda dell'archivio, o l'esecuzione di altri passaggi di configurazione specifici dell'archivio delle chiavi. Ad esempio, per l'utilizzo di SQLServerColumnEncryptionJavaKeyStoreProvider è necessario specificare il percorso e la password di keystore nelle proprietà di connessione. 

Tutti questi provider dell'archivio chiavi sono descritti in dettaglio più avanti.
  
### <a name="using-azure-key-vault-provider"></a>Uso del provider dell'insieme di credenziali delle chiavi di Azure
L'insieme di credenziali delle chiavi di Azure rappresenta una scelta valida per archiviare e gestire le chiavi master delle colonne per Always Encrypted, soprattutto se le applicazioni sono ospitate in Azure. Microsoft JDBC Driver per SQL Server include un provider predefinito, SQLServerColumnEncryptionAzureKeyVaultProvider, le applicazioni che dispongono di chiavi archiviate nell'insieme di credenziali chiave di Azure. Il nome di questo provider è AZURE_KEY_VAULT. Per utilizzare il provider dell'archivio di credenziali chiave di Azure, uno sviluppatore di applicazioni deve creare l'insieme di credenziali e le chiavi in Azure e configurare l'applicazione per accedere alle chiavi. Per ulteriori informazioni su come configurare l'insieme di credenziali chiave e creare una chiave master della colonna, fare riferimento a [insieme credenziali chiavi Azure – Step-by-Step per ulteriori informazioni su come configurare l'insieme di credenziali chiave](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) e [la creazione di chiavi Master della colonna nell'insieme di credenziali chiave di Azure](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2).  
  
Per utilizzare l'insieme di credenziali chiave di Azure, le applicazioni client devono creare un'istanza di SQLServerColumnEncryptionAzureKeyVaultProvider e registrarlo con il driver.

Di seguito è riportato un esempio di inizializzazione SQLServerColumnEncryptionAzureKeyVaultProvider:  
  
```  
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey); 
```

Dopo l'applicazione crea un'istanza di SQLServerColumnEncryptionAzureKeyVaultProvider, l'applicazione deve registrare l'istanza all'interno di Microsoft JDBC Driver per SQL Server utilizzando la Metodo registercolumnencryptionkeystoreproviders (). È consigliabile, l'istanza registrata utilizzando il nome di ricerca predefinito, AZURE_KEY_VAULT, che può essere ottenuto chiamando l'API SQLServerColumnEncryptionAzureKeyVaultProvider.getName(). Il nome predefinito, consente di utilizzare strumenti come SQL Server Management Studio o PowerShell, eseguire il provisioning e gestione delle chiavi di crittografia sempre attiva (strumenti di utilizzano il nome predefinito per generare l'oggetto di metadati per una chiave master della colonna). L'esempio seguente mostra la registrazione del provider di credenziali chiave di Azure. Per ulteriori informazioni sul metodo registercolumnencryptionkeystoreproviders (), vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md). 

```
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();   
keyStoreMap.put(akvProvider.getName(), akvProvider);   
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);   
```
  
> [!IMPORTANT]  
>  L'implementazione insieme credenziali chiavi Azure del driver JDBC ha dipendenze da queste librerie (GitHub):  
>   
>  [Azure sdk per java](https://github.com/Azure/azure-sdk-for-java)  
>   
>  [librerie di Azure-activedirectory-libreria-per-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)  
  
### <a name="using-windows-certificate-store-provider"></a>Utilizzando il Provider di archivio certificati di Windows
Il SQLServerColumnEncryptionCertificateStoreProvider utilizzabile per archiviare chiavi master della colonna nell'archivio certificati Windows. Utilizzare la procedura guidata crittografia sempre attiva SQL Server Management Studio (SSMS) o altri strumenti supportati per creare la chiave master della colonna e la crittografia di colonna le definizioni chiave nel database. La stessa procedura guidata consente di generare un certificato autofirmato nell'archivio certificati di Windows che è utilizzato come chiave master della colonna per i dati sempre crittografati. Per ulteriori informazioni sulla chiave master della colonna e di crittografia della colonna chiave sintassi T-SQL, visitare [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) e [CREATE COLUMN ENCRPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) rispettivamente.

Il nome del SQLServerColumnEncryptionCertificateStoreProvider è "MSSQL_CERTIFICATE_STORE" e può eseguire query per l'API getName() dell'oggetto provider. Viene registrato automaticamente dal driver e possono essere utilizzato facilmente senza la modifica di qualsiasi applicazione.

> [!IMPORTANT]  
>  L'implementazione di SQLServerColumnEncryptionCertificateStoreProvider del driver JDBC è disponibile con solo nei sistemi operativi Windows e presenta una dipendenza sqljdbc_auth.dll disponibile nel pacchetto driver.  Per utilizzare questo provider, copiare il file sqljdbc_auth.dll in una directory nel percorso di sistema di Windows nel computer in cui è installato il driver JDBC. In alternativa è possibile impostare la proprietà di sistema java.libary.path in modo da specificare la directory di sqljdbc_auth.dll. Se si esegue Java Virtual Machine (JVM) a 32 bit, utilizzare il file sqljdbc_auth.dll nella cartella x86, anche se la versione del sistema operativo è x64. Se si esegue JVM a 64 bit in un processore x64, utilizzare il file sqljdbc_auth.dll nella cartella x64. Ad esempio, se si utilizza la JVM a 32 bit e il driver JDBC è installato nella directory predefinita, è possibile specificare il percorso della DLL con il seguente argomento della macchina virtuale (VM) quando viene avviata l'applicazione Java:  
`-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`
        
### <a name="using-java-key-store-provider"></a>Utilizzando il Provider di archivio di chiavi di Java  
Il driver JDBC viene fornito con una chiave incorporata archiviare l'implementazione del provider per l'archivio di chiavi di Java. Il driver automaticamente crea e registra il provider per archivio chiavi Java, se il **keyStoreAuthentication** proprietà della stringa di connessione è presente nella stringa di connessione e viene impostato su "JavaKeyStorePassword" (vedere ulteriori dettagli di seguito). Il nome del provider dell'archivio chiavi Java è MSSQL_JAVA_KEYSTORE. Questo nome è anche possibile eseguire query dall'API di SQLServerColumnEncryptionJavaKeyStoreProvider.getName(). 

Vengono illustrate i tre parole chiave della stringa connessione nuovo per consentire un'applicazione client specificare in modo dichiarativo le credenziali che il driver deve eseguire l'autenticazione per l'archivio di chiavi di Java. Il driver necessario inizializzare il provider, in base ai valori delle seguenti tre proprietà della stringa di connessione, per le connessioni specifiche. 
  
 **keyStoreAuthentication:** identifica l'archivio di chiavi da utilizzare. Con Microsoft JDBC Driver 6.0 per SQL Server, è possibile autenticare per l'archivio di chiavi di Java solo tramite questa proprietà. Per l'archivio di chiavi di Java, il valore di questa proprietà deve essere "JavaKeyStorePassword".   
  
 **keyStoreLocation:** il percorso al file keystore Java che archivia la chiave master della colonna. Si noti che il percorso include il nome del file keystore.  
  
 **keyStoreSecret:** il segreto e la password da utilizzare per il file keystore anche per la chiave. Si noti che per l'utilizzo dell'archivio di chiavi di Java keystore e la password della chiave deve essere lo stesso.  

Di seguito è riportato un esempio per fornire queste credenziali nella stringa di connessione:

    String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
    
Queste impostazioni possono essere set/get tramite l'oggetto SQLServerDataSource. Vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) per ulteriori informazioni.     
  
Il driver JDBC crea automaticamente il SQLServerColumnEncryptionJavaKeyStoreProvider quando queste credenziali sono presenti nelle proprietà di connessione. 
  
### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Creazione di una chiave Master della colonna per l'archivio di chiavi di Java
Il SQLServerColumnEncryptionJavaKeyStoreProvider può essere utilizzato con tipi di archivio chiavi JKS o PKCS12. Per creare o importare una chiave da usare con questo provider di utilizzare il linguaggio [keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) utilità. Si noti che la chiave deve essere la stessa password dell'archivio chiavi stesso. Di seguito è riportato un esempio di come creare una chiave pubblica e la chiave privata associata utilizzando l'utilità keytool.

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks    

Questo comando crea una chiave pubblica e ne esegue il wrapping in un certificato che viene quindi archiviato nell'archivio 'keystore.jks' con la chiave privata associata autofirmato di certificati x. 509. Questa voce nell'archivio viene identificata l'alias 'AlwaysEncryptedKey'. 

Di seguito è riportato un esempio della stessa mediante un storetype PKCS12. 

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword   

Si noti che se l'archivio è di tipo PKCS12 quindi l'utilità keytool non viene visualizzata una richiesta per la password della chiave e la password della chiave devono essere specificato con l'opzione - keypass come il SQLServerColumnEncryptionJavaKeyStoreProvider deve disporre dell'archivio chiavi e la chiave di stessa password.

È inoltre possibile esportare un certificato dall'archivio certificati di Windows nel formato PFX e che utilizzano il SQLServerColumnEncryptionJavaKeyStoreProvider. Il certificato esportato può anche essere importato per l'archivio di chiavi di Java come un tipo di archivio chiavi JKS. 

Dopo aver creato la voce keytool sarà necessario creare i metadati di chiave master della colonna nel database di cui necessita il nome del provider di archivio chiavi e il percorso della chiave. Per ulteriori informazioni su come creare i metadati di chiave master della colonna visitare [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md). Per SQLServerColumnEncryptionJavaKeyStoreProvider, il percorso della chiave è semplicemente l'alias della chiave. E il nome del SQLServerColumnEncryptionJavaKeyStoreProvider è 'MSSQL_JAVA_KEYSTORE'. È inoltre possibile cercare il nome mediante l'API pubblica getName() della classe SQLServerColumnEncryptionJavaKeyStoreProvider. 

La sintassi T-SQL per la creazione della chiave master di colonna è:

```  
CREATE COLUMN MASTER KEY [<CMK_name>]  
WITH  
(  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',  
    KEY_PATH = N'<key_alias>'  
)  
```  

Definizione della chiave master della colonna di 'AlwaysEncryptedKey' creato in precedenza, potrebbe essere:

```  
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```  
    
> [!NOTE]  
>  Incorporato in SQL Server management funzionalità Studio non è possibile creare colonna le definizioni della chiave master per l'archivio di chiavi di Java per il quale è necessario utilizzare il comando T-SQL.  
  
### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Creazione di una chiave di crittografia di colonna per l'archivio di chiavi di Java
Si noti che il SQL Server management Studio o qualsiasi altro strumento non consente di creare chiavi di crittografia tramite chiavi master della colonna nell'archivio chiavi Java di colonna. L'applicazione client deve creare la chiave di crittografia a livello di codice utilizzando la classe SQLServerColumnEncryptionJavaKeyStoreProvider. Per ulteriori informazioni, visitare la sezione 'Tramite chiave Master del provider dell'archivio colonna per il Provisioning di chiave a livello di codice'. 

  
### <a name="implementing-a-custom-column-master-key-store-provider"></a>Implementazione di un provider personalizzato di archivio delle chiavi master delle colonne
Se si desidera archiviare chiavi master della colonna in un archivio chiavi che non è supportato da un provider esistente, è possibile implementare un provider personalizzato estendendo la classe SQLServerColumnEncryptionKeyStoreProvider e registrando il provider con il Metodo registercolumnencryptionkeystoreproviders ().
  
```  
public class MyCustomKeyStore extends SQLServerColumnEncryptionKeyStoreProvider{  
    private String name = "MY_CUSTOM_KEYSTORE";
    
    public void setName(String name)
    {
        this.name = name;
    }
    
    public String getName()
    {
        return name;
    }

    public byte[] encryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)  
    {  
        // Logic for encrypting the column encryption key  
    }  
    
    public byte[] decryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)  
    {  
        // Logic for decrypting the column encryption key  
    }  
}  
  
```  
  
 Registrazione del provider:  
  
```  
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();  
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();  
keyStoreMap.put(storeProvider.getName(), storeProvider);  
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);  
  
```  
  
## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>Uso di provider di archivi chiavi master della colonna per il provisioning di chiavi a livello di codice

Quando si accede a colonne crittografate, il Driver JDBC di Microsoft per SQL Server consente di individuare in modo trasparente e chiama il provider di archivio di chiave master della colonna a destra per decrittografare le chiavi di crittografia di colonna. In genere, il codice dell'applicazione normale non chiama direttamente i provider di archivio delle chiavi master delle colonne. È tuttavia possibile creare un'istanza e chiamare un provider in modo esplicito a livello di codice e gestire le chiavi Always Encrypted per generare la chiave di crittografia di una colonna crittografata e decrittografare la chiave di crittografia di una colonna (ad esempio nell'ambito della rotazione della chiave master della colonna). Per altre informazioni, vedere [Panoramica della gestione delle chiavi per Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).
Si noti che l'implementazione dei propri strumenti di gestione delle chiavi potrebbe essere necessaria solo se si usa un provider di archivio delle chiavi personalizzato. Quando si utilizzano chiavi archiviate nell'archivio certificati Windows o in insieme di credenziali chiave di Azure, è possibile utilizzare gli strumenti esistenti, ad esempio SQL Server Management Studio o PowerShell per gestire ed eseguire il provisioning di chiavi. Quando si utilizzano chiavi archiviate nell'archivio chiavi Java, è necessario eseguire il provisioning di chiavi a livello di codice. L'esempio seguente viene illustrato l'utilizzo di classe SQLServerColumnEncryptionJavaKeyStoreProvider per crittografare la chiave con una chiave archiviata nell'archivio di chiavi di Java.

```  
import java.sql.*;
import javax.xml.bind.DatatypeConverter;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programatically for the Java Key Store.
 */
public class AlwaysEncrypted
{
    // Alias of the key stored in the keystore.
    private static String keyAlias = "<proide key alias>";

    // Name by which the column master key will be known in the database.
    private static String columnMasterKeyName = "MyCMK";

    // Name by which the column encryption key will be known in the database.
    private static String columnEncryptionKey = "MyCEK";

    // The location of the keystore. 
    private static String keyStoreLocation = "C:\\Dev\\Always Encrypted\\keystore.jks";

    // The password of the keystore and the key.
    private static char[] keyStoreSecret = "********".toCharArray();

    /**
     * Name of the encryption algorithm used to encrypt the value of
     * the column encryption key. The algorithm for the system providers must be RSA_OAEP.
     */
    private static String algorithm = "RSA_OAEP";

    public static void main(String[] args)
    {
        String connectionString = GetConnectionString();
        try
        {
            // Note: if you are not using try-with-resources statements (as here),
            // you must remember to call close() on any Connection, Statement,
            // ResultSet objects that you create.

            // Open a connection to the database.
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))
            {
                // Instantiate the Java Key Store provider.
                SQLServerColumnEncryptionKeyStoreProvider storeProvider = 
                        new SQLServerColumnEncryptionJavaKeyStoreProvider(
                                keyStoreLocation,
                                keyStoreSecret);

                byte [] encryptedCEK=getEncryptedCEK(storeProvider);

                /**
                 * Create column encryption key 
                 * For more details on the syntax refer: 
                 * https://msdn.microsoft.com/library/mt146372.aspx
                 * Encrypted column encryption key first needs to be converted into varbinary_literal from bytes, 
                 * for which DatatypeConverter.printHexBinary is used
                 */
                String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY " 
                        + columnEncryptionKey
                        + " WITH VALUES ( "
                        + " COLUMN_MASTER_KEY = " 
                        + columnMasterKeyName
                        + " , ALGORITHM =  '" 
                        + algorithm
                        + "' , ENCRYPTED_VALUE =  0x" 
                        + DatatypeConverter.printHexBinary(encryptedCEK)
                        + " ) ";

                try (Statement cekStatement = sourceConnection.createStatement())
                {
                    cekStatement.executeUpdate(createCEKSQL);
                    System.out.println("Column encryption key created with name : " + columnEncryptionKey);
                }
            }
        }
        catch (Exception e)
        {
            // Handle any errors that may have occurred.
            e.printStackTrace();
        }
    }

    // To avoid storing the sourceConnection String in your code,
    // you can retrieve it from a configuration file.
    private static String GetConnectionString()
    {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +
                "databaseName=ae2;user=sa;password=********;";

        return connectionUrl;
    }

    private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException
    {
        /**
         * Following arguments needed by  SQLServerColumnEncryptionJavaKeyStoreProvider
         * 1) keyStoreLocation : 
         *      Path where keystore is located, including the keystore file name. 
         * 2) keyStoreSecret : 
         *      Password of the keystore and the key.  
         */
        String plainTextKey = "You need to give your plain text";

        // plainTextKey has to be 32 bytes with current algorithm supported
        byte[] plainCEK = plainTextKey.getBytes();

        // This will give us encrypted column encryption key in bytes
        byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(
                keyAlias,
                algorithm,
                plainCEK);

        return encryptedCEK;
    }
}

```  
  
## <a name="force-encryption-on-input-parameters"></a>Forzare la crittografia in parametri di Input
  
La funzionalità di crittografia applica la crittografia di un parametro quando si usa Always Encrypted. Forza crittografia è utilizzata e SQL Server indica al driver che il parametro non deve essere crittografato, la query utilizzando il parametro avrà esito negativo. Questa proprietà fornisce protezione aggiuntiva contro attacchi alla sicurezza in cui un SQL Server compromesso fornisce al client metadati di crittografia non corretti, con conseguente rischio di divulgazione dei dati. I metodi set * in classi SQLServerPreparedStatement e SQLServerCallableStatement e l'aggiornamento\* metodi della classe SQLServerResultSet sono sottoposti a overload per accettare un argomento booleano per specificare l'impostazione di crittografia force. Se il valore di questo argomento è false, il driver non forza la crittografia sui parametri. Se Forza crittografia è impostata su true, la query parametro verrà inviato solo se la colonna di destinazione è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione. In questo modo un ulteriore livello di sicurezza, assicurando che viene inviato alcun dato abbia erroneamente messo a SQL Server come testo non crittografato quando si prevede siano crittografati.  
  
 Per ulteriori informazioni sui metodi SQLServerPreparedStatement e SQLServerCallableStatement che sono sottoposti a overload con l'impostazione di crittografia force, vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-performance-impact-of-always-encrypted"></a>Controllo dell'impatto di Always Encrypted sulle prestazioni

Considerato che Always Encrypted è una tecnologia di crittografia lato client, la maggior parte del sovraccarico delle prestazioni si verifica sul lato client, non nel database. A parte il costo delle operazioni di crittografia e decrittografia, le altre origini di sovraccarico delle prestazioni sul lato client sono le seguenti:
- Round trip aggiuntivi al database per recuperare i metadati per i parametri di query.
- Chiamate a un archivio delle chiavi master delle colonne per accedere alla chiave master di una colonna.

Questa sezione descrive le ottimizzazioni delle prestazioni predefinite in Microsoft JDBC Driver per SQL Server e come sia possibile controllare l'impatto dei fattori sopra due sulle prestazioni.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Controllo dei round trip per recuperare i metadati per i parametri di query

Se Always Encrypted è abilitato per una connessione, per impostazione predefinita, il Driver JDBC di Microsoft per SQL Server chiamerà [sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx?f=255&MSPPError=-2147217396) per ogni query con parametri, passando l'istruzione di query (senza alcuna i valori dei parametri) a SQL Server. [Sys. sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx?f=255&MSPPError=-2147217396) analizza l'istruzione di query per scoprire se i parametri devono essere crittografati e in tal caso, per ognuno di tali, restituisce le informazioni relative alla crittografia che consentono a Microsoft JDBC Driver per SQL Server per crittografare i valori dei parametri. Il comportamento descritto garantisce all'applicazione client un elevato livello di trasparenza. L'applicazione (e lo sviluppatore dell'applicazione) non è necessario essere a conoscenza di quali query accedono alle colonne crittografate, purché i valori destinati alle colonne crittografate vengono passati a Microsoft JDBC Driver per SQL Server come parametri.


#### <a name="setting-always-encrypted-at-the-query-level"></a>Impostazione di Always Encrypted a livello di query

Per controllare l'impatto sulle prestazioni del recupero dei metadati di crittografia per le query con parametri, è possibile abilitare Always Encrypted per singole query, anziché l'impostarla per la connessione. In questo modo, è possibile garantire che sys.sp_describe_parameter_encryption venga richiamato solo per le query con parametri destinati alle colonne crittografate. Si noti, tuttavia, che in tal modo si riduce la trasparenza della crittografia: se si modificano le proprietà di crittografia delle colonne di database, potrebbe essere necessario modificare il codice dell'applicazione per allinearlo alle modifiche dello schema.


Per controllare il comportamento di Always Encrypted delle singole query, è necessario configurare gli oggetti di singola istruzione passando un Enum, SQLServerStatementColumnEncryptionSetting, che specifica come verranno inviati e ricevuti durante la lettura e scrittura di dati colonne crittografate per l'istruzione specifica. Di seguito sono riportate alcune linee guida utili:
- Se la maggior parte delle query che un'applicazione client invia alla connessione del database accede alle colonne crittografate:
    - Impostare la parola chiave stringa di connessione columnEncryptionSetting su abilitato.
    - Impostare SQLServerStatementColumnEncryptionSetting.Disabled per le singole query che non accedono a tutte le colonne crittografate. In questo modo verranno disabilitati sia la chiamata di sys.sp_describe_parameter_encryption chiamante che il tentativo di decrittografare tutti i valori nel set di risultati.
    - Impostare SQLServerStatementColumnEncryptionSetting.ResultSet per le singole query che non dispone di parametri che richiedono la crittografia, ma che recuperano dati dalle colonne crittografate. In questo modo verranno disabilitati la chiamata di sys.sp_describe_parameter_encryption e la crittografia dei parametri. La query potrà decrittografare i risultati delle colonne di crittografia.
- Se la maggior parte delle query che un'applicazione client invia alla connessione del database non accede alle colonne crittografate:
    - Parola chiave della stringa di connessione columnEncryptionSetting disabilitato.
    - Impostare SQLServerStatementColumnEncryptionSetting.Enabled per le singole query con parametri che devono essere crittografati. In questo modo verranno abilitate sia la chiamata di sys.sp_describe_parameter_encryption che la decrittografia dei risultati di query recuperati da colonne crittografate.
    - Impostare SQLServerStatementColumnEncryptionSetting.ResultSet per le query che non dispone di parametri che richiedono la crittografia, ma che recuperano dati dalle colonne crittografate. In questo modo verranno disabilitati la chiamata di sys.sp_describe_parameter_encryption e la crittografia dei parametri. La query potrà decrittografare i risultati delle colonne di crittografia.

Si noti come le impostazioni di SQLServerStatementColumnEncryptionSetting non possono essere utilizzate per ignorare la crittografia e ottenere l'accesso ai dati di testo normale. Per ulteriori informazioni su come configurare la crittografia di colonna in un'istruzione, vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

Nell'esempio seguente Always Encrypted è disabilitato per la connessione al database. La query eseguita dall'applicazione ha un parametro la cui destinazione è la colonna LastName non crittografata. La query recupera i dati dalle colonne SSN e BirthDate, che sono entrambe crittografate. In tal caso, la chiamata di sys.sp_describe_parameter_encryption per recuperare i metadati di crittografia non è necessaria. Tuttavia, è necessario abilitare la decrittografia dei risultati della query in modo che l'applicazione possa ricevere i valori di testo non crittografato dalle due colonne crittografate. SQLServerStatementColumnEncryptionSetting.ResultSet impostazione viene utilizzata per garantire che.

```
// Assumes the same table definition as in Section "Retrieving and modifying data in encrypted columns"
// where only SSN and BirthDate columns are encrypted in the database.
String connectionUrl = "jdbc:sqlserver://localhost;databaseName=ae;user=sa;password=******;"
        + "keyStoreAuthentication=JavaKeyStorePassword;"
        + "keyStoreLocation=" + keyStoreLocation + ";"
        + "keyStoreSecret=******;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);

String filterRecord="SELECT FirstName, LastName, SSN, BirthDate FROM " + tblName + " WHERE LastName = ?";  
PreparedStatement selectStatement = connection.prepareStatement(
        filterRecord, 
        ResultSet.TYPE_FORWARD_ONLY, 
        ResultSet.CONCUR_READ_ONLY, 
        connection.getHoldability(), 
        SQLServerStatementColumnEncryptionSetting.ResultSetOnly);
selectStatement.setString(1, "Abel");  
ResultSet rs = selectStatement.executeQuery();  
while(rs.next()) {  
    System.out.println("First name: " + rs.getString("FirstName"));  
    System.out.println("Last name: " + rs.getString("LastName"));  
    System.out.println("SSN: " + rs.getString("SSN"));  
    System.out.println("Date of Birth: " + rs.getDate("BirthDate"));  
}  
rs.close();
selectStatement.close();
connection.close();
```


### <a name="column-encryption-key-caching"></a>Memorizzazione nella cache delle chiavi di crittografia della colonna

Per ridurre il numero di chiamate a un archivio chiavi master della colonna per decrittografare le chiavi di crittografia di colonna, il Driver JDBC di Microsoft per SQL Server memorizza nella cache le chiavi di crittografia di colonna in testo normale in memoria. Dopo aver ricevuto il valore delle chiavi di crittografia della colonna crittografata dai metadati del database, il driver prova prima di tutto a trovare la chiave di crittografia della colonna di testo non crittografato corrispondente al valore della chiave crittografata. Il driver chiama l'archivio delle chiavi contenente la chiave master della colonna solo se non trova nella cache il valore della chiave di crittografia della colonna crittografata.

È possibile configurare un valore time-to-live per le voci di chiave di crittografia di colonna nella cache con l'API, setColumnEncryptionKeyCacheTtl(), nella classe SQLServerConnection. Il valore predefinito di time-to-live per le voci chiave di crittografia di colonna nella cache è 2 ore. Per disattivare la memorizzazione nella cache utilizzare un valore pari a 0. Per impostare qualsiasi valore time-to-live di utilizzare l'API seguente:
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
   
Ad esempio, per impostare un valore time-to-live di 10 minuti, utilizzare
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)

Si noti che, come l'unità di tempo sono supportati solo i giorni, ore, minuti o secondi.  


## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Copia i dati crittografati con utilizzo di SQLServerBulkCopy

Con SQLServerBulkCopy, è possibile copiare dati, che sono già crittografati e archiviati in una tabella, in un'altra tabella, senza la decrittografia dei dati. Per eseguire questa operazione:

- Assicurarsi che la configurazione di crittografia della tabella di destinazione sia identica alla configurazione della tabella di origine. In particolare, entrambe le tabelle devono avere le stesse colonne crittografate e le colonne devono essere crittografate usando gli stessi tipi di crittografia e le stesse chiavi di crittografia. Nota: se una o più colonne di destinazione sono crittografate in modo diverso dalla relativa colonna di origine corrispondente, non sarà possibile decrittografare i dati nella tabella di destinazione dopo l'operazione di copia. I dati risulteranno danneggiati.
- Configurare entrambe le connessioni di database, per la tabella di origine e la tabella di destinazione, senza Always Encrypted abilitato. 
- Impostare l'opzione allowEncryptedValueModifications. Vedere [tramite copia Bulk con il Driver JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md) per ulteriori informazioni.
 
Nota: Prestare attenzione quando si specifica AllowEncryptedValueModifications come questo potrebbe causare il danneggiamento del database perché il Driver JDBC di Microsoft per SQL Server non verifica se i dati vengono effettivamente crittografati o se vengono crittografati correttamente usando la stessa crittografia tipo di algoritmo e chiave come colonna di destinazione.

## <a name="see-also"></a>Vedere anche  
 [Always Encrypted (Motore di database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
  
  

