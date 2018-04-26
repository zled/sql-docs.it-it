---
title: Documentazione di SQL Server | Microsoft Docs
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
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
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
monikerRange: '>= sql-server-2014 || = sqlallproducts-allversions'
ms.openlocfilehash: 06ccc15f14599c1d9861af90d6a56d65b71e3e0e
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="sql-server-documentation"></a>Documentazione di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server è una parte essenziale della piattaforma dati di Microsoft. SQL Server è leader del settore dei sistemi di gestione di database operativi (ODBMS, Operational Database Management System). Questa documentazione consente di installare, configurare e usare SQL Server. Il contenuto include esempi end-to-end, esempi di codice e video. Per gli argomenti relativi al linguaggio di SQL Server, vedere [Guida di riferimento al linguaggio](../t-sql/language-reference.md).

::: moniker range="=sql-server-2017"
|Novità  | Note sulla versione  |
|---------|---------|
|[Novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)     | [Note sulla versione di SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)        |
::: moniker-end
::: moniker range="=sql-server-2016"
|Novità  | Note sulla versione  |
|---------|---------|
|[Novità di SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)     | [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)        |
::: moniker-end

::: moniker range="=sql-server-2014"
![info_tip](../sql-server/media/info-tip.png) Il contenuto di SQL Server 2014 verrà presto unito al sito .docs.  Per il momento, vedere:
- [Documentazione online per SQL Server 2014](https://msdn.microsoft.com/en-us/library/ms130214(v=sql.120).aspx)
- [Novità di SQL Server 2014](https://msdn.microsoft.com/library/bb500435(v=sql.120).aspx)
- [SQL Server 2014 Release Notes](../sql-server/sql-server-2014-release-notes.md)
- [Versioni precedenti](https://docs.microsoft.com/en-us/previous-versions/sql/)
::: moniker-end

**Prova SQL Server 2016;**
    + [![Download da Evaluation Center](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [Scaricare SQL Server](http://go.microsoft.com/fwlink/?LinkID=829477)
    + [![Download da Evaluation Center](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
    + [![Download da Evaluation Center](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [Scaricare SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
    + [![Creare una macchina virtuale](../includes/media/azure-vm.png)](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) [Ottenere una macchina virtuale con SQL Server](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)

::: moniker range=">=sql-server-2016 || = sqlallproducts-allversions"
## <a name="sql-server-technologies"></a>Tecnologie di SQL Server

|||
|-|-|
|![Motore di database SQL](../sql-server/media/sql-database-engine.png "Motore di database SQL")|**[Motore di database](../database-engine/sql-server-database-engine-overview.md)**<br /><br /> Il motore di database è il servizio di base per l'archiviazione, l'elaborazione e la protezione dei dati e assicura un accesso controllato e una rapida elaborazione delle transazioni per soddisfare i requisiti delle applicazioni a più alto utilizzo di dati all'interno dell'organizzazione. Il motore di database offre inoltre un supporto completo per garantire alti livelli di disponibilità.|
|![R Server](../sql-server/media/r-server.png "R Server")|**[Machine Learning Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> Microsoft Machine Learning Services supporta l'integrazione dell'apprendimento automatico in flussi di lavoro aziendali mediante l'uso di linguaggi diffusi quali R e Python.<br /><br /> Machine Learning Services (In-Database) integra R e Python in SQL Server, semplificando la compilazione, la ripetizione del training e l'assegnazione di punteggi ai modelli mediante la chiamata di stored procedure.  Microsoft Machine Learning Server offre il supporto su scala aziendale per R e Python, senza bisogno di SQL Server.|
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è una piattaforma per la compilazione di soluzioni di integrazione dei dati ad alte prestazioni, con pacchetti che consentono l'elaborazione ETL (estrazione, trasformazione e caricamento) per il data warehousing.|
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] è una piattaforma e un set di strumenti di dati analitici per soluzioni di Business Intelligence personali, per team e aziendali. I server e le utilità di progettazione client supportano soluzioni OLAP tradizionali, nuove soluzioni di modellazione tabulare, nonché analisi e collaborazione in modalità self-service con [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], Excel e un ambiente SharePoint Server. In[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sono incluse anche funzionalità di data mining per individuare le relazioni e i modelli nascosti all'interno di elevati volumi di dati.|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Reporting Services offre funzionalità di reporting abilitate per il Web di livello Enterprise.  È possibile creare report e prelevare contenuti da un'ampia gamma di origini dati, pubblicare report in vari formati e attuare una gestione centralizzata della sicurezza e delle sottoscrizioni.|
|![Servizi di replica](../sql-server/media/replication-services.png "Servizi di replica")|**[Replica](../relational-databases/replication/sql-server-replication.md)**<br /><br /> La replica è costituita da un set di tecnologie per la copia e la distribuzione di oggetti di database e dati da un database a un altro e dalla successiva sincronizzazione dei database allo scopo di mantenerne la consistenza. Tramite la funzione di replica è possibile distribuire i dati in diverse posizioni a utenti remoti o mobili tramite reti LAN o WAN, connessioni remote, connessioni wireless e Internet.|
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> SQL Server Data Quality Services (DQS) offre una soluzione di pulizia dei dati basata sulle informazioni. DQS consente di compilare una Knowledge Base e di usarla per eseguire correzioni di dati e processi di deduplication sui dati in uso tramite mezzi sia computerizzati sia interattivi. È possibile usare servizi dati di riferimento basati su cloud nonché compilare una soluzione di gestione dati che consenta di integrare DQS con SQL Server Integration Services e Master Data Services.|
|![Master Data Services](../sql-server/media/master-data-services.png)|**[Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è la soluzione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per la gestione dei dati master. Una soluzione compilata in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] garantisce che l'esecuzione di operazioni di creazione di report e di analisi siano basate su informazioni corrette. Usando [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], si crea un repository centrale per i dati master e si gestisce un record controllabile e a protezione diretta di tali dati man mano che vengono modificati nel tempo.|
::: moniker-end

## <a name="migrate-and-move-data"></a>Eseguire la migrazione e lo spostamento di dati

- [Importare ed esportare dati con l'Importazione/Esportazione guidata SQL Server](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)
- [Microsoft Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595)
- [Eseguire la migrazione del database SQL Server nel database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

## <a name="update-your-version-of-sql-server"></a>Aggiornare la versione di SQL Server

- [Pagina relativa al centro aggiornamenti di SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) con collegamenti e informazioni per tutte le versioni supportate

## <a name="samples"></a>Esempi

- [Database di esempio Wide World Importers](https://docs.microsoft.com/en-us/sql/samples/wide-world-importers-what-is)
- [Database di esempio AdventureWorks e script per SQL Server 2016](https://docs.microsoft.com/en-us/sql/samples/sql-samples-where-are) 
- [Esempi di SQL Server in GitHub](https://github.com/Microsoft/sql-server-samples)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]