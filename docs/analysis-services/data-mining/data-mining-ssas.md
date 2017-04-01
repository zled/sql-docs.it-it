---
title: "Data mining (SSAS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data mining [Analysis Services], informazioni sul data mining"
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
caps.latest.revision: 31
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 31
---
# Data mining (SSAS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è un avanzato sistema per le analisi predittive fin dalla versione 2000 e offre funzionalità di data mining in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La combinazione di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e Data Mining di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce una piattaforma integrata per le analisi predittive che comprende la pulizia e la preparazione dei dati, il Machine Learning e la creazione di report. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Il data mining include più algoritmi standard, inclusi modelli di clustering EM e K-medie, reti neurali, regressione logistica e regressione lineare, alberi delle decisioni e classificatori Naive Bayes. Tutti i modelli dispongono di visualizzazioni integrate che consentono di sviluppare, ridefinire e valutare i modelli.  L'integrazione del data mining nella soluzione di business intelligence consente di prendere decisioni intelligenti sui problemi complessi.  
  
## Vantaggi del data mining  
 Il data mining (anche denominato analisi predittiva e Machine Learning) usa consolidati principi statistici per individuare modelli nei dati. Applicando gli algoritmi di data mining di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ai dati, è possibile prevedere tendenze, identificare modelli, creare regole e indicazioni, analizzare la sequenza di eventi in set di dati complessi e acquisire nuovi approfondimenti.  
  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] il data mining è efficace, accessibile e integrato con gli strumenti preferiti dagli utenti per l'analisi e la creazione di report.  
  
## Caratteristiche principali del data mining  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In Data Mining di SQL Server sono disponibili le caratteristiche seguenti per il supporto di soluzioni di data mining integrate:  
  
-   Più origini dati: è possibile usare qualsiasi origine dati tabulare per il data mining, inclusi file di testo e fogli di calcolo. È anche possibile eseguire il processo di data mining di cubi OLAP creati in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tuttavia, non è possibile usare i dati di un database in memoria.  
  
-   Pulizia dati integrata, gestione dati e generazione di report: in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono disponibili strumenti avanzati per il profiling e la pulizia dei dati. È possibile creare processi ETL per la pulizia dei dati in preparazione per la modellazione e ssISnoversion facilita la ripetizione del training e l'aggiornamento dei modelli.  
  
-   Più algoritmi personalizzabili: oltre a fornire algoritmi quali quelli di clustering, reti neurali e alberi delle decisioni, Data Mining di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta lo sviluppo di algoritmi plug-in personalizzati.  
  
-   Infrastruttura di test del modello: testare i modelli e i set di dati utilizzando importanti strumenti statistici come la convalida incrociata, le matrici di classificazione, i grafici di accuratezza e a dispersione. Creare e gestire facilmente i set di testing e di training.  
  
-   Esecuzione di query e drill-through: Data Mining di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce il linguaggio DMX per l'integrazione delle query di stima nelle applicazioni. È anche possibile recuperare statistiche dettagliate e schemi dai modelli ed eseguire il drill-through nei dati del case.  
  
-   Strumenti client: oltre agli strumenti di sviluppo e progettazione forniti da SQL Server, è possibile utilizzare i componenti aggiuntivi Data mining per Excel per creare ed esplorare i modelli, nonché per eseguirvi query. In alternativa creare client personalizzati, inclusi i servizi Web.  
  
-   Supporto del linguaggio di scripting e API gestita: tutti gli oggetti di data mining sono completamente programmabili. La generazione di script è possibile tramite MDX, XMLA o le estensioni PowerShell per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Utilizzare il linguaggio DMX (Data Mining Extensions) per eseguire query e generare script velocemente.  
  
-   Sicurezza e distribuzione: tramite [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene fornita la sicurezza basata su ruoli, incluse autorizzazioni separate relative al drill-through per i dati del modello e della struttura. Distribuzione semplice di modelli agli altri server, in modo che gli utenti possano accedere agli schemi o effettuare stime  
  
## Argomenti della sezione  
 Negli argomenti di questa sezione sono illustrate le caratteristiche principali di Data mining di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e le attività correlate.  
  
-   [Concetti di data mining](../../analysis-services/data-mining/data-mining-concepts.md)  
  
-   [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [Strutture di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
-   [Modelli di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
-   [Test e convalida &#40;Data mining&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)  
  
-   [Query di data mining](../../analysis-services/data-mining/data-mining-queries.md)  
  
-   [Soluzioni di data mining](../../analysis-services/data-mining/data-mining-solutions.md)  
  
-   [Strumenti di data mining](../../analysis-services/data-mining/data-mining-tools.md)  
  
-   [Architettura di data mining](../../analysis-services/data-mining/data-mining-architecture.md)  
  
-   [Panoramica della sicurezza &#40;data mining&#41;](../../analysis-services/data-mining/security-overview-data-mining.md)  
  
## Vedere anche  
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  