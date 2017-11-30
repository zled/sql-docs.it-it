---
title: Utilizzo di dimensione, gerarchia e funzioni di livello | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- dimensions [Analysis Services], functions
- level functions [MDX]
- hierarchy functions [MDX]
ms.assetid: e730f65a-1798-4094-9acf-2739e2505d52
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 897542151530a6ab1a82be79fdb8453349898ddf
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Utilizzo di funzioni per dimensioni, gerarchie e livelli
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Le funzioni per dimensioni, gerarchie e livelli consentono di attraversare le strutture multidimensionali utilizzate Analysis Services. Tali funzioni vengono in genere utilizzate insieme ad altre funzioni, per ottenere informazioni sui membri di una dimensione, di una gerarchia o di un livello.  
  
 Nell'esempio seguente viene illustrato come utilizzare il **. Dimensione**, **. Gerarchia**, e **. Livello** funzioni:  
  
 `WITH`  
  
 `MEMBER MEASURES.DIMENSIONNAME AS [Date].[Calendar].CURRENTMEMBER.DIMENSION.NAME`  
  
 `MEMBER MEASURES.HIERARCHYNAME AS [Date].[Calendar].CURRENTMEMBER.HIERARCHY.NAME`  
  
 `MEMBER MEASURES.LEVELNAME AS [Date].[Calendar].LEVEL.NAME`  
  
 `SELECT`  
  
 `{MEASURES.DIMENSIONNAME, MEASURES.HIERARCHYNAME, MEASURES.LEVELNAME}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Dimensione &#40; MDX &#41;](../mdx/dimension-mdx.md)   
 [Funzioni &#40; La sintassi MDX &#41;](../mdx/functions-mdx-syntax.md)   
 [Gerarchia &#40; MDX &#41;](../mdx/hierarchy-mdx.md)   
 [Livello &#40; MDX &#41;](../mdx/level-mdx.md)  
  
  
