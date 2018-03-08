---
title: RIGHT (espressione SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RIGHT function
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8927e53f0cb8bf082211a7f35a112c7ca626d83c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="right-ssis-expression"></a>RIGHT (espressione SSIS)
  Viene restituito il numero specificato di caratteri della parte più a destra dell'espressione di caratteri indicata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RIGHT(character_expression,integer_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da cui estrarre i caratteri.  
  
 *integer_expression*  
 Espressione integer in cui viene indicato il numero di caratteri da restituire.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Se *integer_expression* è maggiore della lunghezza di *character_expression*, la funzione restituirà *character_expression*.  
  
 Se *integer_expression* ha valore 0, la funzione restituirà una stringa di lunghezza zero.  
  
 Se *integer_expression* è un numero negativo, la funzione restituirà un errore.  
  
 L'argomento *integer_expression* accetta variabili e colonne.  
  
 È possibile utilizzare RIGHT solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da RIGHT verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Se l'argomento è Null, verrà restituito Null da RIGHT.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 Nell'esempio seguente viene utilizzato un valore letterale stringa. Il risultato restituito sarà `"Bike"`.  
  
```  
RIGHT("Mountain Bike", 4)  
```  
  
 Nell'esempio seguente dalla colonna `Times` viene restituito il numero di caratteri più a destra specificato nella variabile `Name` . Se `Name` è `Touring Front Wheel` e `Times` è 5, il risultato restituito sarà `"Wheel"`.  
  
```  
RIGHT(Name, @Times)  
```  
  
 Nell'esempio seguente dalla colonna `Times` viene inoltre restituito il numero di caratteri più a destra specificato nella variabile `Name` . `Times` dispone di un tipo di dati non integer e nell'espressione è incluso un cast esplicito al tipo di dati DT_I2. Se `Name` è `Touring Front Wheel` e `Times` è `4.32`, il risultato restituito sarà `"heel"` perché la funzione RIGHT converte il valore 4.32 in 4, quindi verranno restituiti i quattro caratteri più a destra.  
  
```  
RIGHT(Name, (DT_I2)@Times))  
```  
  
## <a name="see-also"></a>Vedere anche  
 [LEFT &#40;espressione SSIS&#41;](../../integration-services/expressions/left-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
