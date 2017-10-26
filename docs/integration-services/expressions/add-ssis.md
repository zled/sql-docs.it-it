---
title: + (Aggiungere) (SSIS) | Documenti Microsoft
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
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 04596cf4762f2473da1555f4ce5f9cd210678986
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="-add-ssis"></a>+ (addizione) (SSIS)
  Vengono aggiunte due espressioni numeriche.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression1, numeric_expression2*  
 Espressione valida con tipo di dati numeric.  
  
## <a name="result-types"></a>Tipi restituiti  
 Dipendenti dai tipi di dati dei due argomenti. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="remarks"></a>Osservazioni  
 Se uno degli operandi è Null, il risultato sarà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio vengono sommati alcuni valori letterali numerici.  
  
```  
5 + 6.09 + 7.0  
```  
  
 In questo esempio vengono sommati i valori nelle colonne **VacationHours** e **SickLeaveHours** .  
  
```  
VacationHours + SickLeaveHours  
```  
  
 In questo esempio un valore calcolato viene sommato alla colonna **StandardCost** . Poiché il nome include il carattere %, la variabile **Profit%** deve essere racchiusa tra parentesi. Per altre informazioni, vedere [Identificatori &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Associatività e precedenza operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40; Espressione SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

