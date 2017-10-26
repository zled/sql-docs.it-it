---
title: Lag (DMX) | Documenti Microsoft
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
- LAG
dev_langs:
- DMX
helpviewer_keywords:
- Lag function
ms.assetid: 2da6df1a-5506-4871-a0f0-83292f1df41e
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4947b2f9a0dc89cd79923f2528ee21471ea9091e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="lag-dmx"></a>Lag (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce l'intervallo di tempo tra la data del case corrente e l'ultima data del set di training.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>Tipo restituito  
 Valore scalare di tipo integer.  
  
## <a name="remarks"></a>Osservazioni  
 Se il **Lag** funzione viene utilizzata in un modello in cui la colonna KEY TIME si trova all'interno di una tabella nidificata, la funzione deve trovarsi nella Sub-select dell'istruzione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti i casi che rientrano negli ultimi 12 mesi dei dati utilizzati per il training del modello.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

