---
title: TopCount (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: beded06a7951d51ce4d0a46d8ae41f049ff0426f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581313"
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
  
## <a name="remarks"></a>Remarks  
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
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
