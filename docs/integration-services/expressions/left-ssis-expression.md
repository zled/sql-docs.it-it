---
title: LEFT (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f65ac38bd8ce47d368720a0b3b4882be08a6db21
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="left-ssis-expression"></a>LEFT (espressione SSIS)
  Viene restituito il numero specificato di caratteri della parte più a sinistra dell'espressione di caratteri indicata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da cui estrarre i caratteri.  
  
 *number*  
 Espressione integer in cui viene indicato il numero di caratteri da restituire.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Se *number* è maggiore della lunghezza di *character_expression*, la funzione restituisce *character_expression*.  
  
 Se *number* ha valore zero, la funzione restituirà una stringa di lunghezza zero.  
  
 Se *number* è un numero negativo, la funzione restituirà un errore.  
  
 L'argomento *number* accetta variabili e colonne.  
  
 È possibile utilizzare LEFT solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da LEFT verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Se l'argomento è Null, verrà restituito Null da LEFT.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 Nell'esempio seguente viene utilizzato un valore letterale stringa. Il risultato restituito sarà `"Mountain"`.  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [RIGHT &#40;espressione SSIS&#41;](../../integration-services/expressions/right-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
