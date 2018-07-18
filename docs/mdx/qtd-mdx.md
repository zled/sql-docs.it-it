---
title: QTD (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 182a86a05cd0dae6adf85d2168fe884ace910a82
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742590"
---
# <a name="qtd-mdx"></a>Qtd (MDX)


  Restituisce i membri di un set di pari livello dallo stesso livello di un membro dato, iniziando con il primo elemento di pari livello e terminando con il membro specificato, come vincolo imposto dal *trimestre* livello nella dimensione temporale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Se expressionis di membro non è specificato, il valore predefinito è il membro corrente della prima gerarchia con un livello di tipo *trimestri* nella prima dimensione di tipo *ora* nel gruppo di misure.  
  
 Il **Qtd** è una funzione di scelta rapida per il [PeriodsToDate &#40;MDX&#41; ](../mdx/periodstodate-mdx.md) funzione il cui argomento di espressione di livello è impostato su *trimestre*. In altre parole, dal punto di vista funzionale `Qtd(Member_Expression)` equivale a `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente restituisce la somma del `Measures.[Order Quantity]` membro, aggregato sui primi due mesi del terzo trimestre dell'anno di calendario 2003 contenuti nel `Date` dimensione, dal **Adventure Works** cubo.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        QTD([Date].[Calendar].[Month].[August 2003])  
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
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
