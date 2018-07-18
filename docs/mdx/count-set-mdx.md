---
title: Conteggio (Set) (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4da622ef883ed1fabba137b0d30adcbdd7e32ded
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577603"
---
# <a name="count-set-mdx"></a>Count (Set) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il numero di celle in un set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Standard syntax  
Count(Set_Expression [ , ( EXCLUDEEMPTY | INCLUDEEMPTY ) ] )  
  
Alternate syntax  
Set_Expression.Count  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Remarks  
 Il **conteggio (Set)** funzione include o esclude le celle vuote, a seconda della sintassi utilizzata. Se viene utilizzata la sintassi standard, le celle vuote escluse o incluse utilizzando il **EXCLUDEEMPTY** o **INCLUDEEMPTY** flag, rispettivamente. Se si utilizza la sintassi alternativa, la funzione includerà sempre le celle vuote.  
  
 Per escludere le celle vuote nel conteggio di un set, usare la sintassi standard e il parametro facoltativo **EXCLUDEEMPTY** flag.  
  
> [!NOTE]  
>  Il **conteggio (Set)** funzione consente di contare le celle vuote per impostazione predefinita. Al contrario, il **conteggio** funzione in OLE DB che conta un set esclude le celle vuote per impostazione predefinita.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene contato il numero di celle nel set di membri che comprende i figli della gerarchia dell'attributo Model Name nella dimensione Product.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente conta il numero di prodotti nella dimensione Product utilizzando la **DrilldownLevel** funzione in combinazione con il **conteggio** (funzione).  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 L'esempio seguente restituisce i rivenditori con alla diminuzione delle vendite rispetto al trimestre di calendario precedente, utilizzando il **conteggio** funzione in combinazione con il **filtro** (funzione) e un numero di altre funzioni. Questa query utilizza la **aggregazione** funzione per supportare la selezione di più membri dell'area geografica, ad esempio la selezione da un elenco a discesa in un'applicazione client.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
   (Filter  
      (Existing(Reseller.Reseller.Reseller),  
         [Measures].[Reseller Sales Amount]   
         < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
      )  
   )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate  
   ( {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
   )  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})  
      })  
   ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,  
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
   ,[Measures].[Declining Reseller Sales])  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Conteggio &#40;dimensione&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Conteggio &#40;livelli di gerarchia&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Conteggio &#40;tupla&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [HIERARCHIZE- &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [Proprietà &#40;MDX&#41;](../mdx/properties-mdx.md)   
 [Aggregazione &#40;MDX&#41;](../mdx/aggregate-mdx.md)   
 [Filtro &#40;MDX&#41;](../mdx/filter-mdx.md)   
 [PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
