---
title: ~ (Not bit per bit) (espressione SSIS) | Documenti Microsoft
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
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 398f902d224f49e00b3fdc62bf39300ba180fda8
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="-bitwise-not-ssis-expression"></a>~ (NOT bit per bit) (espressione SSIS)
  Viene eseguita una negazione bit per bit di un valore integer. Questo operatore può essere applicato a tipi di dati integer con e senza segno.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *integer_expression*  
 Espressione valida con qualsiasi tipo di dati integer. *integer*_*expression* è un numero intero trasformato in un numero binario per l'operazione bit per bit. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati di *integer_expression.*  
  
## <a name="remarks"></a>Osservazioni  
 Nessuno  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene applicato l'operatore ~ (NOT) bit per bit al numero 170 (0000 0000 1010 1010). Il numero è un valore integer con segno.  
  
```  
  
~ 170  
```  
  
 L'espressione restituisce -170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>Vedere anche  
 [Associatività e precedenza operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40; Espressione SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

