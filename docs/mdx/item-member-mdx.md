---
title: Elemento (membro) (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4c2649598e6224c3458dfa0b0278df8d6458b7ce
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="item-member-mdx"></a>Item (Member) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un membro da una tupla specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Tuple_Expression.Item( Index )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Tuple_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una tupla.  
  
 *Indice*  
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
  
  

