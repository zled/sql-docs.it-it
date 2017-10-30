---
title: SUM (MDX) | Documenti Microsoft
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
- SUM
dev_langs:
- kbMDX
helpviewer_keywords:
- Sum function [MDX]
ms.assetid: 6c3db1e3-2c02-49f2-a0bf-cab0fb78c622
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9825bd3230e2cc9e962d059e87a31f1e569ec8b8
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="sum-mdx"></a>Sum (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce la somma di un'espressione numerica valutata su un set specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Sum( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione set MDX (Multidimensional Expression) valida.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Se si specifica un'espressione numerica, questa viene valutata sull'intero set e quindi sommata. Se non viene specificata un'espressione numerica, il set specificato viene valutato nel contesto corrente dei membri del set e quindi sommato. Se la funzione SUM viene applicata a un'espressione non numerica, i risultati saranno indefiniti.  
  
> [!NOTE]  
>  Durante il calcolo della somma di un set di numeri, in Analysis Services vengono ignorati i valori Null.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la somma di Reseller Sales Amounts per tutti i membri della gerarchia di attributi Product.Category per gli anni di calendario 2001 e 2002.  
  
```  
WITH MEMBER Measures.x AS SUM  
   ( { [Date].[Calendar Year].&[2001]  
         , [Date].[Calendar Year].&[2002] }  
      , [Measures].[Reseller Sales Amount]  
    )  
SELECT Measures.x ON 0  
,[Product].[Category].Members ON 1  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene restituita la somma dei costi di spedizione delle vendite Internet per il mese di luglio 2002 fino al giorno 20 luglio.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 L'esempio seguente usa la parola chiave WITH MEMBER e **somma** (funzione) per definire un membro calcolato nella dimensione Measures che contiene la somma della misura Reseller Sales Amount per i membri Canada e United States della gerarchia dell'attributo Country nella dimensione Geography.  
  
```  
WITH MEMBER Measures.NorthAmerica AS SUM   
      (  
         {[Geography].[Country].&[Canada]  
            , [Geography].[Country].&[United States]}  
       ,[Measures].[Reseller Sales Amount]  
      )  
SELECT {[Measures].[NorthAmerica]} ON 0,  
[Product].[Category].members ON 1  
FROM [Adventure Works]  
```  
  
 Spesso, il **somma** funzione viene utilizzata con la **CURRENTMEMBER** funzione o funzioni analoghe **YTD** che restituiscono un set che varia a seconda dell'elemento currentmember di una gerarchia. Nella query seguente, ad esempio, viene restituita la somma della misura di Internet Sales Amount per tutte le date dall'inizio dell'anno di calendario alla data visualizzata sull'asse delle righe:  
  
 `WITH MEMBER MEASURES.YTDSUM AS`  
  
 `SUM(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDSUM} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

