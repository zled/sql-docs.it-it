---
title: FirstChild (MDX) | Documenti Microsoft
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
- FIRSTCHILD
dev_langs:
- kbMDX
helpviewer_keywords:
- FirstChild function
ms.assetid: 3c19a169-7658-4b31-93a9-85f74225ba05
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4f1ecb48b11d69e23bb6dba81a3663515059a274
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="firstchild-mdx"></a>FirstChild (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
