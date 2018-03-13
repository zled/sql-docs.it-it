---
title: Microsoft Machine Learning Services | Documenti Microsoft
ms.date: 11/09/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 40c76cba27559c8fcc314ce4c9761ee42edacac0
ms.sourcegitcommit: 657d18fc805512c9574b2fe7451310601b9d78cb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="microsoft-machine-learning-services"></a>Microsoft Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'obiettivo di Microsoft Machine Learning Services è fornire una piattaforma estendibile e scalabile per l'integrazione di strumenti e attività di machine learning con le applicazioni che utilizzano i servizi di machine learning. La piattaforma deve soddisfare le esigenze di tutti gli utenti coinvolti nel processo analitica e lo sviluppo di dati da esperti di dati, agli architetti e agli amministratori di database.

Vantaggi principali includono:

+ Analitica scalabile
+ Più piattaforme e i contesti di calcolo, per le soluzioni "una volta del codice, distribuire remoto via Internet"
+ Consente di evitare lo spostamento dei dati e al rischio di dati riportando analitica ai dati
+ Gli esperti di dati è possono scegliere i propri strumenti e linguaggi
+ Si integra le migliori funzionalità di open source con funzionalità aziendali di Microsoft
+ Amministrazione semplificata
+ Facile da distribuire e utilizzare modelli predittivi

## <a name="in-database-analytics-with-sql-server"></a>Analitica nel database con SQL Server

In SQL Server 2016, Microsoft avviato due piattaforme server per integrare il diffuso linguaggio open source R con applicazioni aziendali:

+ **SQL Server R Services (In-Database)**, per l'integrazione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
+ **Microsoft R Server**, per distribuzioni a livello aziendale R nel server Windows e Linux

In SQL Server 2017, il nome è stato modificato per riflettere il supporto per il linguaggio Python diffuso.

+ **SQL Server Machine Learning Services (In-Database)** supporta R sia Python per analitica nel database.
+ **Server di Microsoft Machine Learning** supporta le distribuzioni di R e Python nei cluster di Windows, Linux e HDInsight Spark e Hadoop.

### <a name="benefits"></a>Vantaggi

Servizi di Microsoft Machine Learning offre il calcolo per i dati, consentendo di R per l'esecuzione nello stesso computer del database. Include il servizio Launchpad, che viene eseguito all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elaborare e comunica in modo sicuro con il runtime R o Python.

Utilizza servizi di SQL Server Machine Learning, è possibile eseguire il training di modelli, generare grafici, eseguire l'assegnazione dei punteggi e spostare in modo sicuro i dati tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e R o Python.

Data Scientist che si occupano di test e sviluppo di soluzioni possono inviare script da un computer di sviluppo remoto ed eseguire il codice sul server senza lo spostamento dei dati. Gli sviluppatori possono distribuire soluzioni completate a SQL Server per l'incorporamento di codice di machine learning in stored procedure SQL.

Quando si installa l'apprendimento di SQL Server, si otterrà una distribuzione di linguaggio Python o R open source, nonché le librerie di R e Python scalabile fornite da Microsoft. Il motore di database di SQL Server include anche nuovi componenti progettati per rafforzare la connettività e più velocemente, assicurarsi che la protezione delle comunicazioni con i linguaggi esterni, ad esempio R o Python.

### <a name="where-to-get-it"></a>Dove scaricarla

Per iniziare, vedere le seguenti risorse:

+ [SQL Server R Services](sql-server-r-services.md)
+ [Servizi SQL Server Python](../python/sql-server-python-services.md)
+ [Esercitazioni di Machine Learning](../tutorials/machine-learning-services-tutorials.md)

> [!NOTE]
> Supporto per Python viene fornito solo in SQL Server 2017. 

## <a name="machine-learning-server-standalone-and-microsoft-r-server-standalone"></a>Machine Learning Server (Standalone) e Microsoft R Server (Standalone)

Questo sistema server autonomo supporta soluzioni R scalabili e distribuite su più piattaforme e l'utilizzo di più origini dati aziendali, ad esempio Linux e HDInsight. Se non è necessario integrare con SQL Server, è possibile installare R Server per consentire un rapido sviluppo, distribuzione e rendere operativo il machine learning solutions. È inoltre possibile utilizzare i programmi di installazione di R Server per aggiornare i componenti di R associati a un'istanza di SQL Server e per ottenere la versione più recente di R.

Se si installa Microsoft Machine Learning Server tramite l'installazione di SQL Server 2017, è possibile distribuire e utilizzare le applicazioni di Python.

Per ulteriori informazioni, vedere [Microsoft Machine Learning Server](https://docs.microsoft.com/r-server/index).

## <a name="related-technologies"></a>Tecnologie correlate

Microsoft offre un ampio supporto per ecosistemi di machine learning, inclusi gli strumenti, provider, pacchetti R e Python avanzati, per lo sviluppo cloud e piattaforma di servizi e un ambiente di sviluppo integrato.

### <a name="r-tools-for-visual-studio"></a>R Tools for Visual Studio

Visual Studio offre un ambiente di sviluppo completo per il linguaggio R. Il plug-in include un editor, una finestra interattiva, funzionalità per i grafici, un debugger e così via. È possibile usare i linguaggi .NET da R o richiamare R da .NET tramite librerie open source, come R.NET e rClr.

Visual Studio è inoltre un ambiente di sviluppo Python eccellente. Non è più facile lavorare con i linguaggi di machine learning pur continuando a sfruttare l'accesso agli strumenti di sviluppo di database SQL.

Per altre informazioni, vedere:

+ [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)
+ [Python - Visual Studio](https://www.visualstudio.com/vs/python/)

### <a name="azure-machine-learning"></a>Azure Machine Learning

Quando si crea la propria area di lavoro in Azure Machine Learning Studio, puoi accedere a oltre 400 pacchetti R precaricati. È anche possibile scegliere quando si crea un esperimento che usi R, per la distribuzione di R usando una distribuzione standard di CRAN R, o Microsoft R Open. È anche possibile creare pacchetti R personalizzati e caricarli in Azure per l'esecuzione come moduli personalizzati.

Molti degli algoritmi disponibili in Azure Machine Learning sono ora inclusi in Microsoft Machine Learning Services, come parte del pacchetto MicrosoftML. Per ulteriori informazioni, vedere [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package).

Azure Machine Learning è un'altra piattaforma ideale per esperto di dati e gli sviluppatori che devono compilare, eseguire il training e distribuire i modelli di utilizzo dei servizi Web. È possibile pubblicare soluzioni per la [Marketplace per Machine Learning](http://datamarket.azure.com/browse/data?category=machine-learning).

Per ulteriori informazioni sulle modifiche interessanti nel servizio di Azure Machine Learning, per supportare gli esperti di dati professional, vedere queste risorse:

+ [Che cos'è Azure Machine Learning?](https://docs.microsoft.com/azure/machine-learning/preview/overview-what-is-azure-ml)
+ [Funzionalità di gestione dei modelli](https://docs.microsoft.com/azure/machine-learning/preview/model-management-overview)

### <a name="data-science-virtual-machines"></a>Macchine virtuali per l'analisi scientifica dei dati

È possibile distribuire una versione preinstallata e preconfigurata di [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] in Microsoft Azure, per avviare subito e in modo semplice le attività di esplorazione e modellazione dei dati nel cloud, senza dover configurare un sistema completo in locale.

Azure Marketplace contiene diverse macchine virtuali che supportano l'analisi scientifica dei dati.

+ Il **macchina virtuale di Microsoft Data Science** viene configurato con Machine Learning Server, come nonché Python (distribuzione Anaconda), un server Jupyter notebook, Visual Studio Community Edition, Power BI Desktop, Azure SDK e SQL Server.

    Il nuovo [VM di analisi scientifica dei dati per Windows Server 2016](http://aka.ms/dsvm/win2016) fornisce le versioni di GPU del Framework di formazione più diffusi, ad esempio CNTK. Strumenti di pre-installati includono i driver GPU NVIDIA CUDA Toolkit 8.0 e la libreria cuDNN NVIDIA per carichi di lavoro GPU. In pochi minuti, è possibile disporre di un ambiente completo per la compilazione di modelli di apprendimento completa eseguibili di CPU o della CPU e GPU.

+ Per R Server o Machine Learning, è consigliabile il Server 2017 di Microsoft Machine Learning per Linux o Windows Server 2016.

+ Per ottenere un'immagine di Azure con machine learning di SQL Server, è consigliabile una delle offerte di macchina virtuale che includono **SQL Server 2017**. Quando si seleziona l'immagine, seguire le indicazioni aggiuntive sul livello di servizio e livello, per garantire che la macchina virtuale può supportare i carichi di lavoro di machine learning.

## <a name="next-steps"></a>Passaggi successivi

[Introduzione a servizi di Machine Learning](getting-started-with-sql-server-r-services.md)

[Introduzione a Machine Learning Server](getting-started-with-microsoft-r-server-standalone.md)

[Installare il motore di database di SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)
