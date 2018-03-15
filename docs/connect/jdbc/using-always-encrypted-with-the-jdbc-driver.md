---
title: Utilizzo di Always Encrypted con il driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 3/14/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: af8b651364f58c3c4261666d5d6531e99e620efe
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Utilizzo di Always Encrypted con il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Questa pagina fornisce informazioni su come sviluppare applicazioni Java con [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) e Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server.

Always Encrypted consente ai client di crittografare dati sensibili senza mai rivelare le chiavi di crittografia a SQL Server o Database SQL di Azure. Un Always Encrypted abilitato driver, ad esempio Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server, consente di ottenere questo comportamento in modo trasparente la crittografia e decrittografia dei dati sensibili nell'applicazione client. Il driver determina automaticamente una query in cui parametri corrispondono alle colonne del database Always Encrypted e crittografa i valori dei parametri prima di inviarli a SQL Server o Database SQL di Azure. Analogamente, il driver esegue in modo trasparente la decrittografia dei dati, recuperati dalle colonne di database crittografate nei risultati delle query. Per ulteriori informazioni, vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) e [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

## <a name="prerequisites"></a>Prerequisiti
- Verificare che Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server è installato nel computer di sviluppo. 
- Scaricare e installare Java Cryptography Extension (JCE) Unlimited Strenght Jurisdiction Policy Files.  Assicurarsi di leggere il file Readme incluso nel file zip per istruzioni sull'installazione e le informazioni sui problemi di importazione/esportazione possibili.  

    - Se si utilizza il mssql-jdbc-X.X.X.jre7.jar o sqljdbc41.jar, i file dei criteri possono essere scaricati da [scaricare i file dei criteri di Java Cryptography Extension (JCE) Unlimited forza giurisdizione 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)

    - Se si utilizza il mssql-jdbc-X.X.X.jre8.jar o sqljdbc42.jar, i file dei criteri possono essere scaricati da [scaricare i file dei criteri di Java Cryptography Extension (JCE) Unlimited forza giurisdizione 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)

    - Se si utilizza il X.X.X.jre9.jar di jdbc mssql, alcun file di criteri non dovrà essere scaricati. I criteri di competenza in Java 9 per impostazione predefinita a livello di un numero illimitato di crittografia.

## <a name="working-with-column-master-key-stores"></a>Utilizzo di archivi di chiavi master di colonna
Per crittografare o decrittografare i dati per le colonne crittografate, SQL Server gestisce le chiavi di crittografia di colonna. Chiavi di crittografia di colonna vengono archiviate in forma crittografata nei metadati del database. Ogni chiave di crittografia di colonna ha una chiave master della colonna corrispondente che viene utilizzata per crittografare la chiave di crittografia di colonna. I metadati del database non contiene chiavi master della colonna. Tali chiavi vengono mantenuti solo dal client. Tuttavia, i metadati del database contengono informazioni sul percorso di archiviazione delle chiavi master della colonna relativo al client. Ad esempio, i metadati del database potrebbero indicare che il file keystore che contiene una chiave master della colonna è l'archivio certificati di Windows e il certificato specifico utilizzato per crittografare e decrittografare si trova in un percorso specifico all'interno dell'archivio certificati di Windows. Se il client ha accesso a tale certificato nell'archivio certificati Windows, è possibile ottenere il certificato. Il certificato consente quindi di decrittografare la chiave di crittografia di colonna. Tale chiave di crittografia può essere quindi utilizzato per decrittografare o crittografare i dati per le colonne crittografate che utilizzano tale chiave di crittografia di colonna.

Microsoft JDBC Driver per SQL Server comunica con un keystore tramite un provider di archivio chiavi master di colonna, è un'istanza di una classe derivato da **SQLServerColumnEncryptionKeyStoreProvider**.

### <a name="using-built-in-column-master-key-store-providers"></a>Uso dei provider predefiniti di archivio delle chiavi master delle colonne
Microsoft JDBC Driver per SQL Server viene fornito con i seguenti provider di archivio chiave master di colonna predefinito. Alcuni di questi provider sono pre-registrati con i nomi di provider specifico (utilizzati per cercare il provider), mentre altri richiedono ulteriori credenziali o alla registrazione esplicita.

| Classe | Description | Nome del provider (ricerca) |Pre-registrato?|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Un provider per un archivio chiavi per l'insieme di credenziali chiave di Azure.| AZURE_KEY_VAULT|no|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Un provider per l'archivio certificati di Windows.|MSSQL_CERTIFICATE_STORE|Sì
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Un provider per il file keystore Java|MSSQL_JAVA_KEYSTORE|Sì|

Per i provider di archivio chiavi pre-registrato, non è necessario apportare alcuna modifica al codice dell'applicazione per utilizzare questi provider, ma tenere presente quanto segue:

- È necessario assicurarsi che il nome del provider configurato con i metadati della chiave master della colonna sia corretto e il percorso della chiave master della colonna sia conforme con il formato del percorso di chiave valido per un determinato provider è (o l'amministratore del database). Si consiglia di configurare le chiavi usando strumenti, ad esempio SQL Server Management Studio, che genera automaticamente i nomi di provider valido e i percorsi delle chiavi quando eseguire l'istruzione CREATE COLUMN MASTER KEY (Transact-SQL).
- Verificare che l'applicazione può accedere alla chiave nell'archivio. Questa attività può comportare concedendo l'accesso dell'applicazione per la chiave e/o dell'archivio chiavi, a seconda dell'archivio chiavi, o eseguire altri passaggi di configurazione specifica dell'archivio chiavi. Ad esempio, per l'utilizzo di SQLServerColumnEncryptionJavaKeyStoreProvider, è necessario specificare il percorso e la password di keystore nelle proprietà di connessione. 

Tutti questi provider di archivio chiavi sono descritti più dettagliatamente nelle sezioni che seguono. È necessario solo implementare un provider dell'archivio chiavi per l'utilizzo di Always Encrypted.

### <a name="using-azure-key-vault-provider"></a>Uso del provider dell'insieme di credenziali delle chiavi di Azure
Insieme di credenziali chiave di Azure è una soluzione comoda per archiviare e gestire chiavi master della colonna per Always Encrypted (in particolare se l'applicazione è ospitata in Azure). Microsoft JDBC Driver per SQL Server include un provider predefinito SQLServerColumnEncryptionAzureKeyVaultProvider, le applicazioni che dispongono di chiavi archiviate nell'insieme di credenziali chiave di Azure. Il nome di questo provider è AZURE_KEY_VAULT. Per utilizzare il provider dell'archivio di credenziali chiave di Azure, uno sviluppatore di applicazioni deve creare l'insieme di credenziali e le chiavi nell'insieme di credenziali chiave di Azure e creare una registrazione delle App in Azure Active Directory. L'applicazione registrata deve essere concesso ottenere, decrittografia, Encrypt, Unwrap chiave, eseguire il wrapping di chiave e verificare le autorizzazioni nei criteri di accesso definiti per l'insieme di credenziali chiave creata per l'utilizzo con crittografia sempre attiva. Per ulteriori informazioni su come configurare l'insieme di credenziali chiave e creare una chiave master della colonna, vedere [insieme credenziali chiavi Azure – Step by Step](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) e [la creazione di chiavi Master della colonna nell'insieme di credenziali chiave di Azure](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault).

Per gli esempi in questa pagina, se è stato creato un insieme di credenziali chiave di Azure basato su chiave master della colonna e la chiave di crittografia di colonna utilizzando SQL Server Management Studio, lo script T-SQL per ricrearle potrebbe essere simile a questo esempio con il proprio specifico **KEY_ PERCORSO** e **ENCRYPTED_VALUE**:

```
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',
    KEY_PATH = N'https://<MyKeyValutName>.vault.azure.net:443/keys/Always-Encrypted-Auto1/c61f01860f37302457fa512bb7e7f4e8'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x01BA000001680074507400700073003A002F002F006400610076006...
)
```

Per utilizzare l'insieme di credenziali chiave di Azure, le applicazioni client devono creare un'istanza di SQLServerColumnEncryptionAzureKeyVaultProvider e registrarlo con il driver.

Di seguito è riportato un esempio di inizializzazione SQLServerColumnEncryptionAzureKeyVaultProvider:  

```
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**clientID** è l'ID applicazione di una registrazione delle App in un'istanza di Azure Active Directory. **chiave client** è una Password chiave registrata in tale applicazione, che fornisce l'accesso all'API per l'insieme di credenziali chiave di Azure.

Dopo l'applicazione crea un'istanza di SQLServerColumnEncryptionAzureKeyVaultProvider, l'applicazione è necessario registrare l'istanza con il driver utilizzando il metodo registercolumnencryptionkeystoreproviders (). È consigliabile che l'istanza registrata utilizzando il nome di ricerca predefinito, AZURE_KEY_VAULT, che può essere ottenuto chiamando l'API SQLServerColumnEncryptionAzureKeyVaultProvider.getName(). Utilizzando il nome predefinito consente di utilizzare strumenti come SQL Server Management Studio o PowerShell per eseguire il provisioning e gestione delle chiavi di crittografia sempre attiva (strumenti di utilizzano il nome predefinito per generare l'oggetto di metadati per una chiave master della colonna). L'esempio seguente mostra la registrazione del provider di credenziali chiave di Azure. Per ulteriori informazioni sul metodo registercolumnencryptionkeystoreproviders (), vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

```
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Se si utilizza il provider dell'archivio chiavi insieme credenziali chiavi Azure, l'implementazione insieme credenziali chiavi Azure del driver JDBC ha dipendenze da queste librerie (da GitHub) che devono essere incluse con l'applicazione:
>
>  [azure-sdk-for-java](https://github.com/Azure/azure-sdk-for-java)
>
>  [azure-activedirectory-library-for-java libraries](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> Per un esempio di come includere queste dipendenze in un progetto di Maven, vedere [scaricare ADAL4J AKV le dipendenze e con Apache Maven](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven)

### <a name="using-windows-certificate-store-provider"></a>Utilizzando il provider di archivio certificati di Windows
Il SQLServerColumnEncryptionCertificateStoreProvider utilizzabile per archiviare chiavi master della colonna nell'archivio certificati Windows. Utilizzare la procedura guidata crittografia sempre attiva SQL Server Management Studio (SSMS) o altri strumenti supportati per creare la chiave master della colonna e la crittografia di colonna le definizioni chiave nel database. La stessa procedura guidata consente di generare un certificato autofirmato nell'archivio certificati di Windows che può essere utilizzato come chiave master della colonna per i dati sempre crittografati. Per ulteriori informazioni sulla chiave master della colonna e sintassi T-SQL della colonna crittografia chiave, vedere [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) e [CREATE COLUMN ENCRPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) rispettivamente.

Il nome del SQLServerColumnEncryptionCertificateStoreProvider è MSSQL_CERTIFICATE_STORE e può eseguire query per l'API getName() dell'oggetto provider. Viene registrato automaticamente dal driver e possono essere utilizzato facilmente senza la modifica di qualsiasi applicazione.

Per gli esempi in questa pagina, se è stato creato un archivio certificati Windows basati su chiave master della colonna e la chiave di crittografia di colonna utilizzando SQL Server Management Studio, lo script T-SQL per ricrearle potrebbe essere simile a questo esempio con il proprio specifico **KEY_PATH** e **ENCRYPTED_VALUE**:

```
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/My/A2A91F59C461B559E4D962DA9D2BC6131B32CB91'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E0074007500730065007200...
)
```

> [!IMPORTANT]
> L'implementazione di SQLServerColumnEncryptionCertificateStoreProvider del driver JDBC è disponibile con solo nei sistemi operativi Windows e presenta una dipendenza sqljdbc_auth.dll disponibile nel pacchetto driver. Per utilizzare questo provider, copiare il file sqljdbc_auth.dll in una directory nel percorso di sistema di Windows nel computer in cui è installato il driver JDBC. In alternativa è possibile impostare la proprietà di sistema java.libary.path in modo da specificare la directory di sqljdbc_auth.dll. Se si esegue Java Virtual Machine (JVM) a 32 bit, utilizzare il file sqljdbc_auth.dll nella cartella x86, anche se la versione del sistema operativo è x64. Se si esegue JVM a 64 bit in un processore x64, utilizzare il file sqljdbc_auth.dll nella cartella x64. Ad esempio, se si utilizza la JVM a 32 bit e il driver JDBC è installato nella directory predefinita, è possibile specificare il percorso della DLL con il seguente argomento della macchina virtuale (VM) quando viene avviata l'applicazione Java: `-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>Utilizzando il provider di archivio di chiavi di Java
Il driver JDBC viene fornito con un'implementazione del provider di archivio chiavi predefinite per l'archivio di chiavi di Java. Se il **keyStoreAuthentication** proprietà della stringa di connessione è presente nella stringa di connessione e viene impostato su "JavaKeyStorePassword", il driver registra il provider per archivio chiavi di Java e crea automaticamente. Il nome del provider di archivio di chiavi di Java è MSSQL_JAVA_KEYSTORE. Questo nome è anche possibile eseguire query tramite l'API SQLServerColumnEncryptionJavaKeyStoreProvider.getName(). 

Esistono tre proprietà di stringa di connessione che consentono a un'applicazione client specificare le credenziali che il driver deve eseguire l'autenticazione per l'archivio di chiavi di Java. Il driver Inizializza il provider in base ai valori di queste tre proprietà nella stringa di connessione.

**keyStoreAuthentication:** identifica l'archivio di chiavi di linguaggio da utilizzare. Con Microsoft JDBC Driver 6.0 e versioni successive per SQL Server, è possibile autenticare per l'archivio di chiavi di Java solo tramite questa proprietà. Per l'archivio di chiavi di Java, il valore di questa proprietà deve essere `JavaKeyStorePassword`.

**keyStoreLocation:** il percorso del file di archivio di chiavi di Java che archivia la chiave master della colonna. Il percorso include il nome del file keystore.

**keyStoreSecret:** il segreto e la password da utilizzare per il file keystore anche per la chiave. Per l'utilizzo dell'archivio di chiavi di Java, keystore e la password della chiave deve essere lo stesso.

Di seguito è riportato un esempio di fornire queste credenziali nella stringa di connessione:

```
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

È anche possibile ottenere o configurare le impostazioni mediante l'oggetto SQLServerDataSource. Per ulteriori informazioni, vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

Il driver JDBC crea automaticamente il SQLServerColumnEncryptionJavaKeyStoreProvider quando queste credenziali sono presenti nelle proprietà di connessione.

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Creazione di una chiave master della colonna per l'archivio di chiavi di Java
Il SQLServerColumnEncryptionJavaKeyStoreProvider può essere utilizzato con tipi di archivio chiavi JKS o PKCS12. Per creare o importare una chiave da usare con questo provider di utilizzare il linguaggio [keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) utilità. La chiave deve essere la stessa password dell'archivio chiavi stesso. Di seguito è riportato un esempio di come creare una chiave pubblica e la chiave privata associata utilizzando l'utilità keytool:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

Questo comando crea una chiave pubblica e ne esegue il wrapping in un certificato, che viene archiviato nell'archivio 'keystore.jks' con la chiave privata associata autofirmato di certificati x. 509. Questa voce nell'archivio viene identificata l'alias 'AlwaysEncryptedKey'.

Di seguito è riportato un esempio di un tipo di archivio PKCS12 utilizzando stesso:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

Se il file keystore è di tipo PKCS12, l'utilità keytool non Richiedi una password della chiave e la password della chiave deve essere specificato con l'opzione - keypass come il SQLServerColumnEncryptionJavaKeyStoreProvider richiede che il file keystore e la chiave hanno lo stesso password.

È inoltre possibile esportare un certificato dall'archivio certificati di Windows nel formato PFX e che utilizzano il SQLServerColumnEncryptionJavaKeyStoreProvider. Il certificato esportato può anche essere importato per l'archivio di chiavi di Java come un tipo di archivio chiavi JKS.

Dopo aver creato la voce keytool, creare i metadati della chiave master della colonna nel database, che richiede il nome del provider di archivio chiavi e il percorso della chiave. Per ulteriori informazioni su come creare i metadati di chiave master della colonna, vedere [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md). Per SQLServerColumnEncryptionJavaKeyStoreProvider, il percorso della chiave è semplicemente l'alias della chiave e il nome del SQLServerColumnEncryptionJavaKeyStoreProvider è 'MSSQL_JAVA_KEYSTORE'. È inoltre possibile cercare il nome mediante l'API pubblica getName() della classe SQLServerColumnEncryptionJavaKeyStoreProvider. 

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
> La gestione di SQL Server predefinita funzionalità Studio non è possibile creare definizioni di chiave master della colonna per l'archivio di chiavi di Java. I comandi T-SQL devono essere utilizzati a livello di codice.

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Creazione di una chiave di crittografia di colonna per l'archivio di chiavi di Java
Impossibile utilizzare SQL Server Management Studio o qualsiasi altro strumento per creare chiavi di crittografia tramite chiavi master della colonna nell'archivio chiavi Java di colonna. L'applicazione client deve creare la chiave di crittografia a livello di codice utilizzando la classe SQLServerColumnEncryptionJavaKeyStoreProvider. Per ulteriori informazioni, vedere [tramite i provider di archivio chiavi master di colonna per il provisioning di chiavi a livello di codice](#using-column-master-key-store-providers-for-programmatic-key-provisioning).

### <a name="implementing-a-custom-column-master-key-store-provider"></a>Implementazione di un provider personalizzato di archivio delle chiavi master delle colonne
Se si desidera archiviare chiavi master della colonna in un archivio chiavi che non sono supportata da un provider esistente, è possibile implementare un provider personalizzato estendendo la classe SQLServerColumnEncryptionKeyStoreProvider e registrando il provider con il Metodo registercolumnencryptionkeystoreproviders ().

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

## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>Uso di provider di archivio delle chiavi master delle colonne per il provisioning di chiavi a livello di codice
Quando si accede a colonne crittografate, il Driver JDBC di Microsoft per SQL Server consente di individuare in modo trasparente e chiama il provider di archivio di chiave master della colonna a destra per decrittografare le chiavi di crittografia di colonna. In genere, il codice dell'applicazione normale non chiama direttamente i provider di archivio delle chiavi master delle colonne. È possibile, tuttavia, creare un'istanza e chiamare un provider a livello di codice per eseguire il provisioning e gestione delle chiavi di crittografia sempre attiva. Questo passaggio può essere eseguito per generare una chiave di crittografia di colonna crittografata e decrittografare una chiave di crittografia di colonna come parte rotazione della chiave master della colonna, ad esempio. Per altre informazioni, vedere [Panoramica della gestione delle chiavi per Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).

Se si utilizza un provider dell'archivio chiavi personalizzato, potrebbe essere necessario implementare i propri strumenti di gestione delle chiavi. Quando si utilizzano chiavi archiviate nell'archivio certificati Windows o in insieme di credenziali chiave di Azure, è possibile utilizzare gli strumenti esistenti, ad esempio SQL Server Management Studio o PowerShell per gestire ed eseguire il provisioning di chiavi. Quando si utilizzano chiavi archiviate nell'archivio chiavi Java, è necessario eseguire il provisioning di chiavi a livello di codice. Nell'esempio seguente viene illustrato l'utilizzo della classe SQLServerColumnEncryptionJavaKeyStoreProvider per crittografare la chiave con una chiave archiviata nell'archivio di chiavi di Java.

```
import java.sql.*;
import javax.xml.bind.DatatypeConverter;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programmatically for the Java Key Store.
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
                 * For more details on the syntax, see:
                 * https://docs.microsoft.com/sql/t-sql/statements/create-column-encryption-key-transact-sql
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
         * Following arguments needed by SQLServerColumnEncryptionJavaKeyStoreProvider
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

## <a name="enabling-always-encrypted-for-application-queries"></a>Abilitazione di Always Encrypted per le query dell'applicazione
Il modo più semplice per abilitare la crittografia dei parametri e la decrittografia dei risultati di query destinati alle colonne crittografate consiste nell'impostare il valore di **columnEncryptionSetting** parola chiave della stringa di connessione **abilitato** .

Stringa di connessione seguente è riportato un esempio di abilitazione di Always Encrypted nel driver JDBC:

```
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);
```

Il codice seguente è un esempio equivalente che usa l'oggetto SQLServerDataSource:

```
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("localhost");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");
SQLServerConnection con = (SQLServerConnection) ds.getConnection();
```

Always Encrypted può anche essere abilitato per le singole query. Per ulteriori informazioni, vedere [controllare l'impatto sulle prestazioni di Always Encrypted](#controlling-the-performance-impact-of-always-encrypted). Abilitazione di Always Encrypted non è sufficiente per la crittografia o decrittografia abbia esito positivo. È necessario anche assicurarsi che:
- L'applicazione abbia le autorizzazioni di database *VIEW ANY COLUMN MASTER KEY DEFINITION* e *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* , necessarie per accedere ai metadati sulle chiavi Always Encrypted nel database. Per informazioni dettagliate, vedere [autorizzazioni in Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
- L'applicazione può accedere la chiave master della colonna che protegge le chiavi di crittografia di colonna, che crittografa le colonne del database sottoposto a query. Per utilizzare il provider di archivio di chiavi di Java, è necessario fornire ulteriori credenziali nella stringa di connessione. Per ulteriori informazioni, vedere [provider di archivio di chiavi di Java Using](#using-java-key-store-provider).

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Configurare la modalità di invio dei valori Java.SQL. Time al server
Il **sendTimeAsDatetime** proprietà di connessione viene utilizzata per configurare come il valore Java.SQL. Time viene inviato al server. Se impostato su false, il valore di ora viene inviato come un tipo time di SQL Server. Se impostata su true, all'invio di valore come tipo datetime. Se una colonna time è crittografata, il **sendTimeAsDatetime** proprietà deve essere impostato su false, come le colonne crittografate non supportano la conversione da ora in datetime. Si noti inoltre che questa proprietà è per valore predefinito true, pertanto quando si utilizzano colonne crittografati che è necessario impostarlo su false. In caso contrario, il driver genererà un'eccezione. A partire dalla versione 6.0 del driver, la classe SQLServerConnection offre due metodi per configurare il valore di questa proprietà a livello di codice:
 
* pubblica setSendTimeAsDatetime void (sendTimeAsDateTimeValue booleano)
* public boolean getSendTimeAsDatetime()

Per ulteriori informazioni su questa proprietà, vedere [Java.SQL configurazione come i valori vengono inviati al Server](configuring-how-java-sql-time-values-are-sent-to-the-server.md).

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>La configurazione come valori stringa vengono inviati al server
Il **sendStringParametersAsUnicode** proprietà di connessione viene utilizzata per configurare come valori stringa vengono inviati a SQL Server. Se impostato su true, i parametri String viene inviato al server in formato Unicode. Se impostato su false, i parametri di stringa viene inviato in formato non Unicode, ad esempio MBCS, invece di Unicode o ASCII. Il valore predefinito per questa proprietà è true. Quando Always Encrypted è abilitato e una colonna char/varchar/varchar(max) è crittografata, il valore di **sendStringParametersAsUnicode** deve essere impostato su true (o essere lasciato come impostazione predefinita). Se questa proprietà è impostata su false, il driver genererà un'eccezione durante l'inserimento di dati a una colonna crittografata char/varchar/varchar(max). Per ulteriori informazioni su questa proprietà, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Recupero e modifica di dati nelle colonne crittografate
Dopo aver abilitato Always Encrypted per le query dell'applicazione, è possibile utilizzare le API JDBC standard per recuperare o modificare i dati in colonne crittografate del database. Se l'applicazione ha le autorizzazioni di database necessari e può accedere alla chiave master di colonna, il driver consente di crittografare i parametri di query che fanno riferimento alle colonne crittografate e per decrittografare i dati recuperati dalle colonne crittografate.

Se Always Encrypted non è abilitato, le query con parametri destinati alle colonne crittografate avranno esito negativo. Le query possono comunque recuperare dati dalle colonne crittografate, purché la query non ha parametri destinati alle colonne crittografate. Tuttavia, il driver non tenterà di decrittografare tutti i valori recuperati dalle colonne crittografate e l'applicazione riceverà dati crittografati binari (come matrici di byte).

Nella tabella seguente viene riepilogato il comportamento delle query a seconda se Always Encrypted è abilitato o meno:

|Caratteristica della query | Always Encrypted è abilitato e l'applicazione può accedere alle chiavi e ai metadati delle chiavi|Always Encrypted è abilitato e l'applicazione non può accedere alle chiavi o ai metadati delle chiavi | Always Encrypted è disabilitato|
|:---|:---|:---|:---|
| Query con parametri destinati alle colonne crittografate. | I valori dei parametri vengono crittografati in modo trasparente. | Errore | Errore|
| Query che recuperano dati dalle colonne crittografate senza parametri destinati alle colonne crittografate.| I risultati delle colonne vengono decrittografati in modo trasparente. L'applicazione riceve valori di testo normale dei tipi di dati JDBC corrispondenti per i tipi di SQL Server configurato per le colonne crittografate. | Errore | I risultati delle colonne crittografate non vengono decrittografate. L'applicazione riceve i valori crittografati come matrici di byte (byte[]).

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Inserimento e recupero di esempi di dati crittografati 
Gli esempi seguenti illustrano il recupero e la modifica dei dati nelle colonne crittografate. Gli esempi presuppongono la tabella di destinazione nello schema seguente e le colonne SSN e BirthDate crittografate. Se è stata configurata una chiave Master della colonna denominata "MyCMK" e una chiave di crittografia di colonna denominata "MyCEK" (come descritto nelle sezioni precedenti keystore provider), è possibile creare la tabella con questo script:

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

Per ogni esempio di codice Java, è necessario inserire il codice specifico keystore nel percorso indicato.

Se si utilizza un provider dell'archivio chiavi insieme credenziali chiavi Azure:

```
    String clientID = "<Azure Application ID>";
    String clientKey = "<Azure Application API Key Password>";
    SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
    Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
    keyStoreMap.put(akvProvider.getName(), akvProvider);
    SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
```

Se si utilizza un provider dell'archivio chiavi archivio certificati di Windows:

```
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
```

Se si utilizza un provider dell'archivio chiavi archivio chiavi Java:

```
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>Esempio di inserimento dei dati
Questo esempio illustra come inserire una riga nella tabella Patients. Tenere presente quanto segue:
- Il codice di esempio non contiene alcun elemento specifico per la crittografia. Automaticamente, il Driver JDBC di Microsoft per SQL Server rileva e consente di crittografare i parametri destinati alle colonne crittografate. Questo comportamento esegue la crittografia trasparente all'applicazione.
- I valori inseriti nelle colonne di database, incluse le colonne crittografate, vengono passati come parametri utilizzando SQLServerPreparedStatement. Durante l'utilizzo di parametri è facoltativa quando si inviano i valori alle colonne non crittografate (anche se è consigliata perché consente di impedire attacchi SQL injection), è necessario per i valori destinati alle colonne crittografate. Se i valori inseriti nelle colonne crittografate vengono passati come valori letterali incorporati nell'istruzione della query, la query avrà esito negativo poiché il driver non sarebbe in grado di determinare i valori delle colonne di destinazione crittografate e non crittograferà i valori. Di conseguenza, il server li rifiuterà come incompatibili con le colonne crittografate.
- Tutti i valori stampati dal programma saranno in testo non crittografato, come Microsoft JDBC Driver per SQL Server decrittografa in modo trasparente i dati recuperati dalle colonne crittografate.
- Se si sta eseguendo una ricerca utilizzando una clausola WHERE, il valore utilizzato nella clausola WHERE deve essere passata come parametro in modo che il driver possibile codificarli in modo trasparente prima dell'invio al database. Nell'esempio seguente, il codice fiscale viene passato come parametro, ma il cognome viene passato come un valore letterale come LastName non crittografata.
- Il metodo di impostazione utilizzato per il parametro destinato alla colonna SSN è setString(), che esegue il mapping al tipo di dati di SQL Server char/varchar. Se, per questo parametro, il metodo di impostazione utilizzato setNString(), che esegue il mapping a nchar/nvarchar, la query avrà esito negativo, come Always Encrypted non supporta le conversioni da valori nchar/nvarchar crittografati a valori char/varchar crittografati.

```
try
{
    <Insert keystore-specific code here>

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

### <a name="retrieving-plaintext-data-example"></a>Esempio di dati di testo normale di recupero
Nell'esempio seguente viene illustrato il filtraggio dei dati in base a valori crittografati e il recupero dei dati di testo normale dalle colonne crittografate. Tenere presente quanto segue:
- Il valore utilizzato nella clausola WHERE per filtrare la colonna SSN deve essere passata come parametro in modo che il Driver JDBC di Microsoft per SQL Server possibile codificarli in modo trasparente prima dell'invio al database.
- Tutti i valori stampati dal programma saranno in testo non crittografato, come Microsoft JDBC Driver per SQL Server decrittografa in modo trasparente i dati recuperati dalle colonne SSN e BirthDate.

> [!NOTE]
> Se le colonne sono crittografate tramite crittografia deterministica, le query possono eseguire confronti di uguaglianza su di essi. Per ulteriori informazioni, vedere [selezionando deterministica o casuale di crittografia in Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```
try
{
    <Insert keystore-specific code here>

    Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
    try (Connection sourceConnection = DriverManager.getConnection(connectionString))
    {
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
    }
}
catch (Exception e)  
{  
    e.printStackTrace();  
}
```
  
### <a name="retrieving-encrypted-data-example"></a>Esempio di dati crittografati di recupero
Se Always Encrypted non è abilitato, una query può comunque recuperare dati dalle colonne crittografate, a condizione che non presenti parametri destinati alle colonne crittografate.

Nell'esempio seguente viene illustrato il recupero dei dati crittografati binari dalle colonne crittografate. Tenere presente quanto segue:
- Poiché non è abilitato Always Encrypted nella stringa di connessione, la query restituirà i valori crittografati di SSN e BirthDate come matrici di byte (il programma converte i valori in stringhe).
- Una query che recupera dati dalle colonne crittografate con Always Encrypted disabilitato può avere parametri, a condizione che nessuno dei parametri sia destinato a una colonna crittografata. Il seguente query per i filtri LastName, non è crittografata nel database. Se la query avesse filtrato per SSN o data di nascita, avrebbe avuto esito negativo.

```
try
{
    String connectionString  = "jdbc:sqlserver://localhost:1433;" + "databaseName=Clinic;user=sa;password=******";

    Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
    try (Connection sourceConnection = DriverManager.getConnection(connectionString))
    {
        String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;";

        try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))
        {
            selectStatement.setString(1, "Abel");
            ResultSet rs = selectStatement.executeQuery();
            while (rs.next())
            {
                System.out.println("SSN: " + rs.getString("SSN") +
                    ", FirstName: " + rs.getString("FirstName") +
                    ", LastName:"+ rs.getString("LastName") +
                    ", Date of Birth: " + rs.getString("BirthDate"));
            }
        }
    }
}
catch (Exception e)
{
    e.printStackTrace();
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Come evitare i problemi comuni quando si eseguono query su colonne crittografate
Questa sezione vengono descritte le categorie di errori durante l'esecuzione di query su colonne crittografate da applicazioni Java e alcune indicazioni su come evitare il problema.

### <a name="unsupported-data-type-conversion-errors"></a>Errori di conversione dei tipi di dati non supportati
Always Encrypted supporta alcune conversioni per i tipi di dati crittografati. Vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) per un elenco dettagliato delle conversioni di tipo supportato. Ecco cosa è possibile eseguire per evitare errori di conversione di tipo di dati. Assicurarsi che:

- Utilizzare i metodi di impostazione appropriato quando il passaggio di valori per parametri destinati alle colonne crittografate. Verificare che il tipo di dati di SQL Server del parametro è identico al tipo della colonna di destinazione o una conversione del tipo di dati di SQL Server del parametro nel tipo di destinazione della colonna è supportata. Metodi dell'API sono state aggiunte per le classi SQLServerPreparedStatement e SQLServerCallableStatement SQLServerResultSet per passare i parametri corrispondenti a specifici tipi di dati di SQL Server. Ad esempio, se una colonna è crittografata non è possibile utilizzare il metodo setTimestamp() per passare un parametro a un datetime2 o a una colonna datetime. Tuttavia, quando una colonna è crittografata è necessario utilizzare il metodo esatto che rappresenta il tipo della colonna nel database. Ad esempio, utilizzare setTimestamp() per passare i valori a una colonna crittografata datetime2 e utilizzare setDateTime() per passare valori a una colonna datetime crittografati. Vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) per un elenco completo delle nuove API.
- La precisione e la scala dei parametri destinati alle colonne dei tipi di dati di SQL Server decimali e numerici sono uguali a quelle configurate per la colonna di destinazione. Metodi dell'API sono state aggiunte per le classi SQLServerPreparedStatement e SQLServerCallableStatement SQLServerResultSet per accettare precisione e scala insieme ai valori di dati per i parametri o colonne che rappresentano i tipi di dati decimali e numerici. Vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) per un elenco completo di API/nuovo di overload.  
- la precisione/scala di frazioni di parametri destinati alle colonne dei tipi di dati di SQL Server ora, datetime2 o datetimeoffset non è maggiore della precisione/scala di frazioni di secondo per la colonna di destinazione nelle query che modificano i valori della colonna di destinazione . Metodi dell'API sono state aggiunte per le classi SQLServerPreparedStatement e SQLServerCallableStatement SQLServerResultSet per accettare i secondi frazionari scala/precisione insieme ai valori di dati per i parametri che rappresentano i tipi di dati. Per un elenco completo delle nuove/overload API, vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).   

### <a name="errors-due-to-incorrect-connection-properties"></a>Errori a causa di proprietà di connessione non corrette
In questa sezione viene descritto come configurare le impostazioni di connessione in modo corretto per l'utilizzo di dati Always Encrypted. Poiché i tipi di dati crittografati supportano conversioni limitate, di **sendTimeAsDatetime** e **sendStringParametersAsUnicode** le impostazioni di connessione necessaria la configurazione corretta quando si utilizzano colonne crittografate. Assicurarsi che: 
- [sendTimeAsDatetime](setting-the-connection-properties.md) quando si inseriscono dati in tempo colonne con crittografia, l'impostazione di connessione è impostata su false. Per ulteriori informazioni, vedere [come valori Java.SQL. Time verranno inviati al server di configurazione](configuring-how-java-sql-time-values-are-sent-to-the-server.md).
- [sendStringParametersAsUnicode](setting-the-connection-properties.md) connessione è impostata su true (o viene lasciato come impostazione predefinita) quando si inseriscono dati in colonne char/varchar/varchar(max) con crittografia.

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Errori causati dal passaggio di testo non crittografato anziché di valori crittografati
Qualsiasi valore destinato a una colonna crittografata deve essere crittografato all'interno dell'applicazione. Un tentativo di inserire, modificare o filtrare in base a un valore di testo normale su una colonna crittografata comporterà un errore simile al seguente:

```
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Per evitare tali errori, verificare che:
- Always Encrypted è abilitato per le query dell'applicazione destinati alle colonne crittografate (per la stringa di connessione o per una query specifica).
- usare le istruzioni preparate e parametri da inviare dati destinati alle colonne crittografate. Nell'esempio seguente viene illustrata una query che filtra in modo errato una valore letterale/una costante in una colonna crittografata (SSN), anziché passare il valore letterale all'interno di un parametro. Questa query avrà esito negativo:

```
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>Forzare la crittografia in parametri di input
La funzionalità di crittografia applica la crittografia di un parametro quando si usa Always Encrypted. Forza crittografia è utilizzata e SQL Server indica al driver che il parametro non deve essere crittografato, la query utilizzando il parametro avrà esito negativo. Questa proprietà fornisce protezione aggiuntiva contro attacchi alla sicurezza in cui un SQL Server compromesso fornisce al client metadati di crittografia non corretti, con conseguente rischio di divulgazione dei dati. I metodi set * in classi SQLServerPreparedStatement e SQLServerCallableStatement e l'aggiornamento\* metodi della classe SQLServerResultSet sono sottoposti a overload per accettare un argomento booleano per specificare l'impostazione di crittografia force. Se il valore di questo argomento è false, il driver non forza la crittografia sui parametri. Se Forza crittografia è impostata su true, la query parametro viene inviato solo se la colonna di destinazione è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione. Utilizzo di questa proprietà fornisce un ulteriore livello di sicurezza, assicurando che il driver non erroneamente inviare dati a SQL Server come testo non crittografato quando si prevede siano crittografati.

Per ulteriori informazioni sui metodi SQLServerPreparedStatement e SQLServerCallableStatement che sono sottoposti a overload con l'impostazione di crittografia force, vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Controllare l'impatto sulle prestazioni della crittografia sempre attiva
Poiché Always Encrypted è una tecnologia di crittografia lato client, si osserva la maggior parte dell'overhead delle prestazioni sul lato client, non nel database. A parte il costo delle operazioni di crittografia e decrittografia, altre origini di sovraccarico delle prestazioni sul lato client sono:
- Round trip aggiuntivi al database per recuperare i metadati per i parametri di query.
- Chiamate a un archivio delle chiavi master delle colonne per accedere alla chiave master di una colonna.

Questa sezione descrive le ottimizzazioni delle prestazioni predefinite in Microsoft JDBC Driver per SQL Server e come sia possibile controllare l'impatto dei fattori sopra due sulle prestazioni.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Controllo dei round trip per recuperare i metadati per i parametri di query
Se Always Encrypted è abilitato per una connessione, per impostazione predefinita il driver chiama [sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) per ogni query con parametri, passando l'istruzione di query (senza i valori dei parametri) a SQL Server. [Sys. sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) analizza l'istruzione di query per scoprire se i parametri devono essere crittografati e in tal caso, per ogni ne restituisce le informazioni relative alla crittografia che consentono al driver di crittografare i valori di parametro. Questo comportamento assicura un elevato livello di trasparenza per l'applicazione client. Fino a quando l'applicazione utilizza parametri per passare i valori destinati alle colonne crittografate al driver, l'applicazione (e lo sviluppatore dell'applicazione) non è necessario conoscere quali query accedono alle colonne crittografate.

### <a name="setting-always-encrypted-at-the-query-level"></a>Impostazione di Always Encrypted a livello di query
Per controllare l'impatto sulle prestazioni di recupero dei metadati di crittografia per le query con parametri, è possibile abilitare Always Encrypted per le singole query anziché l'impostarla per la connessione. In questo modo è possibile garantire che Sys. sp_describe_parameter_encryption venga richiamato solo per le query con parametri destinati alle colonne crittografate. Si noti, tuttavia, che in questo modo si riduce la trasparenza della crittografia: se si modifica la proprietà di crittografia delle colonne di database, potrebbe essere necessario modificare il codice dell'applicazione per allinearlo alle modifiche dello schema.

Per controllare il comportamento di Always Encrypted delle singole query, è necessario configurare gli oggetti di singola istruzione passando un Enum, SQLServerStatementColumnEncryptionSetting, che specifica come verranno inviati e ricevuti durante la lettura e scrittura di dati colonne crittografate per l'istruzione specifica. Di seguito sono riportate alcune linee guida utili:
- Se la maggior parte delle query di che un'applicazione client invia alla connessione del database accede alle colonne crittografate, è possibile utilizzare queste linee guida:
    - Impostare il **columnEncryptionSetting** parola chiave della stringa di connessione **abilitato**.
    - Impostare SQLServerStatementColumnEncryptionSetting.Disabled per le singole query che non accedono a tutte le colonne crittografate. Questa impostazione disattiva sp_describe_parameter_encryption chiamante nonché a un tentativo di decrittografare tutti i valori nel set di risultati.
    - Impostare SQLServerStatementColumnEncryptionSetting.ResultSet per le singole query che non dispone di parametri che richiedono la crittografia ma che recuperano dati dalle colonne crittografate. Questa impostazione verrà disabilitati sp_describe_parameter_encryption chiamante e crittografia dei parametri. La query potrà decrittografare i risultati delle colonne di crittografia.
- Se la maggior parte delle query di che un'applicazione client invia alla connessione del database non accede alle colonne crittografate, è possibile utilizzare queste linee guida:
    - Impostare il **columnEncryptionSetting** parola chiave della stringa di connessione **disabilitato**.
    - Impostare SQLServerStatementColumnEncryptionSetting.Enabled per le singole query con parametri che devono essere crittografati. Questa impostazione consentirà di Sys. sp_describe_parameter_encryption chiamante sia, nonché la decrittografia dei risultati di query recuperati dalle colonne crittografate.
    - Impostare SQLServerStatementColumnEncryptionSetting.ResultSet per le query che non dispone di parametri che richiedono la crittografia ma che recuperano dati dalle colonne crittografate. Questa impostazione verrà disabilitati sp_describe_parameter_encryption chiamante e crittografia dei parametri. La query potrà decrittografare i risultati delle colonne di crittografia.

Le impostazioni di SQLServerStatementColumnEncryptionSetting non possono essere utilizzate per ignorare la crittografia e ottenere l'accesso ai dati di testo normale. Per ulteriori informazioni su come configurare la crittografia di colonna in un'istruzione, vedere [sempre crittografato riferimento all'API per il Driver JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

Nell'esempio seguente Always Encrypted è disabilitato per la connessione al database. La query, i problemi dell'applicazione contiene un parametro che ha come destinazione la colonna LastName non crittografata. La query recupera i dati dalle colonne SSN e BirthDate, che sono entrambe crittografate. In tal caso, la chiamata di sys.sp_describe_parameter_encryption per recuperare i metadati di crittografia non è necessaria. Tuttavia, la decrittografia dei risultati della query deve essere abilitato in modo che l'applicazione può ricevere valori di testo normale da due colonne crittografate. L'impostazione SQLServerStatementColumnEncryptionSetting.ResultSet viene utilizzato per verificare che.

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
Per ridurre il numero di chiamate a un archivio chiavi master della colonna per decrittografare le chiavi di crittografia di colonna, il Driver JDBC di Microsoft per SQL Server memorizza nella cache le chiavi di crittografia di colonna in testo normale in memoria. Dopo aver ricevuto il valore di chiave di crittografia di colonna crittografata dai metadati del database, il driver tenta innanzitutto di trovare la chiave di crittografia di colonna in testo normale corrispondente al valore della chiave crittografato. Il driver chiama l'archivio chiavi contenente la chiave master della colonna solo se non si trova il valore di chiave di crittografia di colonna crittografata nella cache.

È possibile configurare un valore time-to-live per le voci di chiave di crittografia di colonna nella cache con l'API, setColumnEncryptionKeyCacheTtl(), nella classe SQLServerConnection. Il valore predefinito di time-to-live per le voci chiave di crittografia di colonna nella cache è due ore. Per disabilitare la memorizzazione nella cache, utilizzare un valore pari a 0. Per impostare qualsiasi valore time-to-live, utilizzare l'API seguente:

```
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

Ad esempio, per impostare un valore time-to-live di 10 minuti, utilizzare:

```
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

Come l'unità di tempo, sono supportati solo giorni, ore, minuti o secondi.  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Copia dei dati crittografati di utilizzo di SQLServerBulkCopy
Con SQLServerBulkCopy, è possibile copiare i dati che sono già crittografati e archiviati in una tabella a un'altra tabella senza la decrittografia dei dati. Per eseguire questa operazione:

- Assicurarsi che la configurazione di crittografia della tabella di destinazione sia identica alla configurazione della tabella di origine. In particolare, entrambe le tabelle devono avere le stesse colonne crittografate e le colonne devono essere crittografate utilizzando gli stessi tipi di crittografia e le stesse chiavi di crittografia. Se una colonna di destinazione è crittografata in modo diverso da una colonna di origine corrispondente, non sarà in grado di decrittografare i dati nella tabella di destinazione al termine dell'operazione di copia. I dati risulteranno danneggiati.
- Configurare entrambe le connessioni di database per la tabella di origine e la tabella di destinazione senza Always Encrypted abilitato.
- Impostare l'opzione allowEncryptedValueModifications. Per ulteriori informazioni, vedere [tramite copia Bulk con il Driver JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

> [!NOTE]
> Prestare attenzione quando si specifica AllowEncryptedValueModifications quanto questa opzione può causare il danneggiamento del database perché il Driver JDBC di Microsoft per SQL Server non verifica se i dati vengono effettivamente crittografati o se vengono crittografati correttamente usando la stessa crittografia tipo di algoritmo e chiave come colonna di destinazione.

## <a name="see-also"></a>Vedere anche
[Always Encrypted (Motore di database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
