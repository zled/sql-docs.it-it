---
title: "R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/20/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 20
---
# R Services
  Microsoft R Services offre due piattaforme server per l'integrazione del noto linguaggio R open source con le applicazioni aziendali: **SQL Server R Services (In-Database)**, per l'integrazione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], e **Microsoft R Server**.  
  
-   **R Services (In-Database)**  
  
     L'obiettivo di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è consentire lo sviluppo, la distribuzione e la messa in funzione rapidi delle soluzioni R basate sulla piattaforma [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e dei servizi correlati.  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] introduce le funzionalità di calcolo nei dati consentendo l'esecuzione di R nello stesso computer del database. Include un servizio di database che viene eseguito all'esterno del processo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e comunica in modo sicuro con il runtime di R. È possibile eseguire il training di modelli R, generare grafici R, eseguire l'assegnazione dei punteggi e spostare con facilità i dati tra R e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I data scientist che si occupano di test e sviluppo di soluzioni possono comunicare con il server da un computer di sviluppo remoto per eseguire codice R nel server e distribuire le soluzioni completate in SQL Server incorporando le chiamate a R nelle stored procedure.  
  
     Questo download include una distribuzione del linguaggio R open source e ScaleR, un set di pacchetti R scalabili ad alte prestazioni. Include anche provider per semplificare e velocizzare la connettività con tutte le tecnologie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Per altre informazioni, vedere [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md). Per gli scenari di esempio, vedere [Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md).  
  
-   **Microsoft R Server**  
  
     Questo sistema server autonomo supporta soluzioni R scalabili e distribuite su più piattaforme e l'uso di più origini dati aziendali, tra cui Linux, Hadoop e Teradata.  
  
     Per altre informazioni, vedere [Microsoft R Server (MSDN)](https://msdn.microsoft.com/microsoft-r/index).  
  
## <a name="related-technologies"></a>Tecnologie correlate  
 Microsoft offre un ampio supporto per l'ecosistema del linguaggio R open source, inclusi strumenti, provider, pacchetti R avanzati e ambienti di sviluppo integrato.  
  
-   **R Tools for Visual Studio**  
  
     Visual Studio offre un ambiente di sviluppo completo per il linguaggio R. Il plug-in include un editor, una finestra interattiva, funzionalità per i grafici, un debugger e così via. È possibile usare i linguaggi .NET da R o richiamare R da .NET tramite librerie open source, come R.NET e rClr.  
  
     Per altre informazioni, vedere [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/).  
  
-   **R in Azure Machine Learning**  
  
     Creare un'area di lavoro personale in Azure Machine Learning Studio, in cui è possibile accedere a oltre 400 pacchetti R precaricati. Compilare ed eseguire il training di modelli per la distribuzione come servizio Web o scrivere script personalizzati per la trasformazione dei dati. Creare pacchetti R personalizzati e caricarli in Azure per l'esecuzione come moduli personalizzati e pubblicare soluzioni in [Marketplace per Machine Learning](http://datamarket.azure.com/browse/data?category=machine-learning).  
  
     Per altre informazioni, vedere [Estendere l'esperimento con R](https://docs.microsoft.com/azure/machine-learning/machine-learning-extend-your-experiment-with-r) e [Creare moduli R personalizzati in Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/machine-learning-custom-r-modules).  
  
-   **Macchine virtuali per l'analisi scientifica dei dati**  
  
     È possibile distribuire una versione preinstallata e preconfigurata di [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] in Microsoft Azure, per avviare subito e in modo semplice le attività di esplorazione e modellazione dei dati nel cloud, senza dover configurare un sistema completo in locale.  
  
     Azure Marketplace contiene diverse macchine virtuali che supportano l'analisi scientifica dei dati:
     + La **macchina virtuale Microsoft per l'analisi scientifica dei dati** è configurata con Microsoft R Server e Python (distribuzione Anaconda), un server Jupyter Notebook, Visual Studio Community Edition, Power BI Desktop, Azure SDK e SQL Server Express. 
     + **Microsoft R Server 2016 per Linux** contiene la versione più recente di R Server (versione 9.0.1). Macchine virtuali separate sono disponibili per CentOS versione 7.2 e Ubuntu versione 16.04. 
     + La macchina virtuale **R Server Only SQL Server 2016 Enterprise** include un programma di installazione autonomo per R Server 9.0.1 che supporta il nuovo modello di licenza basato sui criteri relativi al ciclo di vita moderni.
 

## <a name="see-also"></a>Vedere anche  
[Introduzione a SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md) 

[Introduzione a Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  

 [Installare il motore di database di SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)  
  
  