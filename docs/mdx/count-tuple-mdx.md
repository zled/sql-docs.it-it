---
title: Conteggio (tupla) (MDX) | Documenti Microsoft
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
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: c8f4a570-54a8-4c00-ac4b-eef0ebdb353c
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f25899c01bfd30fa5868fa01487d16efa6ff03da
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="count-tuple-mdx"></a>Count (Tuple) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero di dimensioni in una tupla.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>Argomenti  
 *Tuple_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una tupla.  
  
## <a name="remarks"></a>Osservazioni  
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
 [Dimensione conteggio &#40; &#41; &#40; MDX &#41;](../mdx/count-dimension-mdx.md)   
 [Numero &#40; Livelli di gerarchia &#41; &#40; MDX &#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Numero &#40; Set &#41; &#40; MDX &#41;](../mdx/count-set-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

