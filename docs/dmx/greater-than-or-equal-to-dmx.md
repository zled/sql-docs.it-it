---
title: '&gt;= (Maggiore o uguale a) (DMX) | Documenti Microsoft'
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- '>= (greater than or equal to operator)'
- greater than or equal to (>=)
ms.assetid: a96b7e9c-72dc-4df1-aa41-85aad933df96
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 85df71d95f7ff095dde940c66bc4378a8cae01b1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="gt-greater-than-or-equal-to-dmx"></a>&gt;= (Maggiore o uguale a) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un'operazione di confronto che determina se il valore di un'espressione DMX (Data Mining Extensions) è maggiore o uguale a quello di un'altra espressione DMX.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DMX_Expression >= DMX_Expression  
```  
  
#### <a name="parameters"></a>Parametri  
 *DMX_Expression*  
 Espressione DMX valida.  
  
## <a name="return-value"></a>Valore restituito  
 Valore booleano che contiene TRUE se entrambi i parametri sono non Null e il valore del primo parametro è maggiore o uguale a quello del secondo. Tale valore booleano contiene FALSE se entrambi i parametri sono non Null e il valore del primo parametro è minore di quello del secondo. Il valore booleano contiene un valore Null se un parametro o entrambi restituiscono un valore Null.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli operatori di confronto &#40;DMX&#41;](../dmx/operators-comparison.md)   
 [Estensioni Data Mining &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Gli operatori &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
