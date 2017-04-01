---
title: "&amp;&amp; (AND logico) (espressione SSIS) | Microsoft Docs"
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
  - "&& (AND logico)"
  - "AND, AND logico"
  - "AND logico (&&)"
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# &amp;&amp; (AND logico) (espressione SSIS)
  Viene eseguita un'operazione con AND logico. Viene restituito TRUE dall'espressione se tutte le condizioni sono TRUE.  
  
## Sintassi  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## Argomenti  
 *boolean _expression1, boolean_expression2*  
 Qualsiasi espressione valida che restituisce TRUE, FALSE o NULL.  
  
## Tipi restituiti  
 DT_BOOL  
  
## Osservazioni  
 Il risultato dell'operatore && è illustrato nella tabella seguente.  
  
|Risultato|Espressione|Espressione|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## Esempi di espressione  
 In questo esempio vengono usate le colonne **StandardCost** e **ListPrice**. Viene restituito TRUE se il valore della colonna **StandardCost** è minore di 300 e quello della colonna**ListPrice** è maggiore di 500.  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 In questo esempio vengono usate le variabili **SPrice** e **LPrice** anziché valori letterali.  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## Vedere anche  
 [&& &#40;AND bit per bit&#41; &#40;espressione SSIS&#41;](../../integration-services/expressions/bitwise-and-ssis-expression.md)   
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  