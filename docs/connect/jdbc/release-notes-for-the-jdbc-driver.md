---
title: Note sulla versione per il Driver JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
caps.latest.revision: 206
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10f14eedb1a74f74cb1ee055a247a96671224ce0
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662463"
---
# <a name="release-notes-for-the-jdbc-driver"></a>Note sulla versione per il driver JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 7.0 per SQL Server

Microsoft JDBC Driver 7.0 per SQL Server è completamente conforme alla specifica di API di JDBC 4.2. I file JAR nel pacchetto 7.0 sono denominati in base alla compatibilità delle versioni di Java. Ad esempio, il file mssql-jdbc-7.0.0.jre10.jar dal pacchetto 7.0 deve essere utilizzato con Java 10.

### <a name="support-for-jdk-10"></a>Supporto per JDK 10

Microsoft JDBC Driver 7.0 per SQL Server è ora compatibile con Java Development Kit (JDK) versione 10.0, oltre a JDK 1.8. Questo aggiornamento espone anche del driver 'automatico-Module-Name' come `com.microsoft.sqlserver.jdbc` attraverso file manifesto corrispondente.

### <a name="support-for-spatial-datatypes"></a>Supporto per tipi di dati spaziali

Microsoft JDBC Driver 7.0 per SQL Server offre ora il supporto per tipi spaziali di SQL Server 'Geography' e 'Geometry'. Per altre informazioni sui tipi di dati spaziali API e come usarli, vedere [qui](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Implementazione per JDBC 4.3 che ha introdotto le API java.sql.Connection beginRequest() ed endRequest()

Microsoft JDBC Driver 7.0 per SQL Server ora implements `beginRequest()` e `endRequest()` API da `java.sql.Connection` classe. Queste API sono stati introdotti con JDBC 4.3 specifiche e JDK 9. Per altre informazioni sull'implementazione del driver di queste API, vedere [qui](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Supporto di 'Individuazione dati e classificazione SQL'

Microsoft JDBC Driver 7.0 per SQL Server fornisce supporto per funzionalità 'individuazione dati SQL e classificazione' con qualsiasi database di destinazione che supporta questa funzionalità. Il driver ora espone `SQLServerResultSet.getSensitivityClassification()` API per estrarre queste informazioni dal set di risultati recuperato.

Per altre informazioni su come usare questa funzionalità con il Driver JDBC, vedere l'esempio [qui](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-new-connection-property-usebulkcopyforbatchinsert"></a>Aggiunta nuova proprietà di connessione: useBulkCopyForBatchInsert

Microsoft JDBC Driver 7.0 per SQL Server introduce una nuova proprietà di connessione 'useBulkCopyForBatchInsert', che è supportato solo per **Azure Data Warehouse**.

Questa proprietà è **disabilitato** per impostazione predefinita e può essere abilitata per migliorare le prestazioni delle applicazioni utente durante il push di grandi quantità dei dati in Azure Data Warehouse. Abilitazione di questa proprietà viene modificato il comportamento delle operazioni di inserimento Batch per passare alle operazioni di copia Bulk con i dati forniti dall'utente. Per altre informazioni su questa proprietà e le relative limitazioni, vedere [qui](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-new-connection-property-cancelquerytimeout"></a>Aggiunta nuova proprietà di connessione: cancelQueryTimeout

Microsoft JDBC Driver 7.0 per SQL Server introduce nuove proprietà di connessione, `cancelQueryTimeout`, per annullare `queryTimeout` sul `java.sql.Connection` e `java.sql.Statement` oggetti.

### <a name="added-azure-key-vault-provider-constructors"></a>Aggiunta dell'insieme di credenziali chiave Azure Provider costruttori

Microsoft JDBC Driver 7.0 per SQL Server è stata reintrodotta un costruttore rimosso in precedenza, per `SQLServerColumnEncryptionAzureKeyVaultProvider`, quali consentita l'autenticazione usando un metodo personalizzato implementato sulla `SQLServerKeyVaultAuthenticationCallback` per recuperare un token di accesso.

Nuovi costruttori avere la seguente definizione:

```java
/* This constructor is added to provide backwards compatibility with 6.0
* version of the driver. It is marked deprecated for removal in next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New Constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-adal4j-version-to-160"></a>Versione ADAL4J aggiornata alla versione 1.6.0

Microsoft JDBC Driver 7.0 per SQL Server è aggiornata relativa dipendenza maven dopo azure-activedirectory-library-for-java (ADAL4J) alla versione 1.6.0. Per altre informazioni sulle dipendenze, vedere [qui](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.4 per SQL Server

Microsoft JDBC Driver 6.4 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. I file JAR nel pacchetto di 6,4 sono denominati in base alla compatibilità delle versioni di Java. Ad esempio, il file mssql-jdbc-6.4.0.jre8.jar dal pacchetto di 6,4 deve essere utilizzato con Java 8.

### <a name="support-for-jdk-9"></a>Supporto per JDK 9

Supporto per Java Development Kit (JDK) versione 9.0, oltre a JDK 8.0 e 7.0.

### <a name="jdbc-43-compliance"></a>Conformità a JDBC 4.3

Supporto per la specifica Java Database Connectivity API 4.3, oltre a 4.1 e 4.2. I metodi dell'API di JDBC 4.3 vengono aggiunte ma non ancora implementati. Per informazioni dettagliate, vedere [Conformità con JDBC 4.3 per JDBC Driver](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-new-connection-property-sslprotocol"></a>Aggiunta nuova proprietà di connessione: sslProtocol

Aggiungere una nuova proprietà di connessione che consente agli utenti di specificare la parola chiave protocollo TLS. I valori possibili sono: "TLS", "TLSv1", "TLSv1.1", "TLSv1.2". Visualizzare [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol) per informazioni dettagliate.

### <a name="deprecated-connection-property-fipsprovider"></a>Deprecato proprietà di connessione: fipsProvider

Proprietà di connessione "fipsProvider" viene rimosso dall'elenco delle proprietà di connessione accettata. Visualizzare i dettagli [qui](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-custom-trustmanager"></a>Proprietà di connessione aggiunta per trustmanager personalizzato

Driver ora supporta trustmanager personalizzato con aggiunta "trustManagerClass" e "trustmanagerconstructorarg" "trustManagerConstructorArg". Ciò consente la specifica dinamica di un set di certificati considerati attendibili in una singola connessione senza modificare le impostazioni globali per l'ambiente JVM.

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters-tvp"></a>Aggiunta del supporto per datetime/smallDatetime in parametri con valori di tabella (TVP)

Ora il driver supporta i tipi di dati DATETIME e SMALLDATETIME quando si usano i parametri con valori di tabella (TVP, Table-Valued Parameters).

### <a name="added-support-for-sqlvariant-datatype"></a>Aggiunta del supporto per il tipo di dati sql_variant

Il Driver JDBC supporta ora i tipi di dati sql_variant da utilizzare con SQL Server. Sql_variant è anche supportato con funzionalità quali i parametri con valori di tabella (TVP) e BulkCopy con limitazioni di seguito:

1. Per i valori delle Date: quando si usa TVP per popolare una tabella che contiene i valori datetime/smalldatetime/date nella colonna sql_variant, chiamata di metodi getDateTime()/getSmallDateTime()/getDate() sul set di risultati non funziona e genera l'eccezione seguente:  `java java.lang.String cannot be cast to java.sql.Timestamp` Soluzione alternativa: in alternativa, usare i metodi "GetString ()" o "GetObject ()".

2. Uso di TVP con Variante SQL per valori null

Se si usa TVP per popolare una tabella e invia il valore NULL al tipo di colonna sql_variant, che si incontrano un'eccezione una inserimento valore NULL con tipo di colonna sql_variant in TVP non è attualmente supportata.

### <a name="implemented-prepared-statement-metadata-caching"></a>Implementazione di un'istruzione preparata la memorizzazione nella cache dei metadati

Il Driver JDBC è implementata preparato memorizzazione nella cache dei metadati di istruzione per migliorare le prestazioni. Driver ora supporta la memorizzazione dei metadati Prepared Statement nel driver con le proprietà di connessione "disableStatementPooling" e "statementPoolingCacheSize". Questa funzionalità è disabilitata per impostazione predefinita. Altre informazioni sono disponibili [qui](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)

### <a name="added-support-for-aad-integrated-authentication-on-linuxmac"></a>Aggiunta del supporto per l'autenticazione integrata di AAD in Linux/Mac

Ora il driver JDBC supporta anche l'autenticazione integrata di Azure Active Directory in tutti i sistemi operativi supportati (Windows/Linux/Mac) con Kerberos. In alternativa, in sistemi operativi Windows, gli utenti possono eseguire l'autenticazione con sqljdbc_auth.

### <a name="updated-adal4j-version-to-140"></a>Versione aggiornata di ADAL4J per 1.4.0

Il Driver JDBC è aggiornata relativa dipendenza maven dopo azure-activedirectory-library-for-java (ADAL4J) alla versione 1.4.0. Per altre informazioni sulle dipendenze, vedere [qui](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.2 per SQL Server

Microsoft JDBC Driver 6.2 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. I file JAR nel pacchetto 6.2 sono denominati in base alla compatibilità delle versioni di Java. Ad esempio, il file mssql-jdbc-6.2.2.jre8.jar dal pacchetto 6.2 è consigliato per l'uso con Java 8.

> [!NOTE]  
> Un problema con il miglioramento di memorizzazione nella cache dei metadati è stato trovato nella versione RTW 6.2 JDBC rilasciata il 29 giugno 2017. È stato eseguito il rollback il miglioramento e nuovo file con estensione jar (versione 6.2.1) sono state rilasciate 17 luglio 2017. 
>
> È stato effettuato un altro miglioramento per eseguire l'aggiornamento di versione della libreria dipendente da Azure Key Vault a 1.0.0 e nuovo file con estensione jar (versione 6.2.2) sono stati rilasciati il 19 ottobre 2017.
>
> Scaricare gli aggiornamenti più recenti in JDBC Driver 6.2 sul [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2), e [Maven Central](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Aggiornare i progetti per l'uso di 6.2.2 rilasciare i file con estensione jar. Note sulla versione per visualizzare [v6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) e [v6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2) per altri dettagli.

### <a name="azure-active-directory-aad-support-for-linux"></a>Supporto tecnico di Azure Active Directory (AAD) per Linux

Connettere le applicazioni di Linux per il Database SQL di Azure Usa l'autenticazione di AAD tramite i metodi di token nome utente/password e l'accesso.

### <a name="federal-information-processing-standard-fips-enabled-jvms"></a>Federal Information Processing Standard (FIPS) abilitato JVM

Il Driver JDBC ora utilizzabile nella JVM eseguiti in modalità di compatibilità FIPS 140 per soddisfare gli standard federali e conformità.

### <a name="kerberos-authentication-improvements"></a>Miglioramenti di autenticazione Kerberos

Il Driver JDBC include ora il supporto per:

- Metodo di entità e la Password per le applicazioni in cui la configurazione di Kerberos non può essere modificato o non è possibile recuperare un nuovo token o keytab. Questo metodo può essere utilizzato per l'autenticazione a un Server SQL che consente solo l'autenticazione Kerberos.
- Autenticazione tra aree tramite l'autenticazione integrata Kerberos di senza impostare in modo esplicito il nome SPN del server. Il driver adesso viene calcolato automaticamente l'area di autenticazione anche quando esso non è stato fornito.
- La delega vincolata Kerberos mediante l'accettazione di rappresentare le credenziali dell'utente come un oggetto credenziali GSS tramite l'origine dati. Questa credenziale rappresentata viene quindi usata per stabilire una connessione di Kerberos.

### <a name="added-timeouts"></a>Aggiunta dei timeout

Il Driver JDBC supporta ora possibile configurare i timeout seguenti che è possibile modificare in base alle esigenze dell'applicazione:

- Timeout della query per controllare il numero di secondi di attesa prima che si verifica un timeout durante l'esecuzione di una query.
- Timeout del socket per specificare il numero di millisecondi di attesa prima che si verifica un timeout su un socket di lettura o accettare.

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.1 per SQL Server

Il Microsoft JDBC Driver 6.1 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. Questa è la versione open source iniziale del Driver JDBC e contiene i file mssql-jdbc-6.1.0.jre7.jar mssql-jdbc-6.1.0.jre8.jar, che corrispondono alla compatibilità tra le versioni di Java.

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.0 per SQL Server

Microsoft JDBC Driver 6.0 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. I file JAR nel pacchetto 6.0 sono denominate secondo la conformità con la versione dell'API di JDBC. Ad esempio, il file sqljdbc42.jar dal pacchetto 6.0 è conforme a JDBC API 4.2. Analogamente, il file sqljdbc41.jar è conforme con JDBC 4.1 di API.

Per assicurarsi che si dispone di sqljdbc41.jar o sqljdbc42.jar a destra, eseguire le seguenti righe di codice. Se l'output è "versione del Driver: versione 6.0.7507.100", è necessario il pacchetto di JDBC Driver 6.0.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Crittografia sempre attiva

Supporto per la funzionalità Crittografia sempre attiva rilasciata di recente in SQL Server 2016, una nuova funzionalità di sicurezza che assicura che i dati sensibili non siano visualizzati come testo non crittografato in un'istanza di SQL Server. Crittografia sempre attiva crittografa in modo trasparente i dati nell'applicazione, in modo che SQL Server debba gestire solo i dati crittografati e non i valori di testo non crittografato. In caso di compromissione dell'istanza di SQL o del computer host, un utente malintenzionato ottiene solo il testo crittografato dei dati sensibili. Per informazioni dettagliate, vedere [Uso di Always Encrypted con il JDBC Driver](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-name-idn"></a>Internationalized Domain Name (IDN)

Supporto per nomi IDN (Internationalized Domain Name) per i nomi dei server. Per informazioni dettagliate, vedere Utilizzo di International Domain Names nel [funzioni internazionali del Driver JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md) pagina.

### <a name="parameterized-query"></a>Query con parametri

Ora viene fornito il supporto per il recupero dei metadati dei parametri con istruzioni preparate per le query complesse, ad esempio le sottoquery e/o i join. Questo miglioramento è disponibile solo quando si usa SQL Server 2012 e versioni successive.

### <a name="azure-active-directory-aad"></a>Azure Active Directory (AAD)

L'autenticazione AAD è un meccanismo di connessione al Database SQL di Azure v12 usando le identità di AAD. Usare l'autenticazione di Azure Active Directory per gestire centralmente le identità degli utenti del database e come alternativa all'autenticazione di SQL Server. Il driver JDBC 6.0 consente di specificare le credenziali di Azure Active Directory nella stringa di connessione JDBC per connettersi al database SQL di Azure. Per altre informazioni vedere la proprietà di autenticazione sul [impostazione delle proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md) pagina.

### <a name="table-valued-parameters"></a>Parametri con valori di tabella

I parametri con valori di tabella offrono un modo semplice per effettuare il marshalling di più righe di dati da un'applicazione client di SQL Server senza richiedere più round trip o una logica speciale sul lato server per l'elaborazione dei dati. I parametri con valori di tabella possono essere usati per incapsulare le righe di dati in un'applicazione client e inviare i dati al server in un singolo comando con parametri. Le righe di dati in ingresso vengono archiviate in una variabile di tabella che può quindi essere utilizzata tramite Transact-SQL. Per informazioni dettagliate, vedere [Using Table-Valued parametri](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="alwayson-availability-groups-ag"></a>Gruppi di disponibilità AlwaysOn

Il driver ora supporta le connessioni trasparenti ai gruppi di disponibilità AlwaysOn. Il driver individua rapidamente la topologia AlwaysOn corrente dell'infrastruttura server e si connette in modo trasparente al server attivo corrente.

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Aggiornamenti in Microsoft JDBC Driver 4.2 per SQL Server e versioni successive

Microsoft JDBC Driver 4.2 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. I file JAR nel pacchetto 4.2 sono denominate secondo la conformità con la versione dell'API di JDBC. Ad esempio, il file sqljdbc42.jar dal pacchetto 4.2 è conforme a JDBC API 4.2. Analogamente, il file sqljdbc41.jar è conforme con JDBC 4.1 di API.

Per assicurarsi che si dispone di sqljdbc41.jar o sqljdbc42.jar a destra, eseguire le seguenti righe di codice. Se l'output è "versione del Driver: 4.2.6420.100", è necessario il pacchetto di Driver JDBC 4.2.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Supporto per JDK 8

Supporto per Java Development Kit (JDK) versione 8.0, oltre a JDK 7.0, 6.0 e 5.0.

### <a name="jdbc-41-and-42-compliance"></a>Conformità con JDBC 4.1 e 4.2

Supporto per le specifiche Java Database Connectivity API 4.1 e 4.2, oltre a 4.0. Per informazioni dettagliate, vedere [conformità a JDBC 4.1 per il Driver JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) e [JDBC 4.2 conformità per il Driver JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Copia bulk

La funzionalità di copia bulk viene utilizzata per copiare rapidamente grandi quantità di dati in tabelle o viste nei database di SQL Server. Per informazioni dettagliate, vedere [Uso della copia bulk con il driver JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Opzione di rollback di transazione XA

Aggiunte nuove opzioni di timeout per il rollback automatico esistente di transazioni non preparate. Per informazioni dettagliate, vedere [informazioni sulle transazioni XA](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Nuova proprietà di connessione principale Kerberos

Aggiunta una nuova proprietà di connessione per aumentare la flessibilità con le connessioni Kerberos. Per informazioni dettagliate, vedere [Uso dell'autenticazione integrata Kerberos per la connessione a SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Aggiornamenti in Microsoft JDBC Driver 4.1 per SQL Server e versioni successive

### <a name="support-for-jdk-7"></a>Supporto per JDK 7

Supporto per Java Development Kit (JDK) versione 7.0, oltre a JDK 6.0 e 5.0.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Le applicazioni JDBC Driver 6.4, 6.0, 4.2 e 4.1 non supportano i computer Itanium

Le applicazioni Microsoft JDBC Driver 6.4, 6.0, 4.2 e 4.1 per SQL Server non supportano i computer Itanium.

## <a name="see-also"></a>Vedere anche

[Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)
