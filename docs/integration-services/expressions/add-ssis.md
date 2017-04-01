---
title: "+ (addizione) (SSIS) | Microsoft Docs"
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
  - "+ (addizione)"
  - "addizione - operatore (+)"
  - "aggiunta di espressioni"
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# + (addizione) (SSIS)
  Vengono aggiunte due espressioni numeriche.  
  
## Sintassi  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## Argomenti  
 *numeric_expression1, numeric_expression2*  
 Espressione valida con tipo di dati numeric.  
  
## Tipi restituiti  
 Dipendenti dai tipi di dati dei due argomenti. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Osservazioni  
 Se uno degli operandi è Null, il risultato sarà Null.  
  
## Esempi di espressione  
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
  
## Vedere anche  
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  