---
title: STDEV (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a1ef1d720928298e8a44e075f45937903d178ef6
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743040"
---
# <a name="stdev-mdx"></a>Stdev (MDX)


  Restituisce la deviazione standard del campione di un'espressione numerica valutata su un set, utilizzando la formula della popolazione non distorta (con divisione per n-1).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stdev(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Remarks  
 Il **Stdev** funzione utilizza il popolamento non distorto formula, durante il [StdevP](../mdx/stdevp-mdx.md) funzione utilizza la formula della popolazione distorta.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la deviazione standard per Internet Order Quantity, valutata sui primi tre mesi dell'anno di calendario 2003 utilizzando la formula della popolazione non distorta.  
  
```  
WITH MEMBER Measures.x AS   
   Stdev   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
