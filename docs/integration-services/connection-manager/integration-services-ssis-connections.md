---
title: "Connessioni in Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.connectionmanager.f1"
  - "sql13.dts.designer.adddtsconnection.f1"
helpviewer_keywords: 
  - "Pacchetti di Integration Services, connessioni"
  - "Pacchetti SSIS, connessioni"
  - "origini [Integration Services], connessioni"
  - "pacchetti [Integration Services], connessioni"
  - "destinazioni [Integration Services], connessioni"
  - "attività [Integration Services], connessioni"
  - "connessioni [Integration Services], informazioni sulle connessioni"
  - "connessioni [Integration Services]"
  - "pacchetti di SQL Server Integration Services, connessioni"
ms.assetid: 72f5afa3-d636-410b-9e81-2ffa27772a8c
caps.latest.revision: 92
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 91
---
# Connessioni in Integration Services (SSIS)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] vengono utilizzate le connessioni per eseguire varie attività e implementare le funzionalità di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] seguenti:  
  
-   Connessione ad archivi dati di origine e destinazione, ad esempio file di testo, file XML, cartelle di lavoro di Excel e database relazionali, per l'estrazione e il caricamento dei dati.  
  
-   Connessione a database relazionali contenenti dati di riferimento per l'esecuzione di ricerche esatte o fuzzy.  
  
-   Connessione a database relazionali per l'esecuzione di stored procedure e istruzioni SQL quali i comandi SELECT, DELETE e INSERT.  
  
-   Connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'esecuzione di attività di manutenzione e trasferimento quali il backup di database e il trasferimento di account di accesso.  
  
-   Scrittura di voci di log in file di testo e XML e scrittura di configurazioni di pacchetto e tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la creazione di tabelle di lavoro temporanee, necessarie per l'esecuzione delle operazioni previste da alcune trasformazioni.  
  
-   Connessione a database e progetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per l'accesso a modelli di data mining, l'elaborazione di cubi e dimensioni, nonché l'esecuzione di codice DDL.  
  
-   Creazione o indicazione di file e cartelle da utilizzare con attività ed enumeratori del ciclo Foreach.  
  
-   Connessione a code di messaggi e a server di posta elettronica, Web, Strumentazione gestione Windows (WMI) e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).  
  
 Per stabilire queste connessioni, in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] vengono utilizzate le gestioni connessioni, come descritto nella sezione successiva.  
  
## Gestioni connessioni  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene utilizzata la gestione connessione come rappresentazione logica di una connessione. In fase di progettazione si impostano le proprietà della gestione connessione per descrivere la connessione fisica che verrà creata da [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] durante l'esecuzione del pacchetto. Le gestioni connessioni includono ad esempio la proprietà **ConnectionString** , che viene impostata in modalità progettazione. In fase di esecuzione verrà quindi creata una connessione fisica utilizzando il valore archiviato nella proprietà relativa alla stringa di connessione.  
  
 In un pacchetto è possibile utilizzare più istanze di un determinato tipo di gestione connessione ed è possibile impostare proprietà specifiche per ogni istanza. In fase di esecuzione ogni istanza di un determinato tipo di gestione connessione crea una connessione con attributi diversi.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consentono di stabilire connessioni tra i pacchetti e un'ampia gamma di server e origini dati:  
  
-   Durante l'installazione di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] vengono installate le gestioni connessioni predefinite.  
  
-   Dal sito Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] è possibile scaricare alcune gestioni connessioni.  
  
-   Se le gestioni connessioni esistenti non soddisfano le proprie esigenze, è possibile creare una gestione connessione personalizzata.  
  
### Gestioni connessioni predefinite  
 Nella tabella seguente sono elencati i tipi di gestione connessione disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
|Tipo|Description|Argomento|  
|----------|-----------------|-----------|  
|ADO|Consente di connettersi a oggetti ADO (ActiveX Data Objects).|[Gestione connessione ADO](../../integration-services/connection-manager/ado-connection-manager.md)|  
|ADO.NET|Consente di connettersi a un'origine dei dati tramite un provider .NET.|[Gestione connessione ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)|  
|CACHE|Consente di leggere i dati dal flusso di dati o da un file di cache (caw) e di salvare i dati nel file di cache.|[Gestione connessione della cache](../../integration-services/data-flow/transformations/cache-connection-manager.md)|  
|DQS|Consente di connettersi a un server Data Quality Services e a un database Data Quality Services nel server.|[Gestione connessione DQS Cleansing](../../integration-services/data-flow/transformations/dqs-cleansing-connection-manager.md)|  
|EXCEL|Consente di connettersi a un file della cartella di lavoro di Excel.|[Gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager.md)|  
|FILE|Consente di connettersi a un file o a una cartella.|[Gestione connessione file](../../integration-services/connection-manager/file-connection-manager.md)|  
|FLATFILE|Consente di connettersi ai dati contenuti in un singolo file flat.|[Gestione connessione file flat](../../integration-services/connection-manager/flat-file-connection-manager.md)|  
|FTP|Consente di connettersi a un server FTP.|[Gestione connessione FTP](../../integration-services/connection-manager/ftp-connection-manager.md)|  
|HTTP|Consente di connettersi a un server Web.|[Gestione connessione HTTP](../../integration-services/connection-manager/http-connection-manager.md)|  
|MSMQ|Consente di connettersi a una coda di messaggi.|[Gestione connessione MSMQ](../../integration-services/connection-manager/msmq-connection-manager.md)|  
|MSOLAP100|Consente di connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|[Gestione connessione Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)|  
|MULTIFILE|Consente di connettersi a più file e cartelle.|[Gestione connessione per più file](../../integration-services/connection-manager/multiple-files-connection-manager.md)|  
|MULTIFLATFILE|Consente di connettersi a più file e cartelle di dati.|[Gestione connessione per più file flat](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md)|  
|OLEDB|Consente di connettersi a un'origine dei dati tramite un provider OLE DB.|[Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)|  
|ODBC|Consente di connettersi a un'origine dei dati tramite ODBC.|[Gestione connessione ODBC](../../integration-services/connection-manager/odbc-connection-manager.md)|  
|SMOServer|Consente di connettersi a un server SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects).|[Gestione connessione SMO](../../integration-services/connection-manager/smo-connection-manager.md)|  
|SMTP|Consente di connettersi a un server di posta SMTP.|[Gestione connessione SMTP](../../integration-services/connection-manager/smtp-connection-manager.md)|  
|SQLMOBILE|Consente di connettersi a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.|[Gestione connessione SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|  
|WMI|Consente di connettersi a un server e specifica l'ambito della gestione WMI (Windows Management Instrumentation, Strumentazione gestione Windows) sul server.|[Gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager.md)|  
  
### Gestioni connessioni disponibili per download  
 Nella tabella seguente sono elencati i tipi aggiuntivi di gestione connessione che è possibile scaricare dal sito Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
> [!IMPORTANT]  
>  Le gestioni connessioni elencate nella tabella seguente funzionano unicamente con [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] e [!INCLUDE[ssDeveloperEd11](../../includes/ssdevelopered11-md.md)].  
  
|Tipo|Description|Argomento|  
|----------|-----------------|-----------|  
|ORACLE|Consente di connettersi a un server Oracle \<version info>.|La gestione connessione Oracle è il componente per la gestione delle connessioni del connettore [!INCLUDE[msCoName](../../includes/msconame-md.md)] per Oracle di Attunity. Il connettore [!INCLUDE[msCoName](../../includes/msconame-md.md)] per Oracle di Attunity include anche un'origine e una destinazione. Per ulteriori informazioni, vedere la pagina di download relativa ai [connettori Microsoft per Oracle e Teradata di Attunity](http://go.microsoft.com/fwlink/?LinkId=251526).|  
|SAPBI|Consente di connettersi a un sistema SAP NetWeaver BI versione 7.|La gestione connessione SAP BI è il componente per la gestione delle connessioni del connettore [!INCLUDE[msCoName](../../includes/msconame-md.md)] per SAP BI. Il connettore [!INCLUDE[msCoName](../../includes/msconame-md.md)] per SAP BI include anche un'origine e una destinazione. Per ulteriori informazioni, vedere la pagina di download relativa al [Feature Pack di Microsoft SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=262016).|  
|TERADATA|Consente di connettersi a un server Teradata \<version info>.|La gestione connessione Teradata è il componente per la gestione delle connessioni del connettore [!INCLUDE[msCoName](../../includes/msconame-md.md)] per Teradata di Attunity. Il connettore [!INCLUDE[msCoName](../../includes/msconame-md.md)] per Teradata di Attunity include anche un'origine e una destinazione. Per ulteriori informazioni, vedere la pagina di download relativa ai [connettori Microsoft per Oracle e Teradata di Attunity](http://go.microsoft.com/fwlink/?LinkId=251526).|  
  
### Gestioni connessioni personalizzate  
 È inoltre possibile scrivere gestioni connessioni personalizzate. Per ulteriori informazioni, vedere [Developing a Custom Connection Manager](../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md).  
  
## Attività correlate  
 Per informazioni dettagliate su come aggiungere o eliminare una gestione connessione in un pacchetto, vedere [Aggiunta, eliminazione o condivisione di una gestione connessione in un pacchetto](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md).  
  
 Per informazioni dettagliate su come impostare le proprietà di una gestione connessione in un pacchetto, vedere [Impostazione delle proprietà di una gestione connessione](../Topic/Set%20the%20Properties%20of%20a%20Connection%20Manager.md).
  
  
## Contenuto correlato  
  
-   Video sull' [utilizzo del Connettore Microsoft per Oracle di Attunity per migliorare le prestazioni del pacchetto](http://technet.microsoft.com/sqlserver/gg598963.aspx)sul sito Web technet.microsoft.com  
  
-   Articoli di Wiki sulla [connettività di SSIS](http://social.technet.microsoft.com/wiki/contents/articles/sql-server-integration-services-ssis.aspx#Connectivity), sul sito Web social.technet.microsoft.com  
  
-   Intervento nel blog relativo alla [connessione a MySQL da SSIS](http://go.microsoft.com/fwlink/?LinkId=217669)sul sito blogs.msdn.com.  
  
-   Articolo tecnico relativo all' [estrazione e al caricamento dei dati SharePoint in SQL Server Integration Services](http://go.microsoft.com/fwlink/?LinkId=247826)sul sito Web msdn.microsoft.com.  
  
-   Articolo tecnico [You get "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" error message when using Oracle connection manager in SSIS](http://go.microsoft.com/fwlink/?LinkId=233696) (Visualizzazione del messaggio di errore "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" quando si utilizza la gestione connessione Oracle in SSIS) sul sito support.microsoft.com.  
  
  