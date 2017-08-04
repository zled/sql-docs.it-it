---
title: Dimensione (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4d8bbf0f22d1a2370c167f2569ae388742836933
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="dimension-mdx"></a>Dimension (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [Numero &#40; Livelli di gerarchia &#41; &#40; MDX &#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Numero &#40; Set &#41; &#40; MDX &#41;](../mdx/count-set-mdx.md)   
 [Livelli di &#40; MDX &#41;](../mdx/levels-mdx.md)   
 [Membri &#40; Set &#41; &#40; MDX &#41;](../mdx/members-set-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

