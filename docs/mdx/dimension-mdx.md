---
title: Dimensione (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Dimension
dev_langs:
- kbMDX
helpviewer_keywords:
- Dimension function
ms.assetid: 0e3ce539-1d34-45ca-8342-67796e11b730
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: cfdcc90f96b818a2b3592e4c914a5f34df33775f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dimension-mdx"></a>Dimension (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce la gerarchia contenente il membro, il livello o la gerarchia specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.Dimension  
  
Level syntax  
Level_Expression.Dimension  
  
Member syntax  
Member_Expression.Dimension  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
### <a name="examples"></a>Esempi  
 L'esempio seguente usa il **dimensione** funzione, in combinazione con il **nome** funzione per restituire il nome della gerarchia del membro specificato.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Name  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente la funzione Dimension viene utilizzata in combinazione con le funzioni Levels e Count per restituire il numero di livelli presenti nella gerarchia che contiene il membro specificato.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 L'esempio seguente usa il **dimensione** funzione, in combinazione con il **membri** e **conteggio** funzioni, per restituire il numero di membri nella gerarchia che contiene il membro specificato.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Conteggio &#40;livelli di gerarchia&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Numero & #40; Set & #41; & #40; MDX & #41;](../mdx/count-set-mdx.md)   
 [I livelli di &#40;MDX&#41;](../mdx/levels-mdx.md)   
 [I membri &#40;impostare&#41; &#40;MDX&#41;](../mdx/members-set-mdx.md)   
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
