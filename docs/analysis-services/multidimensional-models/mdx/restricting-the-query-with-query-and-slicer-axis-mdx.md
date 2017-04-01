---
title: "Restrizione della query con gli assi della query e di sezionamento (MDX) | Microsoft Docs"
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
  - "espressioni MDX [Analysis Services], assi"
  - "query [MDX], assi"
  - "assi [MDX]"
  - "MDX [Analysis Services], assi"
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Restrizione della query con gli assi della query e di sezionamento (MDX)
  Per la formulazione di un'istruzione SELECT di MDX (Multidimensional Expression), un'applicazione in genere analizza il cubo e suddivide il set di gerarchie in due subset:  
  
-   **Assi della query**, ovvero il set di gerarchie da cui vengono recuperati i dati per più membri. Per altre informazioni sugli assi delle query, vedere [Impostazione del contenuto di un asse della query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-query-axis-mdx.md).  
  
-   **Asse di sezionamento**, ovvero il set di gerarchie da cui vengono recuperati i dati per un unico membro. Per altre informazioni sull'asse di sezionamento, vedere [Impostazione del contenuto di un asse di sezionamento &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-slicer-axis-mdx.md).  
  
 Poiché gli assi della query e di sezionamento possono essere costruiti da più gerarchie del cubo su cui eseguire la query, questi termini vengono utilizzati per distinguere le gerarchie utilizzate dal cubo su cui eseguire la query dalle gerarchie create nel cubo restituito da una query MDX.  
  
 Per vedere un semplice esempio di uso degli assi delle query e degli assi di sezionamento, vedere [Utilizzo di assi di query e assi di sezionamento in un semplice esempio &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-query-and-slicer-axes-in-a-simple-example-mdx.md).  
  
## Vedere anche  
 [Utilizzo di membri, tuple e set &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  