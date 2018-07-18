---
title: (Divisione) (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ab2b355c551b868cec3ee4329460f8bb0532236
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37972667"
---
# <a name="divide-dmx"></a>(Divisione) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un'operazione aritmetica di divisione di un numero per un altro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Parametri  
 *Dividendo*  
 Espressione DMX (Data Mining Extensions) valida che restituisce un valore numerico.  
  
 *Divisore*  
 Espressione DMX valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Valore con il tipo di dati del parametro con precedenza maggiore.  
  
## <a name="remarks"></a>Note  
 Il valore restituito da questo operatore rappresenta il quoziente della divisione tra la prima e la seconda espressione.  
  
 È necessario che alle due espressioni sia applicato lo stesso tipo di dati oppure che un'espressione possa essere convertita in modo implicito nel tipo di dati dell'altra espressione. Se il divisore restituisce un valore Null, verrà generato un errore. Se il divisore e il dividendo restituiscono entrambi un valore Null, l'operatore restituirà un valore Null.  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori aritmetici &#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; di riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Gli operatori &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [Dividere &#40;espressione di SSIS&#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;Dividere&#41; &#40;Transact-SQL&#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  
