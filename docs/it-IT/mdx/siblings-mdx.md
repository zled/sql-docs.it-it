---
title: Elementi di pari livello (MDX) | Documenti Microsoft
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
- SIBLINGS
dev_langs:
- kbMDX
helpviewer_keywords:
- Siblings function
ms.assetid: 33e63808-f07e-44f7-8dfa-4dd9fd89ec82
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: d13c8b6ea2811e5bd6b7f4e0f8748b6fbb9ef0d3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="siblings-mdx"></a>Siblings (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce i membri di pari livello di un membro specificato, incluso il membro stesso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Siblings   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la misura predefinita per gli elementi di pari livello rispetto al mese di marzo 2003, ovvero gennaio 2003, febbraio 2003 e lo stesso marzo 2003.  
  
```  
SELECT [Date].[Calendar].[Month].[March 2003].Siblings ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
