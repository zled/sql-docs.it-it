---
title: "Operatori di rollup personalizzati nelle dimensioni padre-figlio | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "operazioni di rollup figlio"
  - "UnaryOperatorColumn - proprietà"
  - "operatori di rollup personalizzati [Analysis Services]"
  - "operatori unari"
  - "dimensioni padre-figlio [Analysis Services]"
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Operatori di rollup personalizzati nelle dimensioni padre-figlio
  Gli operatori personalizzati di rollup rappresentano un modo semplice per determinare la modalità di esecuzione del rollup dei valori padre di una gerarchia padre-figlio. In una dimensione che contiene una relazione padre-figlio, specificare una colonna che contiene operatori unari che determinano il rollup di tutti i membri non calcolati dell'attributo padre. L'operatore unario viene applicato ai membri ogni volta che i valori dei membri padre vengono valutati.  
  
 Gli operatori unari vengono archiviati nella colonna definita dalla proprietà **UnaryOperatorColumn** dell'attributo padre e vengono applicati a ogni membro dell'attributo. La colonna specificata da questa proprietà può risiedere nella tabella della dimensione o in una tabella correlata alla tabella della dimensione da una chiave esterna nella tabella della dimensione.  
  
 Gli operatori personalizzati di rollup offrono una funzionalità simile, anche se più semplificata, alle formule personalizzate membro. Una formula personalizzata membro utilizza le espressioni MDX (Multidimensional Expressions) per determinare il modo in cui viene eseguito il rollup dei membri. Un operatore personalizzato di rollup, invece, utilizza un operatore unario semplice per determinare gli effetti del valore di un membro sul relativo membro padre. Le formule personalizzate membro del livello precedente hanno priorità rispetto agli operatori personalizzati di rollup di un livello.  
  
## Precedenza del rollup personalizzato  
 In termini di precedenza, gli operatori personalizzati di rollup dell'attributo di origine di un livello di una gerarchia hanno la priorità rispetto alle formule personalizzate membro del livello precedente. Le formule personalizzate membro del livello precedente hanno però priorità rispetto agli operatori personalizzati di rollup di un livello.  
  
## Vedere anche  
 [Definire formule personalizzate membro](../../analysis-services/multidimensional-models/define-custom-member-formulas.md)   
 [Operatori unari nelle dimensioni padre-figlio](../../analysis-services/multidimensional-models/unary-operators-in-parent-child-dimensions.md)  
  
  