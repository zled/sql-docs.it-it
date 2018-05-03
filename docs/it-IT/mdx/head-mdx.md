---
title: Head (MDX) | Documenti Microsoft
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
- HEAD
dev_langs:
- kbMDX
helpviewer_keywords:
- Head function
ms.assetid: 2a909bda-1366-4537-93b0-c089554fc11f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5529333ef2e81b8fee7d78765e0fb528ecb02577
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="head-mdx"></a>Head (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il primo numero specificato di elementi in un set, mantenendo i duplicati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Head(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Count*  
 Espressione numerica valida che specifica il numero di tuple che devono essere restituite.  
  
## <a name="remarks"></a>Osservazioni  
 Il **Head** funzione restituisce il numero di tuple specificato dall'inizio del set specificato. L'ordine degli elementi viene mantenuto. Il valore predefinito di Count è 1. Se il numero specificato di tuple è minore di 1, il **Head** funzione restituisce un set vuoto. Se il numero di tuple specificato supera il numero di tuple nel set, la funzione restituisce il set originale.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituite le cinque sottocategorie di prodotti più vendute, indipendentemente dalla gerarchia, in base al profitto lordo del rivenditore. Il **Head** funzione viene utilizzata per restituire solo i primi 5 set del risultato dopo l'ordinamento del risultato mediante la **ordine** (funzione).  
  
```  
SELECT   
[Measures].[Reseller Gross Profit] ON 0,  
Head  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,5  
   ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Della parte finale del &#40;MDX&#41;](../mdx/tail-mdx.md)   
 [Elemento &#40;tupla&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md)   
 [Elemento &#40;membro&#41; &#40;MDX&#41;](../mdx/item-member-mdx.md)   
 [Numero di dimensioni &#40;MDX&#41;](../mdx/rank-mdx.md)   
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  