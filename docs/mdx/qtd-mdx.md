---
title: QTD (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Qtd function
ms.assetid: c1fe47e0-9c2b-466f-8d6d-e2b1c16a69cb
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d4fcbfa3ac5c02dc04181bb32c8baca10a56fa0e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="qtd-mdx"></a>Qtd (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce i membri di un set di pari livello dallo stesso livello di un membro dato, iniziando con il primo elemento di pari livello e terminando con il membro specificato, come vincolo imposto dal *trimestre* livello nella dimensione temporale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Se expressionis di membro non è specificato, il valore predefinito è il membro corrente della prima gerarchia con un livello di tipo *trimestri* nella prima dimensione di tipo *ora* nel gruppo di misure.  
  
 Il **Qtd** è una funzione di scelta rapida per il [PeriodsToDate &#40; MDX &#41; ](../mdx/periodstodate-mdx.md) funzione il cui argomento di espressione di livello è impostato su *trimestre*. In altre parole, dal punto di vista funzionale `Qtd(Member_Expression)` equivale a `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
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
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

