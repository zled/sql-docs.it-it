---
title: Operatori di Rollup personalizzati nelle dimensioni padre-figlio | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ced2c7f2fabb5c73364527b19423478e67d2894
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="parent-child-dimension-attributes---custom-rollup-operators"></a>Attributi della dimensione padre-figlio - operatori personalizzati di Rollup
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Gli operatori personalizzati di rollup rappresentano un modo semplice per determinare la modalità di esecuzione del rollup dei valori padre di una gerarchia padre-figlio. In una dimensione che contiene una relazione padre-figlio, specificare una colonna che contiene operatori unari che determinano il rollup di tutti i membri non calcolati dell'attributo padre. L'operatore unario viene applicato ai membri ogni volta che i valori dei membri padre vengono valutati.  
  
 Gli operatori unari vengono archiviati nella colonna definita dalla proprietà **UnaryOperatorColumn** dell'attributo padre e vengono applicati a ogni membro dell'attributo. La colonna specificata da questa proprietà può risiedere nella tabella della dimensione o in una tabella correlata alla tabella della dimensione da una chiave esterna nella tabella della dimensione.  
  
 Gli operatori personalizzati di rollup offrono una funzionalità simile, anche se più semplificata, alle formule personalizzate membro. Una formula personalizzata membro utilizza le espressioni MDX (Multidimensional Expressions) per determinare il modo in cui viene eseguito il rollup dei membri. Un operatore personalizzato di rollup, invece, utilizza un operatore unario semplice per determinare gli effetti del valore di un membro sul relativo membro padre. Le formule personalizzate membro del livello precedente hanno priorità rispetto agli operatori personalizzati di rollup di un livello.  
  
## <a name="custom-rollup-precedence"></a>Precedenza del rollup personalizzato  
 In termini di precedenza, gli operatori personalizzati di rollup dell'attributo di origine di un livello di una gerarchia hanno la priorità rispetto alle formule personalizzate membro del livello precedente. Le formule personalizzate membro del livello precedente hanno però priorità rispetto agli operatori personalizzati di rollup di un livello.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire formule personalizzate membro](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)   
 [Operatori unari nelle dimensioni padre-figlio](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md)  
  
  
