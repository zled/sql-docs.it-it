---
title: PeriodsToDate (MDX) | Documenti Microsoft
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
- PERIODSTODATE
dev_langs:
- kbMDX
helpviewer_keywords:
- PeriodsToDate function
ms.assetid: 43b9f69c-7b8c-4de0-9c4b-778ae766f74e
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: be11ebe09b2aeff73264708c83d820eeaffd009e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="periodstodate-mdx"></a>PeriodsToDate (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un set di membri di pari livello dallo stesso livello di un membro dato, iniziando dal primo membro di pari livello e terminando con il membro dato, in base al vincolo imposto dal livello specificato della dimensione temporale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PeriodsToDate( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 All'interno dell'ambito del livello specificato, il **PeriodsToDate** funzione restituisce il set di periodi allo stesso livello del membro specificato, a partire dal primo periodo e fino al membro specificato.  
  
-   Se si specifica un livello, viene derivato il membro corrente della gerarchia *gerarchia*. **CurrentMember**, dove *gerarchia*è la gerarchia del livello specificato.  
  
-   Se non è specificato un livello né un membro, come livello viene considerato il livello padre del membro corrente della prima gerarchia nella prima dimensione di tipo Time del gruppo di misure.  
  
 Dal punto di vista funzionale `PeriodsToDate( Level_Expression, Member_Expression )` equivale all'espressione MDX seguente:  
  
 `TopCount(Descendants(Ancestor(Member_Expression, Level_Expression), Member_Expression.Level), 1):Member_Expression`  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [TopCount &#40;MDX&#41;](../mdx/topcount-mdx.md)   
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
