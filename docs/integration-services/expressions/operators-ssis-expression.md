---
title: Operatori (espressione SSIS) | Documenti Microsoft
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
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ab52310bc72b0288369ed10bccfbf0b58e6c6ee4
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="operators-ssis-expression"></a>Operatori (espressione SSIS)
  In questa sezione vengono descritti gli operatori disponibili nel linguaggio delle espressioni, nonché le regole di associatività e precedenza degli operatori utilizzate dall'analizzatore di espressioni.  
  
 Nella tabella seguente sono elencati gli argomenti dedicati agli operatori disponibili in questa sezione.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[Cast &#40; Espressione SSIS &#41;](../../integration-services/expressions/cast-ssis-expression.md)|Converte un'espressione da un tipo di dati a un altro.|  
|[&#40; &#41; &#40; Le parentesi &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/parentheses-ssis-expression.md)|Viene identificato l'ordine di valutazione delle espressioni.|  
|[+ &#40; Aggiungi &#41; &#40; SSIS &#41;](../../integration-services/expressions/add-ssis.md)|Vengono aggiunte due espressioni numeriche.|  
|[+ &#40; Concatenare &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/concatenate-ssis-expression.md)|Concatena due espressioni.|  
|[-&#40; Sottrarre &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/subtract-ssis-expression.md)|Viene sottratta la seconda espressione numerica dalla prima.|  
|[-&#40; Negare &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/negate-ssis-expression.md)|Viene applicato un segno negativo a un'espressione numerica.|  
|[&#42; &#40; Moltiplicare &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/multiply-ssis-expression.md)|Vengono moltiplicate due espressioni numeriche.|  
|[Divisione &#40; Espressione SSIS &#41;](../../integration-services/expressions/divide-ssis-expression.md)|Viene divisa la prima espressione numerica per la seconda.|  
|[&#40; Modulo &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/modulo-ssis-expression.md)|Viene restituito il resto Integer dopo aver diviso la prima espressione numerica per la seconda.|  
|[&#124; &#124; &#40; OR logico &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/logical-or-ssis-expression.md)|Viene eseguita un'operazione con OR logico.|  
|[& & &#40; AND logico &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/logical-and-ssis-expression.md)|Viene eseguita un'operazione con AND logico.|  
|[! &#40; Not logico &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/logical-not-ssis-expression.md)|NOT logico di un operando booleano.|  
|[&#124; &#40; Bit per bit Inclusivo &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)|Viene eseguita un'operazione con OR bit per bit su due valori integer.|  
|[^ &#40; Bit per bit esclusivo &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)|Viene eseguita un'operazione con OR esclusivo bit per bit su due valori integer.|  
|[& &#40; AND bit per bit &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/bitwise-and-ssis-expression.md)|Esegue un'operazione con AND bit per bit tra due valori integer.|  
|[~ &#40; Not bit per bit &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/bitwise-not-ssis-expression.md)|Viene eseguita una negazione bit per bit di un valore integer.|  
|[= = &#40; Uguale &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/equal-ssis-expression.md)|Viene eseguito un confronto per determinare se due espressioni sono uguali.|  
|[! = &#40; Diverso da &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/unequal-ssis-expression.md)|Esegue un confronto per determinare se due espressioni sono diverse.|  
|[&#62; &#40; Maggiore di &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/greater-than-ssis-expression.md)|Esegue un confronto per determinare se la prima espressione è maggiore della seconda.|  
|[&#60; &#40; Minore di &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/less-than-ssis-expression.md)|Viene eseguito un confronto per determinare se la prima espressione è minore della seconda.|  
|[&#62; = &#40; Maggiore o uguale a &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/greater-than-or-equal-to-ssis-expression.md)|Viene eseguito un confronto per determinare se la prima espressione è maggiore o uguale alla seconda.|  
|[&#60; = &#40; Minore o uguale a &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/less-than-or-equal-to-ssis-expression.md)|Viene eseguito un confronto per determinare se la prima espressione è minore o uguale alla seconda.|  
|[? : &#40; Condizionale &#41; &#40; Espressione SSIS &#41;](../../integration-services/expressions/conditional-ssis-expression.md)|Viene restituita una di due espressioni in base alla valutazione di un'espressione booleana.|  
  
 Per informazioni sulla posizione di ogni operatore nella gerarchia delle precedenze, vedere [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; Espressione SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [Esempi di espressioni di servizi di integrazione avanzata](../../integration-services/expressions/examples-of-advanced-integration-services-expressions.md)   
 [Integration Services &#40; SSIS &#41; Espressioni](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  
