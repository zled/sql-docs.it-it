---
title: NextMember (MDX) | Documenti Microsoft
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
- NEXTMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- NextMember function
ms.assetid: f67be3d0-082e-4bec-92e4-ba6ff33af303
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f1cd2b67e3ec633992ccae294b823128bfb5a2ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="nextmember-mdx"></a>NextMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il membro successivo nel livello contenente il membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.NextMember   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Il **NextMember** funzione restituisce il membro successivo nello stesso livello, che contiene il membro specificato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il membro August 2001 come membro successivo del membro July 2001.  
  
```  
SELECT [Date].[Calendar].[Month].[July 2001].NextMember ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
