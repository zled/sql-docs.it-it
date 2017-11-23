---
title: '- (Sottrazione) (DMX) | Documenti Microsoft'
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: 9602e908-e80c-442a-a412-073e10d0abd4
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d1156dfc98cc1d2fd5d91e9f54fd0ab4001fa2b0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="--subtract-dmx"></a>- (sottrazione) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un'operazione aritmetica che sottrae un numero da un altro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Numeric_Expression - Numeric_Expression  
```  
  
#### <a name="parameters"></a>Parametri  
 *Numeric_expression*  
 Espressione DMX (Data Mining Extensions) valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Valore con il tipo di dati del parametro con precedenza maggiore.  
  
## <a name="remarks"></a>Osservazioni  
 È necessario che alle due espressioni sia applicato lo stesso tipo di dati oppure che un'espressione possa essere convertita in modo implicito nel tipo di dati dell'altra espressione. Se una delle due espressioni restituisce un valore Null, l'operatore restituirà il risultato dell'altra espressione.  
  
## <a name="see-also"></a>Vedere anche  
 [Aritmetici operatori &#40; DMX &#41;](../dmx/operators-arithmetic.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  
