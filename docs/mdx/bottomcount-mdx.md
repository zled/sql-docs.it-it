---
title: BottomCount (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: BOTTOMCOUNT
dev_langs: kbMDX
helpviewer_keywords: BottomCount function
ms.assetid: 1441dab3-7885-4e92-9d48-21d832286677
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8e86dcb2428468e7f187638efa03252489974a08
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="bottomcount-mdx"></a>BottomCount (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dispone un set in ordine crescente e restituisce il numero specificato di tuple nel set specificato con i valori più bassi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BottomCount(Set_Expression, Count [,Numeric_Expression])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Conteggio*  
 Espressione numerica valida che specifica il numero di tuple che devono essere restituite.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Se si specifica un'espressione numerica, la funzione dispone in ordine crescente le tuple nel set specificato in base al valore dell'espressione numerica specificata, valutato sul set. Il **BottomCount** funzione restituisce quindi il numero specificato di tuple con il valore più basso.  
  
> [!IMPORTANT]  
>  Il **BottomCount** funzione, come il [TopCount](../mdx/topcount-mdx.md) funzione, non rispetta mai la gerarchia.  
  
 Se un'espressione numerica non è specificata, la funzione restituisce il set di membri in ordine naturale, senza alcun ordinamento, analogamente il [Tail (MDX)](../mdx/tail-mdx.md) (funzione).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la misura Reseller Order Quantity per ogni anno di calendario per le cinque sottocategorie di prodotti meno vendute, ordinate in base alla misura Reseller Sales Amount.  
  
```  
SELECT BottomCount([Product].[Product Categories].[Subcategory].Members  
   , 10  
   , [Measures].[Reseller Sales Amount]) ON 0,  
   [Date].[Calendar].[Calendar Year].Members ON 1  
  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Reseller Order Quantity]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
