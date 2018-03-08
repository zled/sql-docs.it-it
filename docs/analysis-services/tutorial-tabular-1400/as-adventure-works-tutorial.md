---
title: Esercitazioni su Analysis Services di Adventure Works (1400) | Documenti Microsoft
description: Vengono presentati nell'esercitazione di Adventure Works per Analysis Services
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: 8a7511c096ffacf249187c9f45d71bca340bb1ca
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="tabular-modeling-1400-compatibility-level"></a>Modellazione tabulare (livello di compatibilità 1400)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Questa esercitazione sono incluse lezioni su come creare e distribuire un modello tabulare con la [il livello di compatibilità 1400](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md). Se si ha familiarità con Analysis Services e la modellazione tabulare, completato questa esercitazione è il modo più rapido per informazioni su come creare e distribuire un modello tabulare di base tramite Visual Studio. Dopo avere i prerequisiti sul posto, sono necessarie due a tre ore per completare.  
  
## <a name="what-you-learn"></a>Informazioni   
  
-   Come creare un nuovo progetto di modello tabulare nel **il livello di compatibilità 1400** in Visual Studio con SSDT.
  
-   Come importare dati da un database relazionale in un database dell'area di lavoro progetto di modello tabulare.  
  
-   Modalità di creazione e gestione delle relazioni tra tabelle nel modello.  
  
-   Come creare colonne calcolate, misure e indicatori di prestazioni chiave che consentono agli utenti di analizzare le metriche aziendali critici.  
  
-   Come creare e gestire prospettive e gerarchie che semplificano l'esplorazione dei dati del modello fornendo punti di vista specifici dell'applicazione e di business.  
  
-   Modalità di creazione di partizioni che consentono di dividere i dati della tabella in parti logiche più piccole che possono essere elaborate indipendentemente dalle altre partizioni.  
  
-   Modalità di protezione degli oggetti e dei dati del modello tramite la creazione di ruoli con membri utente.  
  
-   Come distribuire un modello tabulare per un **Azure Analysis Services** server o **2017 Analysis Services di SQL Server** server mediante SSDT.  
  
## <a name="prerequisites"></a>Prerequisiti  

Per completare questa esercitazione, è necessario:  
  
-   Un server Azure Analysis Services o un server di SQL Server 2017 Analysis Services in modalità tabulare. Iscriversi per una liberazione [versione di valutazione di Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/) e [creare un server](https://docs.microsoft.com/azure/analysis-services/analysis-services-create-server) o il download gratuito [2017 Developer Edition di SQL Server](https://www.microsoft.com/sql-server/sql-server-downloads).

-   Un [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/create-data-warehouse-portal) con il **database di esempio AdventureWorksDW**, o un Data Warehouse di on-premise SQL Server con un [database di esempio AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Quando si installa un database AdventureWorksDW a un Data Warehouse di on-premise SQL Server, utilizzare la versione di datbase esempio corrispondente con la versione del server. 

    **Importante:** se si installa il database di esempio per on-premise SQL Server Data Warehouse e distribuire il modello a un server di Azure Analysis Services, un [gateway dati locale](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) è obbligatorio.

-   La versione più recente di [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx). O, se si dispone già di Visual Studio 2017, è possibile scaricare e installare [progetti di Microsoft Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) pacchetto (VSIX). Per questa esercitazione, i riferimenti a Visual Studio e SSDT sono sinonimi. 

-   La versione più recente di [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).    

-   Un'applicazione client, ad esempio [Power BI Desktop](https://powerbi.microsoft.com/desktop/) o Excel. 

## <a name="scenario"></a>Scenario  

Questa esercitazione è basata su Adventure Works Cycles, una società fittizia. Adventure Works è un'azienda manifatturiera multinazionale che produce e commercializza biciclette, parti e accessori sui mercati dell'America del Nord, Europa e Asia. È stata lavorano 500 dipendenti. Inoltre, Adventure Works utilizza diversi team delle vendite regionali di mercato. Il progetto consiste nel creare un modello tabulare agli utenti di vendita e marketing di analizzare i dati delle vendite Internet nel database AdventureWorksDW.  
  
Per completare l'esercitazione, è necessario completare diverse lezioni. In ogni lezione, vi sono attività. Completamento di ogni attività nell'ordine è necessario per completare la lezione. Mentre in una lezione specifica potrebbero essere diverse attività che eseguono un risultato simile, ma il completamento di ogni attività è leggermente diversa. Questo metodo viene illustrato come è spesso più di un modo per completare un'attività e per incentivare l'utilizzo delle conoscenze acquisite in attività e lezioni precedenti.  
  
Lo scopo delle lezioni è illustrata la creazione di un modello tabulare di base tramite molte delle funzionalità incluse in SSDT. Poiché ogni lezione è basata su quella precedente, è necessario completare le lezioni in ordine.
  
In questa esercitazione non fornisce lezioni sulla gestione di un server nel portale di Azure, la gestione di un server o un database utilizzando SQL Server Management Studio o utilizzando un'applicazione client di esplorare i dati del modello. 


## <a name="lessons"></a>Lezioni  

L'esercitazione include le lezioni seguenti:  
  
|Lezione|Tempo stimato per il completamento|  
|----------|------------------------------|  
|[1 - creare un nuovo progetto di modello tabulare](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)|10 minuti|  
|[2 - Recuperare i dati](../tutorial-tabular-1400/as-lesson-2-get-data.md)|10 minuti|  
|[3 - Contrassegnare come tabella data](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)|3 minuti|  
|[4 - Creare relazioni](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)|10 minuti|  
|[5 - Creare colonne calcolate](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)|15 minuti|
|[6 - Creare misure](../tutorial-tabular-1400/as-lesson-6-create-measures.md)|30 minuti|  
|[7 - creare indicatori di prestazioni chiave (KPI)](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)|15 minuti|  
|[8 - Creare prospettive](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)|5 minuti|  
|[9 - Creare gerarchie](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)|20 minuti|  
|[10 - Creare partizioni](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)|15 minuti|  
|[11 - Creare ruoli](../tutorial-tabular-1400/as-lesson-11-create-roles.md)|15 minuti|  
|[12 - Analizzare in Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)|5 minuti| 
|[13 - Distribuire](../tutorial-tabular-1400/as-lesson-13-deploy.md)|5 minuti|  
  
## <a name="supplemental-lessons"></a>Lezioni supplementari  

Queste lezioni non sono necessarie per completare l'esercitazione, ma possono essere utile per una migliore comprensione avanzate dei modelli tabulari le funzioni di modifica.  
  
|Lezione|Tempo stimato per il completamento|  
|----------|------------------------------|  
|[Righe di dettaglio](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)|10 minuti|
|[Sicurezza dinamica](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)|30 minuti|
|[Gerarchie incomplete](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)|20 minuti| 

  
## <a name="next-steps"></a>Passaggi successivi  

Per iniziare, vedere [lezione 1: creare un nuovo progetto di modello tabulare](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
  
  

