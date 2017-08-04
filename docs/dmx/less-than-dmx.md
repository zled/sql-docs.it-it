---
title: '&lt;(Minore di) (DMX) | Documenti Microsoft'
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
dev_langs:
- DMX
helpviewer_keywords:
- less than (<)
- < (less than operator)
ms.assetid: 61d257ce-7ffd-4124-a795-49e5f8a6d72f
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8366421d379efcddd5576cebab1ae333842c91d0
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="lt-less-than-dmx"></a>&lt;(Minore di) (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue un'operazione di confronto che determina se il valore di un'espressione DMX (Data Mining Extensions) è minore di quello di un'altra espressione DMX.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DMX_Expression < DMX_Expression  
```  
  
#### <a name="parameters"></a>Parametri  
 *DMX_Expression*  
 Espressione DMX valida.  
  
## <a name="return-value"></a>Valore restituito  
 Valore booleano che contiene TRUE se entrambi i parametri sono non Null e il valore del primo parametro è minore di quello del secondo. Tale valore booleano contiene FALSE se entrambi i parametri sono non Null e il valore del primo parametro è maggiore o uguale a quello del secondo. Il valore booleano contiene un valore Null se un parametro o entrambi restituiscono un valore Null.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli operatori di confronto &#40; DMX &#41;](../dmx/operators-comparison.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  

