---
title: Esiste (MDX) | Documenti Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- Exists function
ms.assetid: 1e1d93b5-5be6-421c-b82b-839538ea50b1
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 2adc9ae709257cc3d44496e9ad4c7d078b76cb92
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="exists-mdx"></a>Exists (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il set di tuple del primo set specificato in cui esiste almeno una tupla del secondo set specificato. Questa funzione consente di eseguire manualmente ciò che la funzione Auto Exist esegue automaticamente. Per ulteriori informazioni su auto esistono, vedere [concetti chiave di MDX &#40; Analysis Services &#41; ](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
 Se l'opzione facoltativa \<nome gruppo misure > viene specificato, la funzione restituisce tuple in cui esistano almeno una tupla da un secondo set e le tuple cui sono associate righe della tabella dei fatti del gruppo di misure specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Exists( Set_Expression1 , Set_Expression2 [, MeasureGroupName] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *MeasureGroupName*  
 Espressione stringa valida che specifica il nome di un gruppo di misure.  
  
## <a name="remarks"></a>Remarks  
  
1.  Le righe di gruppo di misure con misure contenenti valori null contribuiscono a **Exists** quando è specificato l'argomento MeasureGroupName. Questa situazione rappresenta la differenza tra il form Exists e la funzione Nonempty. Se la proprietà NullProcessing di queste misure è impostata su Preserve, le misure visualizzeranno valori Null quando le query vengono eseguite sulla parte di cubo specifica. In questo caso la funzione NonEmpty rimuoverà sempre le tuple da un set con valori di misura Null, mentre Exists con l'argomento MeasureGroupName non filtrerà tuple che hanno associato righe del gruppo di misure, anche se i valori di misura sono Null.  
  
2.  Se *MeasureGroupName* parametro viene utilizzato, i risultati dipenderanno se sono presenti misure visibili nel gruppo di misure a cui fa riferimento; se non sono disponibili misure visibili nel gruppo di misure di cui viene fatto riferimento, EXISTS restituisce sempre un set vuoto, indipendentemente dai valori di *Set_Expression1* e *Set_Expression2*.  
  
## <a name="examples"></a>Esempi  
 Clienti che vivono in California:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
) ON 1   
FROM [Adventure Works]  
  
```  
  
 Clienti che vivono in California con vendite:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 Clienti con vendite:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, , "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 Clienti che hanno acquistato biciclette:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Product].[Product Categories].[Category].&[1]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Crossjoin &#40; MDX &#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40; MDX &#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [NonEmpty &#40; MDX &#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40; MDX &#41;](../mdx/isempty-mdx.md)  
  
  
