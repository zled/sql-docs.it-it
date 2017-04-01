---
title: "Abilitare il drill-through per un modello di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data mining [Analysis Services], procedure"
  - "drill-through [Analysis Services]"
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 28
---
# Abilitare il drill-through per un modello di data mining
  Se è stato abilitato il drill-through per un modello di data mining, quando si esplora il modello è possibile recuperare informazioni dettagliate sui case utilizzati per creare il modello. Per visualizzare queste informazioni sono necessarie le autorizzazioni adeguate e la struttura deve essere stata già elaborata.  
  
 **Autorizzazioni** Affinché possa effettuare il drill-through ai dati del modello o della struttura, l'utente deve essere membro di un ruolo che disponga di autorizzazioni [AllowDrillThrough](../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) sul modello o sulla struttura di data mining. Le autorizzazioni di drill-through vengono impostate separatamente per la struttura e per il modello.  
  
-   Le autorizzazioni drill-through sul modello consentono di eseguire il drill-through dal modello, anche se non si dispone di autorizzazioni sulla struttura.  
  
-   Le autorizzazioni di drill-through per la struttura consentono di includere colonne della struttura nelle query di drill-through dal modello tramite la funzione [StructureColumn &#40;DMX&#41;](../../dmx/structurecolumn-dmx.md). È anche possibile eseguire query sui test case e sui case di training nella struttura usando la sintassi SELECT… FROM \<struttura>.CASES.  
  
 **Memorizzazione nella cache di case di training** Il drill-through avviene mediante il recupero di informazioni sui case di training nella struttura di data mining. Queste informazioni vengono memorizzate nella cache quando la struttura viene elaborata. Pertanto, se si sceglie di cancellare tutti i dati memorizzati nella cache impostando la proprietà <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> su **ClearAfterProcessing**, il drill-through non funzionerà.  
  
> [!NOTE]  
>  Se i case di training non sono stati memorizzati nella cache, è necessario impostare la proprietà <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> su **KeepTrainingCases** e rielaborare quindi il modello prima che sia possibile visualizzare i dati dei case.  
  
 Per altre informazioni, vedere [Query drill-through &#40;Data mining&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
### Per abilitare il drill-through su un modello di data mining  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], nella scheda **Modelli di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sul nome del modello di data mining in cui si vuole abilitare il drill-through e quindi scegliere **Proprietà**.  
  
2.  Nelle finestre **Proprietà** fare clic su **AllowDrillthrough**e selezionare **True**.  
  
3.  Nella scheda **Modelli di data mining** fare clic con il pulsante destro del mouse sul modello e scegliere **Elabora modello**.  
  
### Per attivare la memorizzazione nella cache per una struttura di data mining  
  
1.  Nella scheda **Struttura di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], fare clic con il pulsante destro del mouse sul nome della struttura di data mining.  
  
2.  Aprire la finestra **Proprietà** .  
  
3.  Nella finestra **Proprietà** individuare la proprietà **CacheMode** e selezionare **KeepTrainingCases** nell'elenco.  
  
4.  Selezionare **Elabora** dal menu **Database**.  
  
## Vedere anche  
 [Query drill-through &#40;Data mining&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
  