---
title: STDEV (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STDEV
dev_langs:
- kbMDX
helpviewer_keywords:
- Stdev function [MDX]
ms.assetid: c3e31763-18ca-4a2b-bc03-3ee777970c68
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6f1e975cb35d0de9d8aec1abaae590a5791422ad
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="stdev-mdx"></a>Stdev (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
