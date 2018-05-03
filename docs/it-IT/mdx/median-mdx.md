---
title: Valore mediano (MDX) | Documenti Microsoft
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
- MEDIAN
dev_langs:
- kbMDX
helpviewer_keywords:
- Median function
ms.assetid: 7a326a3f-0123-45c4-9b18-31f83b90d986
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: dbe31042708d3c4cb4f78c4f5cc291ecf5684a33
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="median-mdx"></a>Median (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce la mediana di un'espressione numerica valutata su un set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Median(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Se si specifica un'espressione numerica, questa viene valutata sull'intero set e restituisce il valore mediano di tale valutazione. Se non viene specificata un'espressione numerica, il set specificato viene valutato nel contesto corrente dei membri del set e viene restituito il valore mediano di tale valutazione.  
  
 Il valore mediano è il valore centrale di un set di numeri ordinati ed è diverso dal valore medio. Mentre il valore medio corrisponde alla somma di un set di numeri divisa per il conteggio dei numeri del set, il valore mediano corrisponde al valore più piccolo rispetto ad almeno metà dei valori del set. Se il numero di valori del set è dispari, il valore mediano corrisponde a un singolo valore. Se invece il numero di valori del set è pari, corrisponde alla somma dei due valori centrali divisa per due.  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignora i valori Null durante il calcolo del valore medio di un set di numeri ordinati.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il valore mediano mensile delle vendite per ogni trimestre, sottocategoria e paese del cubo Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Median   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
