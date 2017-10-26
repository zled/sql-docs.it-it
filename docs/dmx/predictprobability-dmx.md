---
title: PredictProbability (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PredictProbability
dev_langs:
- DMX
helpviewer_keywords:
- PredictProbability function
ms.assetid: 7bb7e74f-e33b-4f7b-ade8-be21ace0dbd0
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8e0cdcf4b193cf1b05967fdbc5b266ebd0ca9700
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="predictprobability-dmx"></a>PredictProbability (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene restituita la probabilità per uno stato specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Si applica a  
 Colonna scalare.  
  
## <a name="return-type"></a>Tipo restituito  
 Valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Se lo stato stimato viene omesso, verrà utilizzato lo stato con la probabilità più alta, escludendo il bucket degli stati mancanti. Per includere il bucket degli stati mancanti, impostare il \<stato stimato > per **INCLUDE_NULL**. Per restituire la probabilità per gli stati mancanti, impostare il \<stato stimato > su NULL.  
  
> [!NOTE]  
>  Alcuni modelli di data mining non forniscono i valori di probabilità e pertanto non possono utilizzare questa funzione. Inoltre, i valori di probabilità per un valore di destinazione specifico vengono calcolati in modo diverso o potrebbero essere interpretati in modo diverso a seconda del tipo di modello su cui si esegue la query. Per ulteriori informazioni sulle modalità di calcolo di probabilità per un determinato tipo di modello, vedere l'argomento di singoli algoritmi in [contenuto del modello di Data Mining &#40; Analysis Services - Data Mining &#41; ](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato un natural prediction join per determinare la probabilità che un individuo sia un acquirente di biciclette sulla base del modello di data mining TM Decision Tree e la probabilità per la stima. In questo esempio sono presenti due funzioni PredictProbability, una per ogni valore possibile. Se si omette questo argomento, la funzione restituisce la probabilità per il valore più probabile.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictProbability([Bike Buyer], 1) AS [Bike Buyer = Yes],  
  PredictProbability([Bike Buyer], 0) AS [Bike Buyer = No]  
FROM [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 Risultati dell'esempio:  
  
|Bike Buyer|Bike Buyer = Yes|Bike Buyer = No|  
|----------------|-----------------------|----------------------|  
|1|0.867074195848097|0.132755556974282|  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

