---
title: "RIGHT (espressione SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RIGHT - funzione"
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# RIGHT (espressione SSIS)
  Viene restituito il numero specificato di caratteri della parte più a destra dell'espressione di caratteri indicata.  
  
## Sintassi  
  
```  
  
RIGHT(character_expression,integer_expression)  
```  
  
## Argomenti  
 *character_expression*  
 Espressione di caratteri da cui estrarre i caratteri.  
  
 *integer_expression*  
 Espressione integer in cui viene indicato il numero di caratteri da restituire.  
  
## Tipi restituiti  
 DT_WSTR  
  
## Osservazioni  
 Se *integer_expression* è maggiore della lunghezza di *character_expression*, la funzione restituirà *character_expression*.  
  
 Se *integer_expression* ha valore 0, la funzione restituirà una stringa di lunghezza zero.  
  
 Se *integer_expression* è un numero negativo, la funzione restituirà un errore.  
  
 L'argomento *integer_expression* accetta variabili e colonne.  
  
 È possibile utilizzare RIGHT solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da RIGHT verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Se l'argomento è Null, verrà restituito Null da RIGHT.  
  
## Esempi di espressione  
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
  
## Vedere anche  
 [LEFT &#40;espressione SSIS&#41;](../../integration-services/expressions/left-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  