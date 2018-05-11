---
title: Eliminazione di un modello di Data Mining da una struttura di Data Mining | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e67e78ff0f3faf2d8a9b468dd2ecc76506c0e80
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>Eliminare un modello di data mining da una struttura di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  È possibile eliminare i modelli di data mining usando Progettazione modelli di data mining, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o istruzioni DMX.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>Eliminare un modello di data mining utilizzando SQL Server Data Tools  
  
1.  Selezionare la scheda **Modelli di data mining** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sul modello da eliminare e quindi scegliere **Elimina**.  
  
     Verrà visualizzata la finestra di dialogo **Elimina oggetti** .  
  
3.  Scegliere **OK**.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>Eliminare un modello di data mining utilizzando SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenente il modello.  
  
2.  Espandere **Strutture di data mining**e quindi espandere **Modelli di data mining**.  
  
3.  Fare clic con il pulsante destro del mouse sul modello che si vuole eliminare e scegliere **Elimina**.  
  
     L'eliminazione del modello non comporta l'eliminazione dei dati di training, ma solo dei metadati e degli schemi creati durante il training del modello.  
  
### <a name="delete-a-mining-model-using-dmx"></a>Eliminare un modello di data mining tramite DMX  
  
-   [ELIMINARE IL MODELLO DI DATA MINING & #40; DMX & #41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività di modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
