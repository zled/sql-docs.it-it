---
title: Eliminazione di un modello di Data Mining da una struttura di Data Mining | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 363ac575844136dee04f9cf249253479e64836dd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>Eliminare un modello di data mining da una struttura di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]È possibile eliminare i modelli di data mining utilizzando Progettazione modelli di Data Mining, utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], o tramite istruzioni DMX.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>Eliminare un modello di data mining utilizzando SQL Server Data Tools  
  
1.  Selezionare la scheda **Modelli di data mining** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sul modello da eliminare e quindi scegliere **Elimina**.  
  
     Verrà visualizzata la finestra di dialogo **Elimina oggetti** .  
  
3.  Fare clic su **OK**.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>Eliminare un modello di data mining utilizzando SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenente il modello.  
  
2.  Espandere **Strutture di data mining**e quindi espandere **Modelli di data mining**.  
  
3.  Fare clic con il pulsante destro del mouse sul modello che si vuole eliminare e scegliere **Elimina**.  
  
     L'eliminazione del modello non comporta l'eliminazione dei dati di training, ma solo dei metadati e degli schemi creati durante il training del modello.  
  
### <a name="delete-a-mining-model-using-dmx"></a>Eliminare un modello di data mining tramite DMX  
  
-   [DROP MINING MODEL &#40;DMX&#41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
