---
title: Conteggio (dimensione) (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd8d61e7907a8fb05a016dabdcb65201bffdbbdc
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577643"
---
# <a name="count-dimension-mdx"></a>Count (Dimension) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
  
