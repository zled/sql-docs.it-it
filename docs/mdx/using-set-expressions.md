---
title: Utilizzo di Set di espressioni | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- expressions [MDX], set
- tuples
- set expressions [MDX]
ms.assetid: 88d65872-0cbe-4c95-b36f-e1aa4ac8ed07
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c6934579db146c851f2677e78abbfa34870de358
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="using-set-expressions"></a>Utilizzo di espressioni set
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Un set è costituito da un elenco ordinato di zeri o più tuple. Un set che non contiene tuple è detto set vuoto.  
  
 L'espressione completa di un set è costituita da zero o più tuple specificate in modo esplicito e racchiuse tra parentesi graffe:  
  
 {[{ *Tuple_expression* | *Member_expression* } [, { *Tuple_expression* | *Member_expression* }]...]}  
  
 Le espressioni di membro specificate in un'espressione set vengono convertite in espressioni di tupla a un membro.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrate due espressioni set utilizzate sugli assi Columns e Rows di una query:  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Sull'asse di Columns, il set  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 è costituito da due membri della dimensione Measures. Sull'asse di Rows, il set  
  
 {([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),  
  
 ([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),  
  
 ([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])},  
  
 è costituito da tre tuple, ognuna delle quali contiene due riferimenti espliciti a membri sulla gerarchia Product Categories della dimensione Product e sulla gerarchia Calendar della dimensione Date.  
  
 Per esempi di funzioni che restituiscono set, vedere [utilizzo di membri, tuple e set &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; MDX &#41;](../mdx/expressions-mdx.md)  
  
  
