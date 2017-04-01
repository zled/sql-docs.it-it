---
title: "Modifica dei dati (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "modifica dei dati [MDX]"
  - "espressioni MDX [Analysis Services], modifica dei dati"
  - "MDX [Analysis Services], modifica dei dati"
  - "modifica dei dati (MDX)"
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Modifica dei dati (MDX)
  Oltre che per recuperare e gestire i dati di dimensioni e cubi, il linguaggio MDX (Multidimensional Expressions) può essere usato anche per aggiornarli o eseguirne il *writeback*. Tali aggiornamenti possono essere temporanei, come nel caso delle analisi speculative, o di simulazione, oppure permanenti, come nel caso in cui le modifiche dipendono dall'analisi dei dati.  
  
 Gli aggiornamenti possono essere eseguiti a livello di dimensione o di cubo:  
  
 **Writeback delle dimensioni**  
 È possibile usare l'istruzione [ALTER CUBE Statement (MDX)](../Topic/ALTER%20CUBE%20Statement%20\(MDX\).md) per modificare i dati di una dimensione abilitata per la scrittura e [REFRESH CUBE Statement (MDX)](../Topic/REFRESH%20CUBE%20Statement%20\(MDX\).md) per riflettere l'eliminazione, la creazione e l'aggiornamento dei valori degli attributi. L'istruzione ALTER CUBE può essere inoltre utilizzata per svolgere operazioni complesse, ad esempio l'eliminazione di un intero sottoalbero di una gerarchia e la promozione dei figli di un membro eliminato.  
  
 **Writeback dei cubi**  
 È possibile usare l'istruzione [UPDATE CUBE](../Topic/UPDATE%20CUBE%20Statement%20\(MDX\).md) per aggiornare un cubo abilitato per la scrittura. L'istruzione UPDATE CUBE consente di aggiornare una tupla con un valore specifico. È possibile usare l'istruzione [REFRESH CUBE Statement (MDX)](../Topic/REFRESH%20CUBE%20Statement%20\(MDX\).md) per aggiornare i dati in una sessione client con i dati aggiornati del server.  
  
 Per altre informazioni, vedere [Utilizzo dei writeback dei cubi &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-cube-writebacks-mdx.md).  
  
## Vedere anche  
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  