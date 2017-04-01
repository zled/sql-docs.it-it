---
title: "Modificare le propriet&#224; di una struttura di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strutture di data mining [Analysis Services], proprietà"
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 28
---
# Modificare le propriet&#224; di una struttura di data mining
  Sono disponibili due tipi di proprietà su una struttura di data mining, entrambi modificabili:  
  
-   Proprietà della struttura di data mining che influiscono sull'intera struttura  
  
-   Proprietà su singole colonne della struttura  
  
 Si noti che alcune proprietà dipendono da altre impostazioni di proprietà. Non è ad esempio possibile impostare le proprietà che controllano la creazione di contenitori, ad esempio <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> o <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> finché non viene impostato il tipo di dati della colonna su **Discretized**.  
  
 Per altre informazioni sulle proprietà di data mining, vedere [Colonne della struttura di data mining](../../analysis-services/data-mining/mining-structure-columns.md).  
  
### Per modificare le proprietà di una struttura di data mining  
  
1.  Nella scheda **Struttura di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sulla struttura di data mining o su una colonna della struttura e quindi scegliere **Proprietà**.  
  
     A destra dello schermo verrà visualizzata la finestra **Proprietà**, se non è già visualizzata.  
  
2.  Nella finestra **Proprietà** selezionare il valore corrispondente alla proprietà che si vuole modificare e quindi immettere il nuovo valore.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
## Vedere anche  
 [Attività e procedure relative alla struttura di data mining](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  