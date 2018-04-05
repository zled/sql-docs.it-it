---
title: Elemento (tupla) (MDX) | Documenti Microsoft
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
- ITEM
dev_langs:
- kbMDX
helpviewer_keywords:
- Item function
ms.assetid: 9ee7af55-d5b5-47c8-a480-ef23878306af
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9c7e727908bbd2265cab05b9d1aa2f55cc7b9ebd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="item-tuple-mdx"></a>Item (Tuple) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce una tupla da un set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Index syntax  
Set_Expression.Item(Index)  
  
String expression syntax  
Set_Expression.Item(String_Expression1 [ ,String_Expression2,...n])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *String_Expression1*  
 Espressione stringa valida che in genere è una tupla espressa come stringa.  
  
 *String_Expression2*  
 Espressione stringa valida che in genere è una tupla espressa come stringa.  
  
 *Index*  
 Espressione numerica valida che specifica la tupla in base alla posizione all'interno del set da restituire.  
  
## <a name="remarks"></a>Remarks  
 Il **elemento** funzione restituisce una tupla dal set specificato. Esistono tre modi per chiamare il **elemento** funzione:  
  
-   Se si specifica una singola espressione stringa, il **elemento** funzione restituisce la tupla specificata. ad esempio "([2005].Q3, [Store05])".  
  
-   Se è specificata più di un'espressione stringa, il **elemento** funzione restituisce la tupla definita dalle coordinate specificate. Il numero di stringhe deve corrispondere al numero di assi e ogni stringa deve identificare una gerarchia univoca, ad esempio "[2005].Q3", "[Store05]".  
  
-   Se viene specificato un numero intero, il **elemento** funzione restituisce la tupla che si trova nella posizione in base zero specificata da *indice*.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito ([1996],Sales):  
  
 `{([1996],Sales), ([1997],Sales), ([1998],Sales)}.Item(0)`  
  
 Nell'esempio seguente viene utilizzata un'espressione di livello e vengono restituiti l'importo delle vendite su Internet per ogni State-Province in Australia e la relativa percentuale sul totale delle vendite su Internet per l'Australia. In questo esempio la funzione Item viene utilizzata per estrarre il primo e unica tupla, il set restituito dal **predecessori** (funzione).  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],    
      Ancestors   
      ( [Customer].[Customer Geography].CurrentMember,  
        [Customer].[Customer Geography].[Country]  
      ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{ Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],  
     [Customer].[Customer Geography].[State-Province], SELF   
   )   
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
