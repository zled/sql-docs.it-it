---
title: Funzione di aggregazione (MDX) | Documenti Microsoft
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
f1_keywords: AGGREGATE
dev_langs: kbMDX
helpviewer_keywords: Aggregate function
ms.assetid: 9d5e0966-74d1-4cc8-b9f9-47e4dc65d165
caps.latest.revision: "52"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 6e0905531658202c86ef5deac9e20d4db36fd9d6
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="aggregate-mdx"></a>Aggregate (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un numero che viene calcolato mediante aggregazione sulle celle restituite dall'espressione set. Se non si specifica un'espressione numerica, questa funzione consente di aggregare ogni misura nel contesto di query corrente utilizzando l'operatore di aggregazione predefinito specificato per ogni misura. Se viene specificata un'espressione numerica, questa funzione innanzitutto valuta e quindi somma l'espressione numerica per ogni cella nel set specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Aggregate(Set_Expression [ ,Numeric_Expression ])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Se è specificato un set di tuple vuote o un set vuoto, la funzione restituisce un valore vuoto.  
  
 La tabella seguente descrive come **aggregazione** il comportamento della funzione con le funzioni di aggregazione diversa.  
  
|Operatore di aggregazione|Risultato|  
|--------------------------|------------|  
|Sum|Restituisce la somma dei valori all'interno del set.|  
|Count|Restituisce il conteggio dei valori all'interno del set.|  
|Max|Restituisce il valore massimo all'interno del set.|  
|Min|Restituisce il valore minimo all'interno del set.|  
|Funzioni di aggregazione semiadditive|Restituisce il calcolo delle funzioni semiadditive all'interno del set dopo la proiezione della forma sull'asse dei tempi.|  
|Distinct Count|Aggrega i dati della tabella dei fatti che contribuiscono al sottocubo quando l'asse di sezionamento include un set.<br /><br /> Restituisce la misura Distinct Count per ogni membro del set. Il risultato dipende dalla sicurezza delle celle aggregate e non dalla sicurezza delle celle necessarie per il calcolo. La sicurezza delle celle all'interno del set genera un errore, mentre la sicurezza delle celle al di sotto della granularità del set specificato viene ignorata. I calcoli sul set generano un errore. I calcoli al di sotto della granularità del set vengono ignorati. L'operatore Distinct Count su un set che include un membro e uno o più dei relativi figli restituisce la misura Distinct Count per i fatti che contribuiscono al membro figlio.|  
|Attributi che non possono essere aggregati|Restituisce la somma dei valori.|  
|Funzioni di aggregazione miste|Non supportate. Viene generato un errore.|  
|Operatori unari|Non rispettati. I valori vengono aggregati tramite somma.|  
|Misure calcolate|L'ordine di valutazione viene impostato in modo da garantire l'applicazione della misura calcolata.|  
|Membri calcolati|Vengono applicate le regole normali, ovvero l'ultimo ordine di valutazione ha la precedenza.|  
|Assegnazioni|L'aggregazione delle assegnazioni viene eseguita in base alla funzione di aggregazione delle misure. Se la funzione di aggregazione delle misure è Distinct Count, l'assegnazione viene sommata.|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente restituisce la somma del `Measures.[Order Quantity]` membro, aggregato sui primi otto mesi dell'anno di calendario 2003 contenuti nel `Date` dimensione, dal **Adventure Works** cubo.  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 Nell'esempio seguente i dati vengono aggregati sui primi due mesi del secondo semestre dell'anno di calendario 2003.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 Nell'esempio seguente viene restituito il numero dei rivenditori le cui vendite sono diminuite nel periodo di tempo precedente, in base ai valori del membro State-Province selezionati dall'utente valutati tramite la funzione di aggregazione. Il **Hierarchize** e **DrillDownLevel** vengono utilizzate per restituire i valori relativi alla diminuzione delle vendite per le categorie di prodotti nella dimensione Product.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS   
   Count(  
      Filter(  
         Existing(Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
            )  
         )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate (   
      {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
         )  
SELECT NON EMPTY Hierarchize (  
   AddCalculatedMembers (  
      {DrillDownLevel({[Product].[All Products]})}  
         )  
   )  
        DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
    [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
    [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [PeriodsToDate &#40; MDX &#41;](../mdx/periodstodate-mdx.md)   
 [Gli elementi figlio &#40; MDX &#41;](../mdx/children-mdx.md)   
 [HIERARCHIZE &#40; MDX &#41;](../mdx/hierarchize-mdx.md)   
 [Numero &#40; Set &#41; &#40; MDX &#41;](../mdx/count-set-mdx.md)   
 [Filtro &#40; MDX &#41;](../mdx/filter-mdx.md)   
 [AddCalculatedMembers &#40; MDX &#41;](../mdx/addcalculatedmembers-mdx.md)   
 [DrilldownLevel &#40; MDX &#41;](../mdx/drilldownlevel-mdx.md)   
 [Proprietà &#40; MDX &#41;](../mdx/properties-mdx.md)   
 [PrevMember &#40; MDX &#41;](../mdx/prevmember-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
