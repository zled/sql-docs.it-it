---
title: '- (Sottrazione) (DMX) | Documenti Microsoft'
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
- '- (subtract)'
- subtract operator (-)
ms.assetid: 9602e908-e80c-442a-a412-073e10d0abd4
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6385e939f6dcf1881b86d9aa20d7f8e6c04aceb4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="--subtract-dmx"></a>- (sottrazione) (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  

