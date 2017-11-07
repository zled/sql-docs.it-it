---
title: Creazione di set denominati in MDX (MultiDimensional Expression) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9239f7ee621cec3032c42d10b70c75702b58db6
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-named-sets---building-named-sets"></a>MDX è denominato a set - creazione di set denominati
  Un'espressione set può essere costituita da una dichiarazione lunga e complessa e risultare pertanto difficile da seguire o comprendere oppure essere utilizzata con tale frequenza che la presenza di definizioni ripetute del set può creare confusione. Per semplificare l'utilizzo di espressioni lunghe, complesse o usate di frequente, le espressioni MDX (Multidimensional Expressions) consentono di definire un'espressione di questo tipo come *set denominato*.  
  
 Un set denominato è essenzialmente un'espressione set a cui è stato assegnato un alias. Un set denominato può incorporare qualsiasi funzione o membro che è normalmente possibile incorporare in un set. Poiché in MDX gli alias dei set denominati vengono gestiti come espressioni set, è possibile utilizzare tali alias in tutte le situazioni in cui è consentito utilizzare un'espressione set.  
  
 Un set denominato può essere definito con uno dei contesti seguenti:  
  
-   **Ambito query** Per creare un set denominato definito come parte di una query MDX, pertanto con ambito limitato alla query, è necessario usare la parola chiave WITH. Tale set denominato può essere quindi utilizzato in un'istruzione MDX SELECT. In questo modo il set denominato creato utilizzando la parola chiave WITH può essere modificato senza alterare l'istruzione SELECT.  
  
     Per altre informazioni sull'uso della parola chiave WITH per la creazione di set denominati, vedere [Creazione di set denominati con ambito query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
-   **Ambito sessione** Per creare un set denominato con ambito più ampio rispetto al contesto della query, ovvero con ambito corrispondente alla durata della sessione MDX, è possibile usare l'istruzione CREATE SET. Un set denominato definito utilizzando un'istruzione CREATE SET è disponibile per tutte le query MDX in tale sessione. L'istruzione CREATE SET risulta utile, ad esempio, in un'applicazione client che riutilizza in modo consistente un set in vari tipi di query.  
  
     Per altre informazioni sull'uso dell'istruzione CREATE SET per la creazione di set denominati in una sessione, vedere [Creazione di set denominati con ambito sessione &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-session-scoped-named-sets.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione SELECT &#40;MDX&#41;](../../../mdx/mdx-data-manipulation-select.md)   
 [CREARE l'istruzione SET &#40; MDX &#41;](../../../mdx/mdx-data-definition-create-set.md)   
 [Nozioni fondamentali sulle query MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  

