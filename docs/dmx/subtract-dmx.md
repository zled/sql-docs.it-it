---
title: '- (Sottrazione) (DMX) | Documenti Microsoft'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e15eba5f642d0506e7c23f0e5790d6867224f9a2
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842044"
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
  
## <a name="remarks"></a>Remarks  
 È necessario che alle due espressioni sia applicato lo stesso tipo di dati oppure che un'espressione possa essere convertita in modo implicito nel tipo di dati dell'altra espressione. Se una delle due espressioni restituisce un valore Null, l'operatore restituirà il risultato dell'altra espressione.  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori aritmetici &#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [Estensioni Data Mining &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Gli operatori &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
