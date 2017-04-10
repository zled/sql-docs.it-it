---
title: "Compilazione di set denominati in MDX (MDX) | Microsoft Docs"
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
  - "MDX (MultiDimensional Expressions) [Analysis Services], set denominati"
  - "set denominati [MDX]"
  - "set [MDX]"
  - "MDX [Analysis Services], set denominati"
  - "query [MDX], set denominati"
  - "espressioni set [MDX]"
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Compilazione di set denominati in MDX (MDX)
  Un'espressione set può essere costituita da una dichiarazione lunga e complessa e risultare pertanto difficile da seguire o comprendere oppure essere utilizzata con tale frequenza che la presenza di definizioni ripetute del set può creare confusione. Per semplificare l'utilizzo di espressioni lunghe, complesse o usate di frequente, le espressioni MDX (Multidimensional Expressions) consentono di definire un'espressione di questo tipo come *set denominato*.  
  
 Un set denominato è essenzialmente un'espressione set a cui è stato assegnato un alias. Un set denominato può incorporare qualsiasi funzione o membro che è normalmente possibile incorporare in un set. Poiché in MDX gli alias dei set denominati vengono gestiti come espressioni set, è possibile utilizzare tali alias in tutte le situazioni in cui è consentito utilizzare un'espressione set.  
  
 Un set denominato può essere definito con uno dei contesti seguenti:  
  
-   **Ambito query** Per creare un set denominato definito come parte di una query MDX, pertanto con ambito limitato alla query, è necessario usare la parola chiave WITH. Tale set denominato può essere quindi utilizzato in un'istruzione MDX SELECT. In questo modo il set denominato creato utilizzando la parola chiave WITH può essere modificato senza alterare l'istruzione SELECT.  
  
     Per altre informazioni sull'uso della parola chiave WITH per la creazione di set denominati, vedere [Creazione di set denominati con ambito query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-named-sets-mdx.md).  
  
-   **Ambito sessione** Per creare un set denominato con ambito più ampio rispetto al contesto della query, ovvero con ambito corrispondente alla durata della sessione MDX, è possibile usare l'istruzione CREATE SET. Un set denominato definito utilizzando un'istruzione CREATE SET è disponibile per tutte le query MDX in tale sessione. L'istruzione CREATE SET risulta utile, ad esempio, in un'applicazione client che riutilizza in modo consistente un set in vari tipi di query.  
  
     Per altre informazioni sull'uso dell'istruzione CREATE SET per la creazione di set denominati in una sessione, vedere [Creazione di set denominati con ambito sessione &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-session-scoped-named-sets-mdx.md).  
  
## Vedere anche  
 [Istruzione SELECT &#40;MDX&#41;](../Topic/SELECT%20Statement%20\(MDX\).md)   
 [Istruzione CREATE SET &#40;MDX&#41;](../Topic/CREATE%20SET%20Statement%20\(MDX\).md)   
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  