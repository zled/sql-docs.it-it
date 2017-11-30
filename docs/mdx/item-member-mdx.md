---
title: Elemento (membro) (MDX) | Documenti Microsoft
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
f1_keywords: ITEM
dev_langs: kbMDX
helpviewer_keywords: Item function
ms.assetid: 71cca249-910b-4ecd-9097-1a17b224e219
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5fbcaf01e9b7bba68d44908d28d4a3458fbc2a2b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
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
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
