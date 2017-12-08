---
title: La creazione di calcoli di celle in MDX (MultiDimensional Expression) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cef256029853aabd5017f610081ed45ac632a935
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-cell-calculations---build-cell-calculations"></a>Calcoli MDX di cella - calcoli di celle di compilazione
  Nel linguaggio MDX (Multidimensional Expressions) sono disponibili numerosi strumenti per la generazione di valori calcolati, ad esempio membri calcolati, rollup personalizzati e membri personalizzati. Utilizzando tali caratteristiche è tuttavia difficile agire su un set specifico di celle o su una singola cella.  
  
 Per generare valori calcolati per celle specifiche, è necessario utilizzare la caratteristica MDX per le celle calcolate. Le celle calcolate consentono di definire una specifica sezione di celle, detta *sottocubo di calcolo*, e di applicare una formula a ogni singola cella del sottocubo di calcolo in base a una condizione facoltativa applicabile a ogni cella.  
  
 Le celle calcolate offrono inoltre funzionalità complesse, ad esempio le formule per la ricerca dell'obiettivo utilizzate negli indicatori di prestazioni chiave (KPI) oppure le formule per l'analisi speculativa. Questo livello di funzionalità si basa sulla caratteristica di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per l'ordine di calcolo, che consente l'uso di sessioni di calcolo ricorsive con le celle calcolate, applicando le formule di calcolo in sessioni specifiche nell'ordine di calcolo. Per altre informazioni sull'ordine di calcolo, vedere [Informazioni sull'ordine di calcolo e di valutazione &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
 Per quanto concerne l'ambito di creazione, le celle calcolate sono simili sia ai set denominati che ai membri calcolati, poiché possono essere create temporaneamente per la durata di una sessione o di una singola query oppure possono essere rese disponibili a livello globale nell'ambito di un cubo.  
  
-   **Ambito query** Per creare una cella calcolata definita come parte di una query MDX e il cui ambito è pertanto limitato alla query, è necessario specificare la parola chiave WITH. La cella calcolata può essere quindi utilizzata in un'istruzione MDX SELECT. Usando questo approccio è possibile modificare la cella calcolata creata mediante la parola chiave **WITH** senza alterare l'istruzione SELECT.  
  
     Per altre informazioni sulla creazione di membri calcolati mediante la parola chiave WITH, vedere [Creazione di formule per il calcolo di celle con ambito query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md).  
  
-   **Ambito sessione** Per creare una cella calcolata il cui ambito risulti più ampio del contesto della query, ovvero il cui ambito corrisponda alla durata della sessione MDX, è necessario usare l'istruzione CREATE CELL CALCULATION o l'istruzione ALTER CUBE.  
  
     Per altre informazioni sulla creazione di celle calcolate in una sessione mediante l'istruzione CREATE CELL CALCULATION o l'istruzione ALTER CUBE, vedere [Creazione di celle calcolate con ambito sessione](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione ALTER CUBE &#40;MDX&#41;](../../../mdx/mdx-data-definition-alter-cube.md)   
 [CREARE l'istruzione di calcolo di celle &#40; MDX &#41;](../../../mdx/mdx-data-definition-create-cell-calculation.md)   
 [Creazione di calcoli di celle con ambito Query &#40; MDX &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
