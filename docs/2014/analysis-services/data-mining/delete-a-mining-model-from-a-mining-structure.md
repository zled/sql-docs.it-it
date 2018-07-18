---
title: Eliminare un modello di Data Mining da una struttura di Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b5d2a4500de682ecf9d0745c472d793ac4848235
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319441"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>Eliminare un modello di data mining da una struttura di data mining
  È possibile eliminare i modelli di data mining usando Progettazione modelli di data mining, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]o istruzioni DMX.  
  
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
  
-   [DROP MINING MODEL &AMP;#40;DMX&AMP;#41;](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](mining-model-tasks-and-how-tos.md)  
  
  
