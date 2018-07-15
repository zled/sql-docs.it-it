---
title: Operatori (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 779597ab830df7cf89ad3d830c41402b43a91768
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320691"
---
# <a name="operators-ssis-expression"></a>Operatori (espressione SSIS)
  In questa sezione vengono descritti gli operatori disponibili nel linguaggio delle espressioni, nonché le regole di associatività e precedenza degli operatori utilizzate dall'analizzatore di espressioni.  
  
 Nella tabella seguente sono elencati gli argomenti dedicati agli operatori disponibili in questa sezione.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[Cast di &#40;espressione di SSIS&#41;](cast-ssis-expression.md)|Converte un'espressione da un tipo di dati a un altro.|  
|[&#40;&#41;&#40;Parentesi&#41; &#40;espressione di SSIS&#41;](parentheses-ssis-expression.md)|Viene identificato l'ordine di valutazione delle espressioni.|  
|[+ &#40;Aggiungi&#41; &#40;SSIS&#41;](add-ssis.md)|Vengono aggiunte due espressioni numeriche.|  
|[+ &#40;Concatenate&#41; &#40;espressione di SSIS&#41;](concatenate-ssis-expression.md)|Concatena due espressioni.|  
|[- &#40;Sottrarre&#41; &#40;espressione di SSIS&#41;](subtract-ssis-expression.md)|Viene sottratta la seconda espressione numerica dalla prima.|  
|[- &#40;Negazione&#41; &#40;espressione di SSIS&#41;](negate-ssis-expression.md)|Viene applicato un segno negativo a un'espressione numerica.|  
|[&#42;&#40;Moltiplica&#41; &#40;espressione di SSIS&#41;](multiply-ssis-expression.md)|Vengono moltiplicate due espressioni numeriche.|  
|[Dividere &#40;espressione di SSIS&#41;](divide-ssis-expression.md)|Viene divisa la prima espressione numerica per la seconda.|  
|[&#40;Modulo&#41; &#40;espressioni SSIS&#41;](modulo-ssis-expression.md)|Viene restituito il resto Integer dopo aver diviso la prima espressione numerica per la seconda.|  
|[&#124;&#124;&#40;OR logico&#41; &#40;espressione di SSIS&#41;](logical-or-ssis-expression.md)|Viene eseguita un'operazione con OR logico.|  
|[& & &#40;AND logico&#41; &#40;espressione di SSIS&#41;](logical-and-ssis-expression.md)|Viene eseguita un'operazione con AND logico.|  
|[! &#40;Not logico&#41; &#40;espressione di SSIS&#41;](logical-not-ssis-expression.md)|NOT logico di un operando booleano.|  
|[&#124;&#40;Bit per bit Inclusivo&#41; &#40;espressione di SSIS&#41;](bitwise-inclusive-or-ssis-expression.md)|Viene eseguita un'operazione con OR bit per bit su due valori integer.|  
|[^ &#40;Bit per bit esclusivo&#41; &#40;espressione di SSIS&#41;](bitwise-exclusive-or-ssis-expression.md)|Viene eseguita un'operazione con OR esclusivo bit per bit su due valori integer.|  
|[& &#40;AND bit per bit&#41; &#40;espressione di SSIS&#41;](bitwise-and-ssis-expression.md)|Esegue un'operazione con AND bit per bit tra due valori integer.|  
|[~ &#40;Not bit per bit&#41; &#40;espressione di SSIS&#41;](bitwise-not-ssis-expression.md)|Viene eseguita una negazione bit per bit di un valore integer.|  
|[= = &#40;Uguale&#41; &#40;espressione di SSIS&#41;](equal-ssis-expression.md)|Viene eseguito un confronto per determinare se due espressioni sono uguali.|  
|[\!= &#40;diverso da&#41; &#40;espressione SSIS&#41;](unequal-ssis-expression.md)|Esegue un confronto per determinare se due espressioni sono diverse.|  
|[&#62;&#40;Maggiore di&#41; &#40;espressione di SSIS&#41;](greater-than-ssis-expression.md)|Esegue un confronto per determinare se la prima espressione è maggiore della seconda.|  
|[&#60;&#40;Minore di&#41; &#40;espressione di SSIS&#41;](less-than-ssis-expression.md)|Viene eseguito un confronto per determinare se la prima espressione è minore della seconda.|  
|[&#62;= &#40;Maggiore o uguale a&#41; &#40;espressione di SSIS&#41;](greater-than-or-equal-to-ssis-expression.md)|Viene eseguito un confronto per determinare se la prima espressione è maggiore o uguale alla seconda.|  
|[&#60;= &#40;Minore o uguale a&#41; &#40;espressione di SSIS&#41;](less-than-or-equal-to-ssis-expression.md)|Viene eseguito un confronto per determinare se la prima espressione è minore o uguale alla seconda.|  
|[? : &#40;condizionale&#41; &#40;espressione SSIS&#41;](conditional-ssis-expression.md)|Viene restituita una di due espressioni in base alla valutazione di un'espressione booleana.|  
  
 Per informazioni sulla posizione di ogni operatore nella gerarchia delle precedenze, vedere [Precedenza e associatività degli operatori](operator-precedence-and-associativity.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Le funzioni &#40;espressione di SSIS&#41;](functions-ssis-expression.md)   
 [Esempi di espressioni avanzate di Integration Services](examples-of-advanced-integration-services-expressions.md)   
 [Espressioni di Integration Services &#40;SSIS&#41;](integration-services-ssis-expressions.md)  
  
  
