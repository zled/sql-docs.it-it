---
title: Creazione di tracce | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 723aeae7-6504-4585-ba8b-3525115bea8b
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32eecd4a6667dd25d58aa9fe09d3382f5dbc374f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="tracing-driver-operation"></a>Creazione di tracce
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'utilizzo di traccia (o registrazione) per risolvere i problemi e problemi con il driver JDBC quando viene utilizzato nell'applicazione. Per abilitare l'utilizzo di traccia, il driver JDBC Usa le API di registrazione in util, che fornisce un set di classi per la creazione di oggetti Logger e LogRecord.  
  
> [!NOTE]  
>  Per il componente nativo (sqljdbc_xa.dll) incluso nel driver JDBC, la creazione di tracce è abilitata grazie al framework Built-In Diagnostics (BID). Per informazioni sul BID, vedere [traccia di accesso ai dati in SQL Server](http://go.microsoft.com/fwlink/?LinkId=70042).  
  
 Quando si sviluppa l'applicazione, è possibile effettuare chiamate a oggetti di Logger, che consentono di creare oggetti LogRecord, che vengono quindi passati a oggetti del gestore per l'elaborazione. Logger e gestore oggetti entrambi vengono utilizzati livelli di registrazione e, facoltativamente, in cui vengono elaborati per definire quali LogRecords i filtri di registrazione. Quando vengono completate le operazioni di registrazione, gli oggetti gestore facoltativamente possono utilizzare gli oggetti del formattatore per pubblicare le informazioni del log.  
  
 Per impostazione predefinita, l'output del framework java.util.logging viene scritto su un file. Tale file deve disporre di autorizzazioni di scrittura per il contesto su cui è in esecuzione il driver JDBC.  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo dei vari oggetti di registrazione per la creazione di tracce dei programmi, vedere la documentazione Java Logging APIs (informazioni in lingua inglese) sul sito Web di Sun Microsystems.  
  
 Nelle sezioni seguenti sono descritti i livelli di registrazione e le categorie che è possibile registrare. Vengono inoltre fornite informazioni sull'abilitazione della creazione di tracce nell'applicazione.  
  
## <a name="logging-levels"></a>Livelli di registrazione  
 A ciascun messaggio di log creato è associato un livello di registrazione. Il livello di registrazione determina l'importanza del messaggio di log, definito dal **livello** classe util. Se abilitata per un livello, la registrazione verrà abilitata per tutti i livelli superiori. In questa sezione vengono descritti i livelli di registrazione per le categorie di registrazione pubbliche e interne. Per ulteriori informazioni sulle categorie di registrazione, vedere la sezione Categorie di registrazione in questo argomento.  
  
 Nella tabella seguente sono descritti i vari livelli di registrazione disponibili per le categorie di registrazione pubbliche.  
  
|Nome|Description|  
|----------|-----------------|  
|SEVERE|Indica un problema grave. Si tratta del livello più elevato. Nel driver JDBC viene utilizzato per segnalare errori ed eccezioni.|  
|WARNING|Indica un potenziale problema.|  
|INFO|Fornisce messaggi informativi.|  
|CONFIG|Fornisce messaggi sulla configurazione. Si noti che il driver JDBC non fornisce attualmente alcun messaggio sulla configurazione.|  
|FINE|Fornisce informazioni di base sulle tracce, incluse tutte le eccezioni generate dai metodi pubblici.|  
|FINER|Fornisce informazioni dettagliate sulle tracce, inclusi tutti i punti di ingresso e di uscita dei metodi pubblici con i tipi di dati dei parametri associati, nonché le proprietà pubbliche per le classi pubbliche. Inoltre, parametri di input, parametri di output e valori restituiti dal metodo ad eccezione di CLOB, BLOB, NCLOB, Reader, \<flusso > restituire tipi di valore.|  
|FINEST|Fornisce le informazioni più dettagliate disponibili sulle tracce. È il livello più basso.|  
|OFF|Disattiva la registrazione.|  
|ALL|Abilita la registrazione di tutti i messaggi.|  
  
 Nella tabella seguente sono descritti i vari livelli di registrazione disponibili per le categorie di registrazione interne.  
  
|Nome|Description|  
|----------|-----------------|  
|SEVERE|Indica un problema grave. Si tratta del livello più elevato. Nel driver JDBC viene utilizzato per segnalare errori ed eccezioni.|  
|WARNING|Indica un potenziale problema.|  
|INFO|Fornisce messaggi informativi.|  
|FINE|Fornisce informazioni di base sulle tracce, incluse la creazione e l'eliminazione di oggetti di base. Fornisce inoltre tutte le eccezioni generate dai metodi pubblici.|  
|FINER|Fornisce informazioni dettagliate sulle tracce, inclusi tutti i punti di ingresso e di uscita dei metodi pubblici con i tipi di dati dei parametri associati, nonché le proprietà pubbliche per le classi pubbliche. Inoltre, parametri di input, parametri di output e valori restituiti dal metodo ad eccezione di CLOB, BLOB, NCLOB, Reader, \<flusso > restituire tipi di valore.<br /><br /> Le seguenti categorie di registrazione erano incluse nella versione 1.2 del driver JDBC e con il livello di registrazione FINE: [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md), [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), XA e [SQLServerDataSource ](../../connect/jdbc/reference/sqlserverdatasource-class.md). A partire dalla versione 2.0 sono state aggiornate al livello FINER.|  
|FINEST|Fornisce le informazioni più dettagliate disponibili sulle tracce. È il livello più basso.<br /><br /> Le seguenti categorie di registrazione erano incluse nella versione 1.2 del driver JDBC con il livello di registrazione FINEST: TDS.DATA e TDS.TOKEN. A partire dalla versione 2.0 hanno mantenuto lo stesso livello di registrazione.|  
|OFF|Disattiva la registrazione.|  
|ALL|Abilita la registrazione di tutti i messaggi.|  
  
## <a name="logging-categories"></a>Categorie di registrazione  
 Quando si crea un oggetto Logger, è necessario indicare l'oggetto che si sia interessati a ottenere informazioni sul log dalla categoria o l'entità denominata. Il driver JDBC supporta le seguenti categorie di registrazione pubbliche, definite tutte nel pacchetto di driver com.microsoft.sqlserver.jdbc.  
  
|Nome|Description|  
|----------|-----------------|  
|Connessione|Registra i messaggi [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINER.|  
|.|Registra i messaggi [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINER.|  
|DataSource|Registra i messaggi [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|ResultSet|Registra i messaggi [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINER.|  
|Driver|Registra i messaggi [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINER.|  
  
 A partire dalla versione 2.0, il driver Microsoft JDBC fornisce anche il pacchetto com.microsoft.sqlserver.jdbc.internals, che include il supporto per la registrazione per le seguenti categorie di registrazione interne.  
  
|Nome|Description|  
|----------|-----------------|  
|AuthenticationJNI|Problemi di autenticazione integrata di messaggi di log relativi a Windows (quando il **authenticationScheme** proprietà di connessione è impostata in modo implicito o esplicito su **NativeAuthentication**).<br /><br /> Le applicazioni possono impostare il livello di registrazione su FINEST e FINE.|  
|SQLServerConnection|Registra i messaggi [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE e FINER.|  
|SQLServerDataSource|Registra i messaggi [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), e [SQLServerPooledConnection](../../connect/jdbc/reference/sqlserverpooledconnection-class.md) classi.<br /><br /> Le applicazioni possono impostare il livello di registrazione su FINER.|  
|InputStream|Consente di registrare i messaggi relativi ai tipi di dati java.io.InputStream e java.io.Reader, nonché ai tipi di dati per i quali è disponibile un identificatore max, ad esempio varchar, nvarchar e varbinary.<br /><br /> Le applicazioni possono impostare il livello di registrazione su FINER.|  
|SQLServerException|Registra i messaggi [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|SQLServerResultSet|Registra i messaggi [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE, FINER e FINEST.|  
|SQLServerStatement|Registra i messaggi [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE, FINER e FINEST.|  
|XA|Registra i messaggi per tutte le transazioni XA il [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE e FINER.|  
|KerbAuthentication|Registra i messaggi relativi autenticazione Kerberos di tipo 4 (quando il **authenticationScheme** connessione è impostata su **JavaKerberos**). L'applicazione può impostare il livello di registrazione su FINE o FINER.|  
|TDS.DATA|Registra i messaggi contenenti la conversazione a livello di protocollo TDS tra il driver e SQL Server. Il contenuto dettagliato di ogni pacchetto TDS inviato e ricevuto viene registrato in formato ASCII ed esadecimale. Le credenziali di accesso (nomi utente e password) non vengono registrati. Tutti gli altri dati vengono registrati.<br /><br /> Questa categoria consente di creare messaggi molto dettagliati ed esaustivi e può essere abilitata solo impostando il livello di registrazione su FINEST.|  
|TDS.Channel|Questa categoria consente di eseguire le tracce delle azioni del canale di comunicazione TCP con SQL Server. I messaggi registrati includono l'apertura e la chiusura di socket, nonché le operazioni di lettura e scrittura. Vengono inoltre eseguite le tracce dei messaggi correlati alla definizione di una connessione SSL (Secure Socket Layer) con SQL Server.<br /><br /> Può essere abilitata solo impostando il livello di registrazione su FINE, FINER o FINEST.|  
|TDS.Writer|Questa categoria consente di eseguire le tracce delle operazioni di scrittura nel canale TDS. Si noti che vengono eseguite le tracce solo della lunghezza delle operazioni di scrittura e non del contenuto. Vengono inoltre eseguite le tracce dei problemi quando al server viene inviato un segnale di attenzione per annullare l'esecuzione di un'istruzione.<br /><br /> Può essere abilitata solo impostando il livello di registrazione su FINEST.|  
|TDS.Reader|Questa categoria consente di eseguire le tracce di alcune operazioni di lettura dal canale TDS con livello FINEST. Con tale livello le tracce possono risultare particolarmente dettagliate. Con i livelli WARNING e SEVERE questa categoria consente di eseguire le tracce quando il driver riceve un protocollo TDS non valido da SQL Server prima della chiusura della connessione.<br /><br /> Può essere abilitata solo impostando il livello di registrazione su FINER e FINEST.|  
|TDS.Command|Le tracce di questa categoria transizioni di stato di basso livello e altre informazioni associate all'esecuzione di comandi TDS, ad esempio [!INCLUDE[tsql](../../includes/tsql_md.md)] esecuzioni di istruzioni, cursori ResultSet, commit e così via.<br /><br /> Può essere abilitata solo impostando il livello di registrazione su FINEST.|  
|TDS.TOKEN|Questa categoria consente di registrare solo i token dei pacchetti di flussi TDS e risulta meno dettagliata della categoria TDS.DATA. Può essere abilitata solo impostando il livello di registrazione su FINEST.<br /><br /> Con il livello FINEST questa categoria consente di eseguire le tracce dei token TDS quando vengono elaborati nella risposta. Con il livello SEVERE esegue le tracce quando viene rilevato un token TDS non valido.|  
|SQLServerDatabaseMetaData|Registra i messaggi [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|SQLServerResultSetMetaData|Registra i messaggi [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|SQLServerParameterMetaData|Registra i messaggi [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|SQLServerBlob|Registra i messaggi [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|SQLServerClob|Registra i messaggi [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|SQLServerSQLXML|Registra i messaggi nella classe SQLServerSQLXML interna. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|SQLServerDriver|Registra i messaggi [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
|SQLServerNClob|Registra i messaggi [SQLServerNClob](../../connect/jdbc/reference/sqlservernclob-class.md) classe. Le applicazioni possono impostare il livello di registrazione su FINE.|  
  
## <a name="enabling-tracing-programmatically"></a>Abilitazione delle tracce a livello di programmazione  
 Analisi può essere abilitata a livello di programmazione creando un oggetto Logger e indicando la categoria da registrare. Il codice seguente, ad esempio, consente di abilitare la registrazione per le istruzioni SQL:  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.FINER);  
```  
  
 Per disabilitare la registrazione dal codice, utilizzare:  
  
```  
logger.setLevel(Level.OFF);  
```  
  
 Per registrare tutte le categorie disponibili, utilizzare:  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc");  
logger.setLevel(Level.FINE);  
```  
  
 Per disabilitare una categoria specifica, utilizzare:  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.OFF);  
```  
  
## <a name="enabling-tracing-by-using-the-loggingproperties-file"></a>Abilitazione delle tracce utilizzando il file Logging.Properties  
 È inoltre possibile abilitare la traccia utilizzando la `logging.properties` file, è reperibile nel `lib` directory di installazione di Java Runtime Environment (JRE). Il file può essere utilizzato per impostare i valori predefiniti degli oggetti logger e handler utilizzati una volta abilitate le tracce.  
  
 Ecco un esempio delle impostazioni che è possibile apportare la `logging.properties` file:  
  
```  
# Specify the handler, the handlers will be installed during VM startup.  
handlers= java.util.logging.FileHandler  
  
# Default global logging level.  
.level= OFF  
  
# default file output is in user's home directory.  
java.util.logging.FileHandler.pattern = %h/java%u.log  
java.util.logging.FileHandler.limit = 5000000  
java.util.logging.FileHandler.count = 20  
java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter  
java.util.logging.FileHandler.level = FINEST  
  
# Facility specific properties.  
com.microsoft.sqlserver.jdbc.level=FINEST  
  
```  
  
> [!NOTE]  
>  È possibile impostare le proprietà `logging.properties` file tramite l'oggetto LogManager che fa parte di util.  
  
## <a name="see-also"></a>Vedere anche  
 [Diagnosi dei problemi relativi al driver JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
