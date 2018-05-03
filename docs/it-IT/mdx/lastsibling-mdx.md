---
title: LastSibling (MDX) | Documenti Microsoft
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
- LASTSIBLING
dev_langs:
- kbMDX
helpviewer_keywords:
- LastSibling function
ms.assetid: 05542812-4bdb-48bf-823e-065d105b1721
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b6e40b50474603a8ad989b39692989961bb9c5e7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lastsibling-mdx"></a>LastSibling (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce l'ultimo membro figlio del padre di un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.LastSibling   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la misura predefinita per l'ultimo giorno di luglio 2002.  
  
```  
SELECT [Date].[Fiscal].[Date].&[20020717].LastSibling   
   ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
