---
title: Modifica dei dati (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
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
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 63268d2f905d91833ad1ec542d0db78ab7b921cf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-data-modification---modifying-data"></a>Modifica dei dati MDX - modifica dei dati
  Oltre che per recuperare e gestire i dati di dimensioni e cubi, il linguaggio MDX (Multidimensional Expressions) può essere usato anche per aggiornarli o eseguirne il *writeback* . Tali aggiornamenti possono essere temporanei, come nel caso delle analisi speculative, o di simulazione, oppure permanenti, come nel caso in cui le modifiche dipendono dall'analisi dei dati.  
  
 Gli aggiornamenti possono essere eseguiti a livello di dimensione o di cubo:  
  
 **Writeback delle dimensioni**  
 È possibile usare l'istruzione [ALTER CUBE Statement (MDX)](../../../mdx/mdx-data-definition-alter-cube.md) per modificare i dati di una dimensione abilitata per la scrittura e [REFRESH CUBE Statement (MDX)](../../../mdx/mdx-data-definition-refresh-cube.md) per riflettere l'eliminazione, la creazione e l'aggiornamento dei valori degli attributi. L'istruzione ALTER CUBE può essere inoltre utilizzata per svolgere operazioni complesse, ad esempio l'eliminazione di un intero sottoalbero di una gerarchia e la promozione dei figli di un membro eliminato.  
  
 **Writeback dei cubi**  
 È possibile usare l'istruzione [UPDATE CUBE](../../../mdx/mdx-data-manipulation-update-cube.md) per aggiornare un cubo abilitato per la scrittura. L'istruzione UPDATE CUBE consente di aggiornare una tupla con un valore specifico. È possibile usare l'istruzione [REFRESH CUBE Statement (MDX)](../../../mdx/mdx-data-definition-refresh-cube.md) per aggiornare i dati in una sessione client con i dati aggiornati del server.  
  
 Per altre informazioni, vedere [Utilizzo dei writeback dei cubi &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-modification-using-cube-writebacks.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
