---
title: '|| (OR logico) (Espressione SSIS) | Documenti Microsoft'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c369d66dbfdfefa0249ef0e479266bf17cf8f7d6
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="-logical-or-ssis-expression"></a>|| (OR logico) (espressione SSIS)
  Viene eseguita un'operazione con OR logico. Viene restituito TRUE dall'espressione se una o entrambe le condizioni sono TRUE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>Argomenti  
 *boolean_expression1, boolean_expression2*  
 Qualsiasi espressione valida che restituisce TRUE, FALSE o NULL.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_BOOL  
  
## <a name="remarks"></a>Osservazioni  
 Il risultato dell'operatore || è illustrato nella tabella seguente.  
  
|Risultato|Espressione|Espressione|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>Esempi di espressione SSIS  
 In questo esempio vengono utilizzate le colonne **StandardCost** e **ListPrice** . Viene restituito TRUE se il valore della colonna **StandardCost** è minore di 300 o quello della colonna **ListPrice** è maggiore di 500.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 In questo esempio vengono utilizzate le variabili **SPrice** e **LPrice** anziché valori letterali numerici.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Vedere anche  
 [&#124; &#40; Bit per bit Inclusivo &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40; Bit per bit esclusivo &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [Associatività e precedenza operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40; Espressione SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

