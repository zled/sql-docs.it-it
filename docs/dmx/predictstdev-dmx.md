---
title: PredictStdev (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PredictStdev
dev_langs: DMX
helpviewer_keywords: PredictStdev function
ms.assetid: 2614aad0-f3f2-4f56-9dad-9c436f11a35f
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 80972c7888cab4c64e30e346064d321715e5f2ce
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="predictstdev-dmx"></a>PredictStdev (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce la deviazione standard stimata per la colonna specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictStdev(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Si applica a  
 Colonna scalare.  
  
## <a name="return-type"></a>Tipo restituito  
 Un valore scalare del tipo specificato da  *\<riferimento alla colonna scalare >*.  
  
## <a name="remarks"></a>Osservazioni  
 Se il riferimento alla colonna è discreto, **PredictStdev** restituisce 0, perché non è possibile calcolare la deviazione standard da valori discreti.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato un natural prediction join per determinare la probabilità che un individuo sia un acquirente di biciclette sulla base del modello di data mining TM Decision Tree e la deviazione standard per la stima.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictStdev([Bike Buyer]) AS [Standard Deviation]  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
