---
title: IsDescendant (DMX) | Documenti Microsoft
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
- IsDescendant
dev_langs:
- DMX
helpviewer_keywords:
- IsDescendant function
ms.assetid: d9fe7446-edb5-487b-8ea6-c9efaccf6d90
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4a1e7959a303b768851784af0ab9c88abd257674
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indica se il nodo corrente discende dal nodo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Tipo restituito  
 Tipo booleano.  
  
## <a name="remarks"></a>Osservazioni  
 **IsDescendant** viene utilizzato solo in [modello SELECT FROM &#60; &#62;. DMX contenuto &#40; &#41; ](../dmx/select-from-model-content-dmx.md) e [modello SELECT FROM &#60; &#62;. DMX DIMENSION_CONTENT &#40; &#41; ](../dmx/select-from-model-dimension-content-dmx.md) query.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti i case discendenti dal nodo specificato nella funzione IsDescendant.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

