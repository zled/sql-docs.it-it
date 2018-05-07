---
title: Elemento (membro) (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ITEM
dev_langs:
- kbMDX
helpviewer_keywords:
- Item function
ms.assetid: 71cca249-910b-4ecd-9097-1a17b224e219
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 48944238630565e6a8655cb10a3f6c7d8adddbdf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="item-member-mdx"></a>Item (Member) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un membro da una tupla specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Tuple_Expression.Item( Index )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Tuple_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una tupla.  
  
 *Index*  
 Espressione numerica valida che specifica il membro specifico in base alla posizione nella tupla da restituire.  
  
## <a name="remarks"></a>Osservazioni  
 Il **elemento** funzione restituisce un membro della tupla specificata. La funzione restituisce il membro trovato in corrispondenza della posizione in base zero specificata da *indice*.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il membro `[2003]`, ovvero il primo elemento nella tupla `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).`, nelle colonne:  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
