---
title: TopCount (MDX) | Documenti Microsoft
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
f1_keywords: TOPCOUNT
dev_langs: kbMDX
helpviewer_keywords: TopCount function
ms.assetid: 15026a8f-35c5-4307-8856-348f5c44bfd5
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 597faa6bfe343a0a1329dfc0dd75be5a1f785491
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="topcount-mdx"></a>TopCount (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dispone un set in ordine decrescente e restituisce il numero specificato di elementi con i valori più alti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Conteggio*  
 Espressione numerica valida che specifica il numero di tuple che devono essere restituite.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificata un'espressione numerica, la **TopCount** funzione dispone in ordine decrescente, le tuple nel set specificato per il set specificato in base al valore specificato dall'espressione numerica, valutato sul set specificato. Dopo l'ordinamento, il set di **TopCount** funzione restituisce quindi il numero specificato di tuple con valore più alto.  
  
> [!IMPORTANT]  
>  Ad esempio il [BottomCount](../mdx/bottomcount-mdx.md) funzione, il **TopCount** funzione rispetta mai la gerarchia.  
  
 Se un'espressione numerica non è specificata, la funzione restituisce il set di membri in ordine naturale, senza alcun ordinamento, analogamente il [Head (MDX)](../mdx/head-mdx.md) (funzione).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite le prime 10 date da Internet Sales Amount:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 Nell'esempio seguente vengono restituiti, per la categoria Bike, i primi cinque elementi nel set contenente tutte le combinazioni di membri del livello City nella gerarchia Geography della dimensione Geography e tutti gli anni fiscali nella gerarchia Fiscal della dimensione Date, ordinati in base alla misura Reseller Sales Amount (a partire dai membri di questo set con il numero di vendite più elevato).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
