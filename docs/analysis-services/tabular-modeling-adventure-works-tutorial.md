---
title: "Modellazione tabulare (esercitazione di AdventureWorks) | Microsoft Docs"
ms.custom: ""
ms.date: "03/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
keywords: 
  - "Analysis Services"
  - "Modello tabulare"
  - "Esercitazione"
  - "SSAS"
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
caps.latest.revision: 40
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 35
---
# Modellazione tabulare (esercitazione di AdventureWorks)
In questa esercitazione sono incluse lezioni sulla creazione di un [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]modello tabulare di Analysis Services tramite [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
  
## Lezioni dell'esercitazione  
Durante questa esercitazione verranno appresi i concetti seguenti:  
  
-   Modalità di creazione di un nuovo progetto di modello tabulare in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
-   Modalità di importazione dei dati da un database relazionale di SQL Server a un progetto di modello tabulare.  
  
-   Modalità di creazione e gestione delle relazioni tra tabelle nel modello.  
  
-   Modalità di creazione e gestione di calcoli, misure e indicatori di prestazioni chiave per l'analisi dei dati del modello.  
  
-   Modalità di creazione e gestione di prospettive e gerarchie che semplificano l'esplorazione dei dati del modello fornendo punti di vista specifici dell'applicazione e dell'azienda.  
  
-   Modalità di creazione di partizioni che consentono di dividere i dati della tabella in parti logiche più piccole che possono essere elaborate indipendentemente dalle altre partizioni.  
  
-   Modalità di protezione degli oggetti e dei dati del modello tramite la creazione di ruoli con membri utente.  
  
-   Modalità di distribuzione di un modello tabulare in un'istanza di produzione o sandbox di Analysis Services in esecuzione in modalità tabulare.  
  
## Scenario  
Questa esercitazione si riferisce alla società fittizia [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] è una multinazionale che produce e commercializza biciclette in acciaio e in materiali compositi sui mercati dell'America del Nord, dell'Europa e dell'Asia. La sede centrale di [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] si trova a Bothell, nello stato di Washington, e vi lavorano 500 dipendenti. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] dispone inoltre di numerosi team di vendita dislocati nelle diverse aree di mercato.  
  
Per offrire un supporto migliore per le esigenze di analisi dei dati di team di vendita e marketing e dei responsabili, si desidera creare un modello tabulare che consenta agli utenti di analizzare i dati relativi alle vendite Internet nel database di esempio AdventureWorksDW.  
  
Per completare l'esercitazione e il modello tabulare relativo alle vendite Internet di Adventure Works, è necessario completare diverse lezioni. Ogni lezione include diverse attività. Per completare la lezione è necessario completare ogni attività. Sebbene in una lezione specifica potrebbero essere presenti diverse attività che portano a un risultato simile, la modalità di completamento di ogni attività è leggermente diversa. L'obiettivo è quello di mostrare come spesso vi sia più di un modo per completare una determinata attività e di incentivare l'utilizzo di nozioni apprese nelle attività precedenti.  
  
Lo scopo delle lezioni è quello di assistere l'utente nella creazione di un modello tabulare di base in esecuzione nella modalità In-Memory utilizzando numerose funzionalità incluse in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Poiché ogni lezione è basata su quella precedente, è necessario completare le lezioni in ordine. Dopo aver completato tutte le lezioni, sarà stato creato e distribuito il modello tabulare di esempio di Adventure Works relativo alle vendite Internet in un server Analysis Services.  
  
Questa esercitazione non fornisce lezioni o informazioni sulla gestione di un database di modello tabulare distribuito tramite SQL Server Management Studio o sull'utilizzo di un'applicazione client di creazione di report per la connessione a un modello distribuito per l'esplorazione dei dati del modello.  
  
## Prerequisiti  
Per completare l'esercitazione, è necessario che siano installati i prerequisiti seguenti:  
  
-   [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Istanza di Analysis Services in esecuzione nella modalità tabulare.  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. [Ottenere l'ultima versione.](https://msdn.microsoft.com/library/mt204009.aspx)  
  
-   Database di esempio Adventure Works DW 2014. Questo database di esempio include i dati necessari per completare questa esercitazione. Per scaricare il database di esempio, accedere alla pagina [http://go.microsoft.com/fwlink/?LinkID=335807](http://go.microsoft.com/fwlink/?LinkID=335807).  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 2003 o versione successiva, per poter usare la funzionalità di analisi in Excel illustrata nella lezione 11.  
  
## Lezioni  
L'esercitazione include le lezioni seguenti:  
  
|Lezione|Tempo stimato per il completamento|  
|----------|------------------------------|  
|[Lezione 1: Creare un nuovo modello di progetto tabulare](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)|10 minuti|  
|[Lezione 2: Aggiungere dati](../analysis-services/lesson-2-add-data.md)|20 minuti|  
|[Lezione 3: Rinominare colonne](../analysis-services/lesson-3-rename-columns.md)|20 minuti|  
|[Lezione 4: Contrassegna come tabella data](../analysis-services/lesson-4-mark-as-date-table.md)|3 minuti|  
|[Lezione 5: Creare relazioni](../analysis-services/lesson-5-create-relationships.md)|10 minuti|  
|[Lezione 6: Creare colonne calcolate](../analysis-services/lesson-6-create-calculated-columns.md)|15 minuti|  
|[Lezione 7: Creare misure](../analysis-services/lesson-7-create-measures.md)|30 minuti|  
|[Lezione 8: Creare indicatori di prestazioni chiave](../analysis-services/lesson-8-create-key-performance-indicators.md)|15 minuti|  
|[Lezione 9: Creare prospettive](../Topic/Lesson%209:%20Create%20Perspectives.md)|5 minuti|  
|[Lezione 10: Creare gerarchie](../analysis-services/lesson-10-create-hierarchies.md)|20 minuti|  
|[Lezione 11: Creare partizioni](../analysis-services/lesson-11-create-partitions.md)|15 minuti|  
|[Lezione 12: Creare ruoli](../analysis-services/lesson-12-create-roles.md)|15 minuti|  
|[Lezione 13: Analizza in Excel](../analysis-services/lesson-13-analyze-in-excel.md)|20 minuti|  
|[Lezione 14: Distribuire](../analysis-services/lesson-14-deploy.md)|5 minuti|  
  
## Lezioni supplementari  
In questa esercitazione sono incluse [Lezioni supplementari](../Topic/Supplemental%20Lessons.md). Gli argomenti di questa sezione non sono necessari per completare l'esercitazione, ma possono risultare utili per comprendere meglio le funzionalità avanzate di creazione dei modelli tabulari.  
  
|Lezione|Tempo stimato per il completamento|  
|----------|------------------------------|  
|[Implementare la sicurezza dinamica mediante i filtri di riga](../analysis-services/implement-dynamic-security-by-using-row-filters.md)|30 minuti|  
|[Configurare le proprietà di creazione di report per i report Power View](../analysis-services/configure-reporting-properties-for-power-view-reports.md)|30 minuti|  
  
## Passaggio successivo  
Per iniziare l'esercitazione, passare alla prima lezione: [Lezione 1: Creare un nuovo modello di progetto tabulare](../analysis-services/lesson-1-create-a-new-tabular-model-project.md).  
  
  
  
