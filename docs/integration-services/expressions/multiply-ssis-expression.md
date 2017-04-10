---
title: "* (moltiplicazione) (espressione SSIS) | Microsoft Docs"
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
  - "* (operatore di moltiplicazione)"
  - "moltiplicazione - operatore (*)"
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# * (moltiplicazione) (espressione SSIS)
  Vengono moltiplicate due espressioni numeriche.  
  
## Sintassi  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## Argomenti  
 *numeric_expression1, numeric_expression2*  
 Espressione valida con tipo di dati numeric. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Tipi restituiti  
 Dipendenti dai tipi di dati dei due argomenti. Per altre informazioni, vedere [Tipi di dati nelle espressioni di Integration Services](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## Osservazioni  
 Se uno degli operandi è Null, il risultato sarà Null.  
  
## Esempi di espressione  
 In questo esempio vengono moltiplicati due valori letterali numerici.  
  
```  
5 * 6.09  
```  
  
 Questo esempio moltiplica i valori nella colonna **ListPrice** per il 10%.  
  
```  
ListPrice * .10  
```  
  
 Questo esempio sottrae il risultato di un'espressione dalla colonna **ListPrice**. Poiché il nome include il carattere %, la variabile **Discount%** deve essere racchiusa tra parentesi. Per altre informazioni, vedere [Identificatori &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## Vedere anche  
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  