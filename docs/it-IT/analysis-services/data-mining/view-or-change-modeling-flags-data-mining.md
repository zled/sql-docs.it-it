---
title: Visualizzare o modificare flag di modellazione (Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5ca890dca3e0ffb966f1b87a745b189db4af6d81
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="view-or-change-modeling-flags-data-mining"></a>Visualizzare o modificare flag di modellazione (Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  I flag di modellazione sono proprietà impostate in una colonna della struttura di data mining o in colonne del modello di data mining per controllare la modalità di elaborazione dei dati durante l'analisi da parte dell'algoritmo.  
  
 In Progettazione modelli di data mining è possibile visualizzare e modificare i flag di modellazione associati a una struttura di data mining o a una colonna di data mining visualizzando le proprietà della struttura o del modello. Inoltre, è possibile impostare i flag di modellazione tramite DMX, AMO o XMLA.  
  
 In questa procedura viene descritto come modificare i flag di modellazione nella finestra di progettazione.  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>Visualizzare o modificare il flag di modellazione per una colonna della struttura o una colonna del modello  
  
1.  In SQL Server Design Studio aprire Esplora soluzioni, quindi fare doppio clic sulla struttura di data mining.  
  
2.  Per impostare il flag di modellazione NOT NULL, fare clic sulla scheda **Struttura di data mining** . Per impostare i flag REGRESSOR o MODEL_EXISTENCE_ONLY, fare clic sulla scheda **Modello di data mining** .  
  
3.  Fare clic con il pulsante destro del mouse sulla colonna da visualizzare o modificare, quindi scegliere **Proprietà**.  
  
4.  Per aggiungere un nuovo flag di modellazione, fare clic sulla casella di testo accanto alla proprietà **ModelingFlags** e selezionare le casella o le caselle di controllo relative ai flag di modellazione che si desidera utilizzare.  
  
     I flag di modellazione vengono visualizzati solo se sono appropriati per il tipo di dati della colonna.  
  
    > [!NOTE]  
    >  Dopo avere modificato un flag di modellazione, è necessario rielaborare il modello.  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>Recuperare i flag di modellazione utilizzati nel modello  
  
-   In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire una finestra Query DMX e digitare una query simile alla seguente:  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività di modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Modello di Data Mining flag & #40; & #41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
  
