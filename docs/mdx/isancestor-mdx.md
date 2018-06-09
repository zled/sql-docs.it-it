---
title: IsAncestor (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8aacd6825a81ff172d8fdf79373f5b251d6e18b9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740621"
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)


  Indica se il membro specificato è un predecessore di un altro membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Member_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Il **IsAncestor** risultato della funzione **true** se il primo membro specificato è un predecessore del secondo membro specificato. In caso contrario, la funzione restituisce **false**.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente restituisce **true** se [Date]. [ Fiscal]. CurrentMember è un predecessore di 2003:  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Predecessore &#40;MDX&#41;](../mdx/ancestor-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
