---
title: Documentazione tecnica di SQL Server | Documenti Microsoft
ms.date: 03/24/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.portal.f1
helpviewer_keywords:
- documentation [SQL Server], home page
- Help [SQL Server]
- SQL Server, documentation
- home page [SQL Server]
- Help [SQL Server], documentation home page
- Books Online [SQL Server], home page
- portal page [SQL Server]
ms.assetid: 674933a8-e423-4d44-a39b-2a997e2c2333
caps.latest.revision: 106
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 6ba40fbd036ee6476d7eb3439a5d9e816e79651d
ms.contentlocale: it-it
ms.lasthandoff: 05/25/2017

---
# <a name="sql-server-technical-documentation"></a>Documentazione tecnica di SQL Server
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 > Per contenuti relativi a versioni precedenti di SQL Server, vedere [installazione per SQL Server 2014](https://msdn.microsoft.com/en-US/library/bb500469(SQL.120).aspx).

 Documentazione per installare, configurare e usare SQL Server. Il contenuto include esempi end-to-end, esempi di codice e video. Per gli argomenti relativi al linguaggio di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] , vedere [Guida di riferimento al linguaggio](../t-sql/language-reference.md).

**SQL Server 2017**

- [Note sulla versione di SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)
- [Novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)
 
**SQL Server 2016:**
 
- [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
- [Novità di SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)
    
 **Prova SQL Server&2016;**    
 - [**Scaricare SQL Server 2016 da Evaluation Center**](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) 
 - **[Spin up a Virtual Machine with SQL Server 2016 already installed](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)** (Accedere a una macchina virtuale con SQL Server 2016 già installato)    
 - **[Scaricare SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**   
      
## <a name="sql-server-technologies"></a>Tecnologie di SQL Server    
    
|||    
|-|-|    
|![Motore di database SQL](../sql-server/media/sql-database-engine.png "Motore di database SQL")|**[Motore di database](../database-engine/configure-windows/sql-server-database-engine.md)**<br /><br /> Il motore di database è il servizio di base per l'archiviazione, l'elaborazione e la protezione dei dati e assicura un accesso controllato e una rapida elaborazione delle transazioni per soddisfare i requisiti delle applicazioni a più alto utilizzo di dati all'interno dell'organizzazione. Il motore di database offre inoltre un supporto completo per garantire alti livelli di disponibilità.|    
|![R Server](../sql-server/media/r-server.png "R Server")|**[R Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> Microsoft R Services offre molti modi per incorporare il popolare linguaggio R nei flussi di lavoro aziendali.<br /><br /> [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] integra il linguaggio R con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], semplificando la compilazione, la ripetizione del training e l'assegnazione del punteggio dei modelli chiamando le stored procedure [!INCLUDE[tsql](../includes/tsql-md.md)] .<br /><br /> Microsoft R Server fornisce il supporto multipiattaforma e scalabile per R nell'organizzazione e supporta origini dati quali Hadoop e Teradata.|    
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> SQL Server Data Quality Services (DQS) offre una soluzione di pulizia dei dati basata sulle informazioni. DQS consente di compilare una Knowledge Base e di usarla per eseguire correzioni di dati e processi di deduplication sui dati in uso tramite mezzi sia computerizzati sia interattivi. È possibile usare servizi dati di riferimento basati su cloud nonché compilare una soluzione di gestione dati che consenta di integrare DQS con SQL Server Integration Services e Master Data Services.|    
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è una piattaforma per la compilazione di soluzioni di integrazione dei dati ad alte prestazioni, con pacchetti che consentono l'elaborazione ETL (estrazione, trasformazione e caricamento) per il data warehousing.|    
|![Master Data Services](../sql-server/media/master-data-services.png)|**[Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è la soluzione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per la gestione dei dati master. Una soluzione compilata in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] garantisce che l'esecuzione di operazioni di creazione di report e di analisi siano basate su informazioni corrette. Usando [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], si crea un repository centrale per i dati master e si gestisce un record controllabile e a protezione diretta di tali dati man mano che vengono modificati nel tempo.|    
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] è una piattaforma e un set di strumenti di dati analitici per soluzioni di Business Intelligence personali, per team e aziendali. I server e le utilità di progettazione client supportano soluzioni OLAP tradizionali, nuove soluzioni di modellazione tabulare, nonché analisi e collaborazione in modalità self-service con [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], Excel e un ambiente SharePoint Server. In[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sono incluse anche funzionalità di data mining per individuare le relazioni e i modelli nascosti all'interno di elevati volumi di dati.|    
|![Servizi di replica](../sql-server/media/replication-services.png "Servizi di replica")|**[Replica](../relational-databases/replication/sql-server-replication.md)**<br /><br /> La replica è costituita da un set di tecnologie per la copia e la distribuzione di oggetti di database e dati da un database a un altro e dalla successiva sincronizzazione dei database allo scopo di mantenerne la consistenza. Tramite la funzione di replica è possibile distribuire i dati in diverse posizioni a utenti remoti o mobili tramite reti LAN o WAN, connessioni remote, connessioni wireless e Internet.|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Reporting Services offre funzionalità Web aziendali per la gestione e la creazione di report usando come contenuto una serie di origini dati diverse, la pubblicazione dei report in vari formati e la gestione centralizzata della sicurezza e delle sottoscrizioni.|    

    
## <a name="earlier-sql-server-versions"></a>Versioni precedenti di SQL Server
- [Documentazione Online per la documentazione Online di SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx)
- [Installare SQL Server 2014 Express e altre versioni di SQL Server precedenti](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx). (**Grazie a [Scott Hanselman](http://www.hanselman.com/) per la raccolta di tutti i collegamenti ai pacchetti del programma di installazione in un unico posto**)  
- [Documentazione tecnica di SQL Server 2012](https://technet.microsoft.com/library/bb418433(v=sql.10).aspx)  
- [Documentazione del prodotto di SQL Server 2008 R2](https://msdn.microsoft.com/library/hh278298(v=sql.10).aspx)  
- [Documentazione tecnica di SQL Server 2008](https://msdn.microsoft.com/library/hh994727(v=sql.10).aspx) 
- [Documentazione archiviata di SQL Server 2005](https://msdn.microsoft.com/library/hh278313(v=sql.10).aspx)    

**Database di esempio**  
- [Database di esempio Wide World Importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx)  
- [Database di esempio AdventureWorks e script per SQL Server 2016](https://www.microsoft.com/en-us/download/details.aspx?id=49502) 
- [Esempi di SQL Server in GitHub](https://github.com/Microsoft/sql-server-samples) 
   
 ## <a name="more-information"></a>Ulteriori informazioni   
+ [Gestione configurazione SQL Server](../relational-databases/sql-server-configuration-manager.md)
+ [Pagina relativa al centro aggiornamenti di SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) con collegamenti e informazioni per tutte le versioni supportate 
+ [Installare il motore di database di SQL Server](../database-engine/install-windows/install-sql-server-database-engine.md) 
+ [Install SQL Server Management Tools with SSMS](https://msdn.microsoft.com/library/bb500441.aspx) 
+ [SQL Server Data Tools in Visual Studio 2015](https://msdn.microsoft.com/mt186501.aspx)
+ [Videos, samples, and community resources](https://msdn.microsoft.com/library/dn237258.aspx)
  
[!INCLUDE[feedback_stackoverflow_msdn_connect-md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

