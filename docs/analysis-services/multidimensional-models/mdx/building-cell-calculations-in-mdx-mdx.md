---
title: "Compilazione di formule per il calcolo di celle in MDX (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "celle calcolate [MDX]"
  - "query [MDX], calcoli di celle"
  - "celle [MDX]"
  - "MDX [Analysis Services], calcoli"
  - "sottocubi di calcolo [MDX]"
  - "valori calcolati [MDX]"
  - "Espressioni MDX [Analysis Services], calcoli di celle"
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Compilazione di formule per il calcolo di celle in MDX (MDX)
  Nel linguaggio MDX (Multidimensional Expressions) sono disponibili numerosi strumenti per la generazione di valori calcolati, ad esempio membri calcolati, rollup personalizzati e membri personalizzati. Utilizzando tali caratteristiche è tuttavia difficile agire su un set specifico di celle o su una singola cella.  
  
 Per generare valori calcolati per celle specifiche, è necessario utilizzare la caratteristica MDX per le celle calcolate. Le celle calcolate consentono di definire una specifica sezione di celle, detta *sottocubo di calcolo*, e di applicare una formula a ogni singola cella del sottocubo di calcolo in base a una condizione facoltativa applicabile a ogni cella.  
  
 Le celle calcolate offrono inoltre funzionalità complesse, ad esempio le formule per la ricerca dell'obiettivo utilizzate negli indicatori di prestazioni chiave (KPI) oppure le formule per l'analisi speculativa. Questo livello di funzionalità si basa sulla caratteristica di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per l'ordine di calcolo, che consente l'uso di sessioni di calcolo ricorsive con le celle calcolate, applicando le formule di calcolo in sessioni specifiche nell'ordine di calcolo. Per altre informazioni sull'ordine di calcolo, vedere [Informazioni sull'ordine di calcolo e di valutazione &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/understanding-pass-order-and-solve-order-mdx.md).  
  
 Per quanto concerne l'ambito di creazione, le celle calcolate sono simili sia ai set denominati che ai membri calcolati, poiché possono essere create temporaneamente per la durata di una sessione o di una singola query oppure possono essere rese disponibili a livello globale nell'ambito di un cubo.  
  
-   **Ambito query** Per creare una cella calcolata definita come parte di una query MDX e il cui ambito è pertanto limitato alla query, è necessario specificare la parola chiave WITH. La cella calcolata può essere quindi utilizzata in un'istruzione MDX SELECT. Usando questo approccio è possibile modificare la cella calcolata creata mediante la parola chiave **WITH** senza alterare l'istruzione SELECT.  
  
     Per altre informazioni sulla creazione di membri calcolati mediante la parola chiave WITH, vedere [Creazione di formule per il calcolo di celle con ambito query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-cell-calculations-mdx.md).  
  
-   **Ambito sessione** Per creare una cella calcolata il cui ambito risulti più ampio del contesto della query, ovvero il cui ambito corrisponda alla durata della sessione MDX, è necessario usare l'istruzione CREATE CELL CALCULATION o l'istruzione ALTER CUBE.  
  
     Per altre informazioni sulla creazione di celle calcolate in una sessione mediante l'istruzione CREATE CELL CALCULATION o l'istruzione ALTER CUBE, vedere [Creazione di celle calcolate con ambito sessione](../../../analysis-services/multidimensional-models/mdx/creating-session-scoped-calculated-cells.md)  
  
## Vedere anche  
 [Istruzione ALTER CUBE &#40;MDX&#41;](../Topic/ALTER%20CUBE%20Statement%20\(MDX\).md)   
 [Istruzione CREATE CELL CALCULATION &#40;MDX&#41;](../Topic/CREATE%20CELL%20CALCULATION%20Statement%20\(MDX\).md)   
 [Creazione di formule per il calcolo di celle con ambito query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-cell-calculations-mdx.md)   
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  