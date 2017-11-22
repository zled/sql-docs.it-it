---
title: NonEmpty (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: NonEmpty function
ms.assetid: dfbfa747-3175-405c-aa5b-15c187b06338
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: df0650ada514d4b5bf33202b572d0e1a316120da
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="nonempty-mdx"></a>NonEmpty (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il set delle tuple non vuote da un set specificato, in base al prodotto incrociato tra il set specificato e un secondo set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NONEMPTY(set_expression1 [,set_expression2])  
```  
  
## <a name="arguments"></a>Argomenti  
 *set_expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *set_expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione restituisce le tuple del primo set specificato che risultano non vuote quando vengono valutate sulle tuple del secondo set. Il **NonEmpty** funzione tiene conto dei calcoli e mantiene le tuple duplicate. Se non viene specificato un secondo set, l'espressione viene valutata nel contesto delle coordinate correnti dei membri delle gerarchie degli attributi e delle misure del cubo.  
  
> [!NOTE]  
>  Utilizzare questa funzione anziché deprecate [NonEmptyCrossjoin &#40; MDX &#41; ](../mdx/nonemptycrossjoin-mdx.md) (funzione).  
  
> [!IMPORTANT]  
>  Non sono le tuple a essere non vuote, bensì le celle a cui fanno riferimento le tuple.  
  
## <a name="examples"></a>Esempi  
 La query seguente viene illustrato un esempio semplice di **NonEmpty**, restituisce tutti i clienti che hanno un valore non null per Internet Sales Amount in data 1 luglio 2001:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 L'esempio seguente restituisce il set di tuple contenente i clienti e le date di acquisto, utilizzando il **filtro** funzione e **NonEmpty** funzioni per consentirti di individuare l'ultima data di ogni cliente che ha eseguito un acquisto:  
  
 `WITH SET MYROWS AS FILTER`  
  
 `(NONEMPTY`  
  
 `([Customer].[Customer Geography].[Customer].MEMBERS`  
  
 `* [Date].[Date].[Date].MEMBERS`  
  
 `, [Measures].[Internet Sales Amount]`  
  
 `) AS MYSET`  
  
 `, NOT(MYSET.CURRENT.ITEM(0)`  
  
 `IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))`  
  
 `)`  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `MYROWS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [DefaultMember &#40; MDX &#41;](../mdx/defaultmember-mdx.md)   
 [Filtro &#40; MDX &#41;](../mdx/filter-mdx.md)   
 [IsEmpty &#40; MDX &#41;](../mdx/isempty-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin &#40; MDX &#41;](../mdx/nonemptycrossjoin-mdx.md)  
  
  
