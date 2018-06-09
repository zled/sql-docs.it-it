---
title: Conteggio (tupla) (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3775af63181489b982778d40ddd69ebc12872271
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739850"
---
# <a name="count-tuple-mdx"></a>Count (Tuple) (MDX)


  Restituisce il numero di dimensioni in una tupla.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>Argomenti  
 *Tuple_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una tupla.  
  
## <a name="remarks"></a>Remarks  
 Restituisce il numero di dimensioni in una tupla.  
  
## <a name="example"></a>Esempio  
 La misura calcolata nella query seguente restituisce il valore 2, ovvero il numero di gerarchie presenti nella tupla `([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])`:  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Conteggio &#40;dimensione&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Conteggio &#40;livelli di gerarchia&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Conteggio &#40;impostare&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
