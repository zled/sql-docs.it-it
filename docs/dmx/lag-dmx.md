---
title: Lag (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0f984e50b2c6a800a66f689d88b21dfcb487e282
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842494"
---
# <a name="lag-dmx"></a>Lag (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce l'intervallo di tempo tra la data del case corrente e l'ultima data del set di training.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>Tipo restituito  
 Valore scalare di tipo integer.  
  
## <a name="remarks"></a>Remarks  
 Se il **Lag** funzione viene utilizzata in un modello in cui la colonna KEY TIME si trova all'interno di una tabella nidificata, la funzione deve trovarsi nella Sub-select dell'istruzione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti i casi che rientrano negli ultimi 12 mesi dei dati utilizzati per il training del modello.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
