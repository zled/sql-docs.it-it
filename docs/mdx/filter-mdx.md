---
title: Filtro (MDX) | Documenti Microsoft
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
- filter
dev_langs:
- kbMDX
helpviewer_keywords:
- Filter function
ms.assetid: f2df51c8-6acb-4300-b71c-2a480c9fbdf8
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 729adc2230242798e67914907b6928ec7346b871
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="filter-mdx"></a>Filter (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il set risultante dal filtro di un set specificato in base a una condizione di ricerca.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Logical_Expression*  
 Espressione logica MDX (Multidimensional Expression) valida che restituisce true o false.  
  
## <a name="remarks"></a>Remarks  
 Il **filtro** funzione valuta l'espressione logica specificata rispetto a ogni tupla nel set specificato. La funzione restituisce un set costituito da ogni tupla nel set specificato in cui l'espressione logica restituisce **true**. Se nessuna tupla restituisce **true**, viene restituito un set vuoto.  
  
 Il **filtro** funzione funziona in modo simile a quello del [IIf](../mdx/iif-mdx.md) (funzione). Il **IIf** funzione restituisce solo una delle due opzioni in base alla valutazione di un'espressione logica MDX, mentre il **filtro** funzione restituisce un set di tuple che soddisfano la condizione di ricerca specificati. In effetti, il **filtro** funzione esegue `IIf(Logical_Expression, Set_Expression.Current, NULL)` su ogni tupla del set e restituisce il set risultante.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo della funzione Filter sull'asse Rows di una query, per restituire solo le date in cui Internet Sales Amount è maggiore di $10.000:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 La funzione Filter può essere utilizzata anche nelle definizioni di membri calcolati. Nell'esempio seguente restituisce la somma del `Measures.[Order Quantity]` membro, aggregato sui primi nove mesi del 2003 contenuti nella `Date` dimensione, dal **Adventure Works** cubo. Il **PeriodsToDate** funzione definisce le tuple del set su cui il **aggregazione** funzione viene eseguita. Il **filtro** funzione limita le tuple da restituire a quelli con i valori più bassi per la misura Reseller Sales Amount per il periodo di tempo precedente.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
