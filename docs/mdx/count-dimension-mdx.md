---
title: Conteggio (dimensione) (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6ee8fe09f7a840d32511d3a208a4621612ee9939
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740150"
---
# <a name="count-dimension-mdx"></a>Count (Dimension) (MDX)


  Restituisce il numero di gerarchie in un cubo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>Remarks  
 Restituisce il numero di gerarchie di un cubo, inclusa la gerarchia `[Measures].[Measures]`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il numero delle gerarchie presenti nel cubo Adventure Works.  
  
```  
WITH MEMBER measures.X AS  
  dimensions.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Conteggio &#40;tupla&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [Conteggio &#40;livelli di gerarchia&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Conteggio &#40;impostare&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
