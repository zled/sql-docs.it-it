---
title: Note sulla versione per il Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
caps.latest.revision: "206"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 827840a7aa7e221edaad60060fb51972460808ed
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="release-notes-for-the-jdbc-driver"></a>Note sulla versione per il Driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Aggiornamenti in Microsoft JDBC Driver 6.2 per SQL Server
Il Driver JDBC di Microsoft 6.2 per SQL Server è completamente compatibile con le specifiche JDBC 4.1 e 4.2. Il JAR contenuti nel pacchetto 6.0 sono denominati in base alla compatibilità tra versioni di Java. Ad esempio, è consigliabile che il file mssql-jdbc-6.2.1.jre8.jar dal pacchetto 6.2 utilizzabile con Java 8. 

**Nota:** un problema con i metadati di memorizzazione nella cache di analisi utilizzo software è stato trovato nella RTW 6.2 JDBC ha rilasciato il 29 giugno 2017. È stato eseguito il rollback il miglioramento e nuovo JAR (versione 6.2.1) sono stati rilasciati in 17 luglio 2017 il [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1), e [Maven centrale](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Aggiornare i progetti per l'utilizzo di 6.2.1 JAR di rilascio. Visualizzare [note sulla versione](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) per altri dettagli.

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
  
## <a name="updates-in-microsoft-jdbc-driver-40-for-sql-server-and-later"></a>Aggiornamenti in Microsoft JDBC Driver 4.0 per SQL Server e versioni successive  
 **Informazioni sulla connessione a un Database SQL di Azure**  
  
 È disponibile un nuovo argomento con informazioni sulla connessione a un database SQL di Azure. Vedere [la connessione a un database SQL di Azure](../../connect/jdbc/connecting-to-an-azure-sql-database.md) per ulteriori informazioni.  
  
 **Supporto per il ripristino di emergenza a disponibilità elevato**  
  
 Supporto per le connessioni di ripristino di emergenza a disponibilità elevata a gruppi di disponibilità AlwaysOn in [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]. Vedere [supporto del Driver JDBC per il ripristino di emergenza a disponibilità elevata](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) per ulteriori informazioni.  
  
 **Uso dell'autenticazione integrata Kerberos per la connessione a SQL Server**  
  
 Supporto per l'autenticazione integrata Kerberos di tipo 4 per applicazioni di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Per ulteriori informazioni, vedere [utilizzando l'autenticazione integrata Kerberos per connettersi a SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md). (Kerberos di tipo 2 l'autenticazione integrata è disponibile in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] le versioni precedenti alla 4.0.)  
  
 **Accesso alle informazioni di diagnostica nel log degli eventi estesi**  
  
 È possibile accedere al contenuto del log degli eventi estesi del server per ottenere informazioni sugli errori di connessione. Per ulteriori informazioni, vedere [l'accesso a informazioni di diagnostica nel Log degli eventi estesi](../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
 **Supporto aggiuntivo per le colonne di tipo Sparse**  
  
 Se l'applicazione accede già ai dati in una tabella che usa colonne di tipo sparse, si sarà notato un aumento delle prestazioni. È possibile ottenere informazioni sulle colonne (incluse le informazioni di colonna di tipo sparse) con [getColumns metodo &#40; SQLServerDatabaseMetaData &#41; ](../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md). Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] colonne di tipo sparse, vedere [utilizzando colonne di tipo Sparse](http://go.microsoft.com/fwlink/?LinkId=224244).  
  
 **Xid.getFormatId**  
  
 A partire da [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], il driver JDBC passa l'identificatore di formato dall'applicazione al server di database. Per ottenere il comportamento aggiornato, verificare che il file sqljdbc_xa.dll nel server sia aggiornato. Per ulteriori informazioni sulla copia di una versione aggiornata del file sqljdbc_xa.dll nel server, vedere [nozioni fondamentali sulle transazioni XA](../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="itanium-not-supported-for-jdbc-driver-60-42-41-and-40-applications"></a>Itanium non supportato per le applicazioni JDBC Driver 6.0, 4.2, 4.1 e 4.0  
  
 Microsoft JDBC driver 6.0, 4.2, 4.1 e 4.0 per applicazioni SQL Server non sono supportati per l'esecuzione in un computer Itanium.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
