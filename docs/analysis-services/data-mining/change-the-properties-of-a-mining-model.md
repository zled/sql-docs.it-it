---
title: "Modificare le propriet&#224; di un modello di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli di data mining [Analysis Services], proprietà"
  - "proprietà [data mining]"
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 38
---
# Modificare le propriet&#224; di un modello di data mining
  Alcune proprietà dei modelli di data mining si applicano all'intero modello, altre solo a singole colonne. Esempi di proprietà che si applicano all'intero modello sono la proprietà **Drillthrough**, che specifica se i dati del case devono essere disponibili per le query, e la proprietà **Description**. Le proprietà che si applicano alle singole colonne sono **Usage** e **ModelingFlags**, che controllano il modo in cui i dati della colonna vengono usati all'interno del modello.  
  
 Le proprietà del modello seguenti sono associate a editor avanzati che è possibile utilizzare per creare espressioni o configurare proprietà più complesse. Di seguito sono elencate queste proprietà.  
  
-   Proprietà **Filter**: consente di aprire la [finestra di dialogo Filtro dei set di dati o Filtro modello](../Topic/Data%20Set%20Filter%20or%20Model%20Filter%20Dialog%20Box.md).  
  
-   Proprietà **AlgorithmParameters**: consente di aprire la [finestra di dialogo Parametri algoritmo &#40;visualizzazione Modelli di data mining&#41;](../Topic/Algorithm%20Parameters%20Dialog%20Box%20\(Mining%20Models%20View\).md).  
  
 Per informazioni su come impostare le proprietà in un modello di data mining, vedere [Colonne del modello di data mining](../../analysis-services/data-mining/mining-model-columns.md).  
  
### Per modificare le proprietà di un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sull'intestazione di colonna che contiene il nome del modello di data mining o sulla riga della griglia che contiene il nome dell'algoritmo di data mining e quindi scegliere **Proprietà**.  
  
2.  Nella finestra **Proprietà** a destra dello schermo evidenziare il valore corrispondente alla proprietà da modificare e quindi immettere il nuovo valore.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
### Per modificare le proprietà di un modello di data mining  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sulla cella della griglia in corrispondenza dell'intersezione tra la colonna della struttura di data mining e il modello di data mining e quindi scegliere **Proprietà**.  
  
2.  Nella finestra **Proprietà** a destra dello schermo evidenziare il valore corrispondente alla proprietà da modificare e quindi immettere il nuovo valore.  
  
    > [!NOTE]  
    >  Se l'uso della colonna è impostato su **Ignore**, la finestra **Proprietà** per la colonna è vuota.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
## Vedere anche  
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  