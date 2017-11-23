---
title: Operatori di Rollup personalizzati nelle dimensioni padre-figlio | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1d731ba3666e4569a45b6ab3e9254a1eaafdda35
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="parent-child-dimension-attributes---custom-rollup-operators"></a>Attributi della dimensione padre-figlio - operatori personalizzati di Rollup
  Gli operatori personalizzati di rollup rappresentano un modo semplice per determinare la modalità di esecuzione del rollup dei valori padre di una gerarchia padre-figlio. In una dimensione che contiene una relazione padre-figlio, specificare una colonna che contiene operatori unari che determinano il rollup di tutti i membri non calcolati dell'attributo padre. L'operatore unario viene applicato ai membri ogni volta che i valori dei membri padre vengono valutati.  
  
 Gli operatori unari vengono archiviati nella colonna definita dalla proprietà **UnaryOperatorColumn** dell'attributo padre e vengono applicati a ogni membro dell'attributo. La colonna specificata da questa proprietà può risiedere nella tabella della dimensione o in una tabella correlata alla tabella della dimensione da una chiave esterna nella tabella della dimensione.  
  
 Gli operatori personalizzati di rollup offrono una funzionalità simile, anche se più semplificata, alle formule personalizzate membro. Una formula personalizzata membro utilizza le espressioni MDX (Multidimensional Expressions) per determinare il modo in cui viene eseguito il rollup dei membri. Un operatore personalizzato di rollup, invece, utilizza un operatore unario semplice per determinare gli effetti del valore di un membro sul relativo membro padre. Le formule personalizzate membro del livello precedente hanno priorità rispetto agli operatori personalizzati di rollup di un livello.  
  
## <a name="custom-rollup-precedence"></a>Precedenza del rollup personalizzato  
 In termini di precedenza, gli operatori personalizzati di rollup dell'attributo di origine di un livello di una gerarchia hanno la priorità rispetto alle formule personalizzate membro del livello precedente. Le formule personalizzate membro del livello precedente hanno però priorità rispetto agli operatori personalizzati di rollup di un livello.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire formule personalizzate membro](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)   
 [Operatori unari nelle dimensioni padre-figlio](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md)  
  
  
