---
title: Modifica dei dati (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
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
ms.openlocfilehash: fcf75945b77c8ced0321089805f7e23fc7223821
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-modification---modifying-data"></a>Modifica dei dati MDX - modifica dei dati
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Oltre a utilizzare MDX (Multidimensional Expressions) per recuperare e gestire i dati di cubi e dimensioni, è possibile utilizzare MDX per l'aggiornamento o *writeback* dimensione e il cubo di dati. Tali aggiornamenti possono essere temporanei, come nel caso delle analisi speculative, o di simulazione, oppure permanenti, come nel caso in cui le modifiche dipendono dall'analisi dei dati.  
  
 Gli aggiornamenti possono essere eseguiti a livello di dimensione o di cubo:  
  
 **Writeback delle dimensioni**  
 È possibile usare l'istruzione [ALTER CUBE Statement (MDX)](../../../mdx/mdx-data-definition-alter-cube.md) per modificare i dati di una dimensione abilitata per la scrittura e [REFRESH CUBE Statement (MDX)](../../../mdx/mdx-data-definition-refresh-cube.md) per riflettere l'eliminazione, la creazione e l'aggiornamento dei valori degli attributi. L'istruzione ALTER CUBE può essere inoltre utilizzata per svolgere operazioni complesse, ad esempio l'eliminazione di un intero sottoalbero di una gerarchia e la promozione dei figli di un membro eliminato.  
  
 **Writeback dei cubi**  
 È possibile usare l'istruzione [UPDATE CUBE](../../../mdx/mdx-data-manipulation-update-cube.md) per aggiornare un cubo abilitato per la scrittura. L'istruzione UPDATE CUBE consente di aggiornare una tupla con un valore specifico. È possibile usare l'istruzione [REFRESH CUBE Statement (MDX)](../../../mdx/mdx-data-definition-refresh-cube.md) per aggiornare i dati in una sessione client con i dati aggiornati del server.  
  
 Per altre informazioni, vedere [Utilizzo dei writeback dei cubi &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-modification-using-cube-writebacks.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
