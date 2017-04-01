---
title: "Eliminare un modello di data mining da una struttura di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strutture di data mining [Analysis Services], modelli di data mining"
  - "eliminazione di modelli di data mining"
  - "rimozione di modelli di data mining"
  - "modelli di data mining [Analysis Services], eliminazione"
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 29
---
# Eliminare un modello di data mining da una struttura di data mining
  È possibile eliminare i modelli di data mining usando Progettazione modelli di data mining, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o istruzioni DMX.  
  
### Eliminare un modello di data mining utilizzando SQL Server Data Tools  
  
1.  Selezionare la scheda **Modelli di data mining** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sul modello da eliminare e quindi scegliere **Elimina**.  
  
     Verrà visualizzata la finestra di dialogo **Elimina oggetti**.  
  
3.  Scegliere **OK**.  
  
### Eliminare un modello di data mining utilizzando SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aprire il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenente il modello.  
  
2.  Espandere **Strutture di data mining** e quindi espandere **Modelli di data mining**.  
  
3.  Fare clic con il pulsante destro del mouse sul modello che si vuole eliminare e scegliere **Elimina**.  
  
     L'eliminazione del modello non comporta l'eliminazione dei dati di training, ma solo dei metadati e degli schemi creati durante il training del modello.  
  
### Eliminare un modello di data mining tramite DMX  
  
-   [DROP MINING MODEL &#40;DMX&#41;](../../dmx/drop-mining-model-dmx.md)  
  
## Vedere anche  
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  