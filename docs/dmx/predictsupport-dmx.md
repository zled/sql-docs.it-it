---
title: PredictSupport (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 57b340d4f79ec093f6322687ceca0186931a9dcf
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842074"
---
# <a name="predictsupport-dmx"></a>PredictSupport (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Viene restituito il valore di supporto per uno stato specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Si applica a  
 Colonna scalare.  
  
## <a name="return-type"></a>Tipo restituito  
 Un valore scalare del tipo specificato da *\<* riferimento alla colonna scalare*>*.  
  
## <a name="remarks"></a>Remarks  
 Se lo stato stimato viene omesso, verrà utilizzato lo stato con la più alta probabilità stimabile, escludendo il bucket degli stati mancanti. Per includere il bucket degli stati mancanti, impostare il \<stato stimato > per **INCLUDE_NULL**.  
  
 Per restituire il supporto per gli stati mancanti, impostare il \<stato stimato > su NULL.  
  
> [!NOTE]  
>  I valori di supporto vengono calcolati in modo diverso o potrebbero essere interpretati in modo diverso a seconda del tipo di modello su cui si esegue la query. Per ulteriori informazioni sulle modalità di calcolo di supporto per qualsiasi tipo di modello specifico, vedere il singolo algoritmo corrispondente digitare [Mining Model Content &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata una query singleton per stimare se un individuo sarà un acquirente di biciclette e determinare il supporto per la stima sulla base del modello di data mining TM Decision Tree.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictSupport([Bike Buyer]) AS [Support],  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
