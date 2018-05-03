---
title: Note sulla versione per il Driver JDBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
caps.latest.revision: 206
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c450b8a41c87ec28f0c576f6a8a468e901cdfa2a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="release-notes-for-the-jdbc-driver"></a>Note sulla versione per il Driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.4 per SQL Server
Il Driver JDBC di Microsoft 6.4 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. Il JAR contenuti nel pacchetto 6.4 sono denominati in base alla compatibilità tra versioni di Java. Ad esempio, è consigliabile che il file mssql-jdbc-6.4.0.jre8.jar dal pacchetto di 6,4 utilizzabile con Java 8. 

**Supporto per JDK 9**  
  
Supporto per Java Development Kit (JDK) versione 9.0, oltre a JDK 8.0 e 7.0.
  
**Conformità a JDBC 4.3**  
  
Supporto per la specifica Java Database Connectivity API 4.3, oltre a 4.1 e 4.2. I metodi dell'API di JDBC 4.3 vengono aggiunti ma non ancora implementati. Per informazioni dettagliate, vedere [JDBC 4.3 conformità per il Driver JDBC](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).
 
**Aggiungere una nuova proprietà di connessione: sslProtocol**

Aggiungere una nuova proprietà di connessione che consente agli utenti di specificare la parola chiave protocollo TLS. I valori possibili sono: "TLS", "TLSv1", "TLSv1.1", "TLSv1.2". Vedere [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol) per informazioni dettagliate.

**Deprecato di proprietà di connessione: fipsProvider**

Proprietà di connessione "fipsProvider" viene rimosso dall'elenco di proprietà di connessione accettata. Visualizzare i dettagli [qui](https://github.com/Microsoft/mssql-jdbc/pull/460).

**Proprietà di connessione per l'impostazione TrustManager personalizzato**

Driver supporta ora la definizione TrustManager personalizzati con proprietà di connessione di "trustManagerConstructorArg" e "trustManagerClass" aggiunto. In questo modo per la specifica dinamica di un set di certificati che sono considerati attendibili in ogni connessione senza modificare le impostazioni globali per l'ambiente JVM.

**Aggiunta del supporto per datetime/smallDatetime in parametri con valori di tabella (TVP)**

Driver supporta ora i tipi di dati DATETIME e SMALLDATETIME quando si utilizzano parametri con valori di tabella (TVP).

**Aggiunta del supporto per il tipo di dati sql_variant**

Il Driver JDBC supporta ora i tipi di dati sql_variant da utilizzare con SQL Server. Sql_variant è anche supportato con funzionalità quali parametri con valori di tabella (TVP) e BulkCopy con limitazioni di seguito:

1. Per i valori di data: quando si utilizza TVP per popolare una tabella che contiene valori data/datetime e smalldatetime archiviati nella colonna sql_variant, la chiamata di metodi getDateTime()/getSmallDateTime()/getDate() sul set di risultati non funziona e genera l'eccezione seguente:
    ```
    java.lang.String cannot be cast to java.sql.Timestamp
    ```
    Soluzione alternativa: utilizzare "GetString ()" o "GetObject ()".

2. Utilizzo di TVP con Variant SQL per i valori null

Se si utilizza TVP per popolare una tabella e inviare il valore NULL nel tipo di colonna sql_variant, si verifica un'eccezione durante l'inserimento di valore NULL con tipo di colonna sql_variant in TVP non è attualmente supportato.

**Istruzione preparata implementata la memorizzazione nella cache di metadati**

Il Driver JDBC è implementata preparato memorizzazione nella cache dei metadati di istruzione per migliorare le prestazioni. Driver ora supporta la memorizzazione nella cache i metadati di istruzione preparata nel driver con le proprietà di connessione "disableStatementPooling" e "statementPoolingCacheSize". Questa funzionalità è disabilitata per impostazione predefinita. Altre informazioni sono reperibili [qui](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)

**Aggiunta del supporto per l'autenticazione integrata di AAD su Linux/Mac**

Il Driver JDBC supporta ora anche Azure Active Directory Integrated Authentication in tutti i sistemi operativi (Linux/Windows/Mac) con Kerberos. In alternativa, nei sistemi operativi Windows, gli utenti possono autenticarsi con sqljdbc_auth.dll.

**Versione aggiornata di ADAL4J per 1.4.0**

Il Driver JDBC ha aggiornato la dipendenza maven azure-activedirectory-libreria-per-java (ADAL4J) alla versione 1.4.0. Per ulteriori informazioni sulle dipendenze, fare riferimento a [qui](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.2 per SQL Server
Il Driver JDBC di Microsoft 6.2 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. Il JAR contenuti nel pacchetto 6.0 sono denominati in base alla compatibilità tra versioni di Java. Ad esempio, è consigliabile che il file mssql-jdbc-6.2.1.jre8.jar dal pacchetto 6.2 utilizzabile con Java 8. 

> [!NOTE]  
>  Un problema con il miglioramento di memorizzazione nella cache dei metadati è stato trovato nella RTW 6.2 JDBC ha rilasciato il 29 giugno 2017. È stato eseguito il rollback il miglioramento e nuovo JAR (versione 6.2.1) sono stati rilasciati in 17 luglio 2017 il [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1), e [Maven centrale](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Aggiornare i progetti per l'utilizzo di 6.2.1 JAR di rilascio. Visualizzare [note sulla versione](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) per altri dettagli.

**Supporto tecnico di Azure Active Directory (AAD) per Linux**

Connettere le applicazioni di Linux per Database SQL di Azure utilizzando l'autenticazione AAD tramite i metodi di token nome utente/password e di accesso.

**Federal informazioni Processing Standard (FIPS) abilitato JVMs**

Il Driver JDBC ora utilizzabile JVMs eseguiti in modalità di compatibilità FIPS 140 per soddisfare le norme federali e conformità. 

**Miglioramenti di autenticazione Kerberos** 

Il Driver JDBC include ora il supporto per: 
* Metodo/Password dell'entità per le applicazioni in cui la configurazione di Kerberos non può essere modificato o non è possibile recuperare un nuovo token o keytab. Questo metodo può essere utilizzato per l'autenticazione a un Server SQL che consente solo l'autenticazione Kerberos. 
* Autenticazione tra aree utilizzando l'autenticazione integrata Kerberos di senza impostare in modo esplicito il nome SPN del server. Il driver ora calcola automaticamente l'area di autenticazione anche quando non è stato specificato.
* La delega vincolata Kerberos mediante l'accettazione di rappresentare le credenziali dell'utente come un oggetto credenziale GSS tramite l'origine dati. Questa credenziale rappresentata viene quindi usata per stabilire una connessione di Kerberos. 

**Aggiunta di timeout**

Il Driver JDBC supporta ora possibile configurare i timeout seguenti che è possibile modificare in base alle esigenze dell'applicazione: 
* Quando si esegue una query, si verifica il Timeout di query per controllare il numero di secondi di attesa prima del timeout. 
* Il timeout del socket per specificare il numero di millisecondi di attesa prima che si verifica un timeout su un socket di lettura o accettare. 

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.1 per SQL Server

Nella versione 6.1 Driver JDBC di Microsoft per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. Questa è la versione di origine aprire iniziale del Driver JDBC e contiene i file mssql-jdbc-6.1.0.jre7.jar mssql-jdbc-6.1.0.jre8.jar, che corrispondono per la compatibilità di versione di Java. 

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.0 per SQL Server

Microsoft JDBC Driver 6.0 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. Il JAR contenuti nel pacchetto 6.0 sono denominati in base alla relativa conformità con la versione dell'API di JDBC. Ad esempio, il file sqljdbc42.jar dal pacchetto 6.0 è JDBC API 4.2 è conforme. Analogamente, il file sqljdbc41.jar è compatibile con l'API JDBC 4.1.

Per assicurarsi di che avere il diritto sqljdbc42.jar o sqljdbc41.jar, eseguire le seguenti righe di codice. Se l'output è "versione del Driver: 6.0.7507.100", di disporre del pacchetto di Driver JDBC 6.0.
```
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```  
 **Crittografia sempre attiva**  
  
 Supporto per la funzionalità crittografia sempre attiva rilasciata di recente in SQL Server 2016, una nuova funzionalità di sicurezza che assicura che i dati sensibili non siano visualizzati in testo non crittografato in un'istanza di SQL Server. Crittografia sempre attiva crittografa in modo trasparente i dati nell'applicazione, in modo che SQL Server debba gestire solo i dati crittografati e non i valori di testo non crittografato. Anche se l'istanza SQL o del computer host viene compromesso, un utente malintenzionato ottiene è testo crittografato dei dati sensibili. Per informazioni dettagliate, vedere [uso di Always Encrypted con il Driver JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
 **Nome IDN (Internationalized)**  
  
 Supporto per nomi IDN (Internationalized Domain Name) per i nomi dei server. Per informazioni dettagliate, vedere Utilizzo di International Domain Names nel [funzionalità internazionali del Driver JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md) pagina.  
  
 **Query con parametri**  
  
 Ora viene fornito il supporto per il recupero dei metadati dei parametri con istruzioni preparate per le query complesse, ad esempio le sottoquery e/o i join. Questo miglioramento è disponibile solo quando si usa SQL Server 2012 e versioni successive.  
  
 **Azure Active Directory (AAD)**  
  
 L'autenticazione AAD è un meccanismo di connessione al Database SQL di Azure v12 usando le identità in AAD. Utilizzare l'autenticazione di Azure ad per gestire centralmente le identità di utenti del database e come alternativa all'autenticazione di SQL Server. Il Driver JDBC 6.0 consente di specificare le credenziali AAD nella stringa di connessione JDBC per connettersi al database SQL di Azure.  Per informazioni dettagliate, vedere la proprietà di autenticazione nel [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md) pagina.  
  
 **Parametri con valori di tabella**  
  
 Parametri con valori di tabella forniscono un modo semplice per effettuare il marshalling di più righe di dati da un'applicazione client a SQL Server senza richiedere più round trip o logica speciale sul lato di server per l'elaborazione dei dati. È possibile utilizzare parametri con valori di tabella per incapsulare le righe di dati in un'applicazione client e inviare i dati al server in un singolo comando con parametri. Le righe di dati in ingresso vengono archiviate in una variabile di tabella che può quindi essere utilizzata tramite Transact-SQL. Per informazioni dettagliate, vedere [Using Table-Valued parametri](../../connect/jdbc/using-table-valued-parameters.md).  
  
 **Gruppi di disponibilità AlwaysOn (gruppo di disponibilità)**  
  
 Il driver supporta le connessioni trasparenti ai gruppi di disponibilità AlwaysOn. Il driver rapidamente consente di individuare la topologia AlwaysOn corrente dell'infrastruttura server e si connette al server attivo corrente in modo trasparente.  
  
## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Aggiornamenti in Microsoft JDBC Driver 4.2 per SQL Server e versioni successive  
Microsoft JDBC Driver 4.2 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. Il JAR contenuti nel pacchetto 4.2 sono denominati in base alla relativa conformità con la versione dell'API di JDBC. Ad esempio, il file sqljdbc42.jar dal pacchetto 4.2 è JDBC API 4.2 è conforme. Analogamente, il file sqljdbc41.jar è compatibile con l'API JDBC 4.1.

Per assicurarsi di che avere il diritto sqljdbc42.jar o sqljdbc41.jar, eseguire le seguenti righe di codice. Se l'output è "versione del Driver: 4.2.6420.100", di disporre del pacchetto di Driver JDBC 4.2.
```
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```
 **Supporto per JDK 8**  
  
 Supporto per Java Development Kit (JDK) versione 8.0, oltre a JDK 7.0, 6.0 e 5.0.  
  
 **Conformità JDBC 4.1 e 4.2**  
  
 Supporto per le specifiche Java Database Connectivity API 4.1 e 4.2, oltre a 4.0. Per informazioni dettagliate, vedere [conformità a JDBC 4.1 per il Driver JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) e [JDBC 4.2 conformità per il Driver JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).  
  
 **Copia di massa**  
  
 La funzionalità di copia bulk viene utilizzata per copiare rapidamente grandi quantità di dati in tabelle o viste nei database di SQL Server. Per informazioni dettagliate, vedere [tramite copia Bulk con il Driver JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).  
  
 **Opzione di rollback delle transazioni XA**  
  
 Aggiunte nuove opzioni di timeout per il rollback automatico esistente di transazioni non preparate. Per dettagli, vedere [nozioni fondamentali sulle transazioni XA](../../connect/jdbc/understanding-xa-transactions.md).  
  
 **Nuova proprietà di connessione principale Kerberos**  
  
 Aggiunta una nuova proprietà di connessione per aumentare la flessibilità con le connessioni Kerberos. Per dettagli, vedere [utilizzando l'autenticazione integrata Kerberos per connettersi a SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).  
  
## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Aggiornamenti in Microsoft JDBC Driver 4.1 per SQL Server e versioni successive  
 **Supporto per JDK 7**  
  
 Supporto per Java Development Kit (JDK) versione 7.0, oltre a JDK 6.0 e 5.0.  
  
## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium non supportato per le applicazioni JDBC Driver 6.4, 6.0, 4.2 e 4.1  
  
 Microsoft JDBC driver versione 6.4, 6.0, 4.2 e 4.1 per le applicazioni di SQL Server non sono supportati per l'esecuzione in un computer Itanium.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

