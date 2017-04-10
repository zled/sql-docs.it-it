---
title: "~ (NOT bit per bit) (espressione SSIS) | Microsoft Docs"
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
  - "NOT bit per bit (~)"
  - "~ (NOT bit per bit)"
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# ~ (NOT bit per bit) (espressione SSIS)
  Viene eseguita una negazione bit per bit di un valore integer. Questo operatore può essere applicato a tipi di dati integer con e senza segno.  
  
## Sintassi  
  
```  
  
~integer_expression  
  
```  
  
## Argomenti  
 *integer_expression*  
 Espressione valida con qualsiasi tipo di dati integer. *integer*_*expression* è un numero intero trasformato in un numero binario per l'operazione bit per bit. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Tipi restituiti  
 Restituisce il tipo di dati di *integer_expression.*  
  
## Osservazioni  
 Nessuno  
  
## Esempi di espressione  
 In questo esempio viene applicato l'operatore ~ (NOT) bit per bit al numero 170 (0000 0000 1010 1010). Il numero è un valore integer con segno.  
  
```  
  
~ 170  
```  
  
 L'espressione restituisce -170 (1111111101010101).  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## Vedere anche  
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  