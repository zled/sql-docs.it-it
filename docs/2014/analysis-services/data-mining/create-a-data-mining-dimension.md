---
title: Creare una dimensione di Data Mining | Microsoft Docs
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
- mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1e0bb84b1627aaeafaf16a39df9a1bdf32fef489
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220461"
---
# <a name="create-a-data-mining-dimension"></a>Creare una dimensione di data mining
  Se la struttura di data mining è basata su un cubo OLAP, è possibile creare una dimensione che includa il contenuto del modello di data mining. È quindi possibile includere nuovamente la dimensione nel cubo di origine.  
  
 È inoltre possibile esplorare la dimensione, utilizzarla per esplorare i risultati del modello o eseguire una query sulla dimensione tramite MDX.  
  
### <a name="to-create-a-data-mining-dimension"></a>Per creare una dimensione di data mining  
  
1.  In Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]selezionare la scheda **Struttura di data mining** o **Modelli di data mining** .  
  
2.  Scegliere **Crea dimensione di data mining** dal menu **Modello di data mining**.  
  
     Verrà visualizzata la finestra di dialogo **Crea dimensione di data mining** .  
  
3.  Nell'elenco **Nome modello** della finestra di dialogo **Crea dimensione di data mining** selezionare un modello di data mining OLAP.  
  
4.  Nella casella **Nome dimensione** immettere un nome per la nuova dimensione di data mining.  
  
5.  Per creare un cubo che includa la nuova dimensione di data mining, selezionare **Crea cubo**. Dopo avere fatto clic su **Crea cubo**, è possibile immettere un nuovo nome per il cubo.  
  
6.  Fare clic su **OK**.  
  
     La dimensione di data mining verrà creata e aggiunta alla cartella **Dimensioni** in Esplora soluzioni. Se è stata selezionata l'opzione **Crea cubo**verrà anche creato un nuovo cubo, che verrà aggiunto alla cartella **Cubi** .  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative alla struttura di data mining](mining-structure-tasks-and-how-tos.md)  
  
  
