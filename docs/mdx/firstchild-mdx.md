---
title: FirstChild (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed769da991c54b4ae7bc85091a652a27f5399a73
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740380"
---
# <a name="firstchild-mdx"></a>FirstChild (MDX)


  Restituisce il primo membro figlio di un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.FirstChild   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
### <a name="example"></a>Esempio  
 La query seguente restituisce il primo membro figlio dell'anno fiscale 2003 nella gerarchia Fiscal, ovvero il primo semestre dell'anno fiscale 2003.  
  
```  
SELECT [Date].[Fiscal].[Fiscal Year].&[2003].FirstChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [LastChild &#40;MDX&#41;](../mdx/lastchild-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
