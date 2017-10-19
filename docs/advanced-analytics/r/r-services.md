---
title: Microsoft Machine Learning Services | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 10/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
caps.latest.revision: 23
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 246ea9f306c7d99b835c933c9feec695850a861b
ms.openlocfilehash: ddc9b3f17afe1f9d4c811e4a5871f48a3a08de7f
ms.contentlocale: it-it
ms.lasthandoff: 10/13/2017

---
# <a name="microsoft-machine-learning-services"></a>Servizi Microsoft Machine Learning

L'obiettivo di Microsoft Machine Learning Services è fornire una piattaforma estendibile e scalabile per l'integrazione di strumenti e attività di machine learning con le applicazioni che utilizzano i servizi di machine learning. La piattaforma deve soddisfare le esigenze di tutti gli utenti coinvolti nel processo analitica e lo sviluppo di dati da esperti di dati, agli architetti e agli amministratori di database.

Vantaggi principali includono:

+ Analitica scalabile
+ Più piattaforme e i contesti di calcolo, per le soluzioni "scrivere una sola volta, distribuire remoto via Internet"
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
+ **Server di Microsoft Machine Learning** supporta le distribuzioni di R e Python in Windows Server con espansione ad altre piattaforme supportate pianificata 2017 ad associazione tardiva.

### <a name="benefits"></a>Vantaggi

Servizi di Microsoft Machine Learning offre il calcolo per i dati, consentendo di R per l'esecuzione nello stesso computer del database. Include il servizio Launchpad attendibile, che viene eseguito all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elaborare e comunica in modo sicuro con il runtime R o Python.

Utilizza servizi di SQL Server Machine Learning, è possibile eseguire il training di modelli, generare grafici, eseguire l'assegnazione dei punteggi e spostare facilmente i dati tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e R o Python.

Data Scientist che si occupano di test e sviluppo di soluzioni è possibile inviare gli script da un computer di sviluppo remoto per eseguire il codice in modo sicuro nel server, oppure è possibile distribuire soluzioni completate a SQL Server per l'incorporamento di codice di machine learning in stored procedure SQL.

Quando si installa l'apprendimento di SQL Server, si otterrà una distribuzione di linguaggio Python o R open source, nonché le librerie di R e Python scalabile fornite da Microsoft. Il motore di database di SQL Server include anche nuovi componenti progettati per rafforzare la connettività e più velocemente, assicurarsi che la protezione delle comunicazioni con i linguaggi esterni, ad esempio R o Python.

### <a name="where-to-get-it"></a>Dove scaricarla

Per iniziare, vedere le seguenti risorse:

+ [SQL Server R Services](sql-server-r-services.md)
+ [Servizi SQL Server Python](../python/sql-server-python-services.md)
+ [Esercitazioni di Machine Learning](../tutorials/machine-learning-services-tutorials.md)

> [!NOTE]
> Supporto per Python viene fornito solo in SQL Server 2017. 

## <a name="machine-learning-server-standalone-and-microsoft-r-server-standalone"></a>Machine Learning Server (Standalone) e Microsoft R Server (Standalone)

Questo sistema server autonomo supporta soluzioni R scalabili e distribuite su più piattaforme e l'utilizzo di più origini dati aziendali, ad esempio Linux e HD Insight. Se non è necessario integrare con SQL Server, è possibile installare R Server per consentire un rapido sviluppo, distribuzione e rendere operativo il machine learning solutions. È inoltre possibile utilizzare i programmi di installazione di R Server per aggiornare i componenti di R associati a un'istanza di SQL Server e per ottenere la versione più recente di R.

Se si installa Microsoft Machine Learning Server tramite l'installazione di SQL Server 2017, è possibile distribuire e utilizzare le applicazioni di Python.

Per ulteriori informazioni, vedere [Microsoft Machine Learning Server](https://docs.microsoft.com/r-server/index).

## <a name="related-technologies"></a>Tecnologie correlate

Microsoft offre un ampio supporto per ecosistemi di machine learning, inclusi gli strumenti, provider, pacchetti R e Python avanzati, per lo sviluppo cloud e piattaforma di servizi e un ambiente di sviluppo integrato.

### <a name="r-tools-for-visual-studio"></a>R Tools for Visual Studio

Visual Studio offre un ambiente di sviluppo completo per il linguaggio R. Il plug-in include un editor, una finestra interattiva, funzionalità per i grafici, un debugger e così via. È possibile usare i linguaggi .NET da R o richiamare R da .NET tramite librerie open source, come R.NET e rClr.

Visual Studio è inoltre un ambiente di sviluppo Python eccellente. Non è più facile lavorare con i linguaggi di machine learning pur continuando a sfruttare l'accesso agli strumenti di sviluppo di database SQL.

Per altre informazioni, vedere:

+ [Strumenti R per Visual Studio](https://www.visualstudio.com/vs/rtvs/)
+ [Python - Visual Studio](https://www.visualstudio.com/vs/python/)

### <a name="azure-machine-learning"></a>Azure Machine Learning

Quando si crea la propria area di lavoro in Azure Machine Learning Studio, sarà possibile accedere a oltre 400 pacchetti R precaricati. È anche possibile scegliere quando si crea un esperimento che usi R, per la distribuzione di R usando una distribuzione standard di CRAN R, o Microsoft R Open. È anche possibile creare pacchetti R personalizzati e caricarli in Azure per l'esecuzione come moduli personalizzati.

Per altre informazioni, vedere le risorse seguenti:

+ [Estendere l'esperimento con R](https://docs.microsoft.com/azure/machine-learning/machine-learning-extend-your-experiment-with-r)
+ [Creare moduli R personalizzati in Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/machine-learning-custom-r-modules)

Molti degli algoritmi disponibili in Azure Machine Learning sono ora inclusi in Microsoft Machine Learning Services, come parte del pacchetto MicrosoftML. Per ulteriori informazioni, vedere [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package).

Azure Machine Learning è un'altra piattaforma ideale per esperto di dati e gli sviluppatori che devono compilare, eseguire il training e distribuire i modelli di utilizzo dei servizi Web. È possibile pubblicare soluzioni per la [Marketplace per Machine Learning](http://datamarket.azure.com/browse/data?category=machine-learning).

### <a name="data-science-virtual-machines"></a>Macchine virtuali per l'analisi scientifica dei dati

È possibile distribuire una versione preinstallata e preconfigurata di [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] in Microsoft Azure, per avviare subito e in modo semplice le attività di esplorazione e modellazione dei dati nel cloud, senza dover configurare un sistema completo in locale.

Azure Marketplace contiene diverse macchine virtuali che supportano l'analisi scientifica dei dati:

+ La **macchina virtuale Microsoft per l'analisi scientifica dei dati** è configurata con Microsoft R Server e Python (distribuzione Anaconda), un server Jupyter Notebook, Visual Studio Community Edition, Power BI Desktop, Azure SDK e SQL Server Express.

+ **Microsoft R Server 2016 per Linux** contiene la versione più recente di R Server (versione 9.0.1). Macchine virtuali separate sono disponibili per CentOS versione 7.2 e Ubuntu versione 16.04.

+ Il **R Server solo SQL Server 2016 Enterprise Edition** macchina virtuale include un programma di installazione autonomo per il Server di R 9.0.1 che supporta il nuovo modello di licenza del ciclo di vita di Software più recenti.

> [!TIP]
> Il nuovo [VM di analisi scientifica dei dati per Windows Server 2016](http://aka.ms/dsvm/win2016) fornisce le versioni di GPU del Framework di formazione più diffusi, ad esempio CNTK. Strumenti di pre-installati includono i driver GPU NVIDIA CUDA Toolkit 8.0 e la libreria cuDNN NVIDIA per carichi di lavoro GPU. In pochi minuti, è possibile disporre di un ambiente completo per la compilazione di modelli di apprendimento completa eseguibili di CPU o della CPU e GPU.

## <a name="next-steps"></a>Passaggi successivi

[Introduzione a servizi di Machine Learning](getting-started-with-sql-server-r-services.md)

[Introduzione a Machine Learning Server](getting-started-with-microsoft-r-server-standalone.md)

[Installare il motore di database di SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)

