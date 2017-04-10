---
title: "- (sottrazione) (espressione SSIS) | Microsoft Docs"
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
  - "- (sottrazione)"
  - "sottrazione - operatore (-)"
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# - (sottrazione) (espressione SSIS)
  Viene sottratta la seconda espressione numerica dalla prima.  
  
## Sintassi  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## Argomenti  
 *numeric_expression1, numeric_expression2*  
 Espressione valida con tipo di dati numeric. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Tipi restituiti  
 Dipendenti dai tipi di dati dei due argomenti. Per altre informazioni, vedere [Tipi di dati nelle espressioni di Integration Services](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## Osservazioni  
 Racchiudere l'espressione con il meno unario tra parentesi per assicurarsi che l'espressione venga valutata nell'ordine corretto  
  
## Osservazioni  
 Se uno degli operandi è Null, il risultato sarà Null.  
  
## Esempi di espressione  
 In questo esempio viene eseguita una sottrazione tra alcuni valori letterali numerici.  
  
```  
5 - 6.09  
```  
  
 In questo esempio il valore nella colonna **StandardCost** viene sottratto dal valore nella colonna **ListPrice**.  
  
```  
ListPrice - StandardCost  
```  
  
 In questo esempio un valore calcolato viene sottratto dalla colonna **ListPrice**. Poiché il nome include il carattere %, la variabile **Discount%** deve essere racchiusa tra parentesi. Per altre informazioni, vedere [Identificatori &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## Vedere anche  
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  