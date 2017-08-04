---
title: Utilizzo di espressioni scalari | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- scalar expressions
- expressions [MDX], scalar
ms.assetid: 4678b675-8fbd-4e5b-a519-d4cd1bb8c46a
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 67966680e10b35064c65a91f8b8da22a00fb17c4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="using-scalar-expressions"></a>Utilizzo di espressioni scalari
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Nel linguaggio MDX (Multidimensional Expressions) un'espressione scalare è un elemento della sintassi MDX che, quando viene valutato, restituisce un valore singolo nel contesto di valutazione.  
  
 In MDX le espressioni scalari includono espressioni stringa, numeriche o di data.  
  
 Le espressioni scalari vengono in genere utilizzate nelle definizioni di membri calcolati, poiché i membri calcolati devono restituire un valore scalare. Nella query seguente vengono illustrati esempi di membri calcolati sulla dimensione Measures che utilizzano tipi diversi di espressione scalare:  
  
 `WITH`  
  
 `MEMBER MEASURES.NumericValue AS 10`  
  
 `MEMBER MEASURES.NumericExpression AS 10 + 10`  
  
 `MEMBER MEASURES.NumericExpressionBasedOnMeasure AS [Measures].[Internet Sales Amount] + 10`  
  
 `MEMBER MEASURES.StringValue AS "10"`  
  
 `MEMBER MEASURES.ConcatenatedString AS "10" + "10"`  
  
 `MEMBER MEASURES.StringFunction AS MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.TodaysDate AS NOW()`  
  
 `SELECT`  
  
 `{MEASURES.NumericValue,MEASURES.NumericExpression,MEASURES.NumericExpressionBasedOnMeasure,`  
  
 `MEASURES.StringValue, MEASURES.ConcatenatedString, MEASURES.StringFunction, MEASURES.TodaysDate}`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 L'unico tipo di dati solo che una misura, calcolata o non, può restituire è il tipo OLE Variant. Qualche volta potrebbe essere pertanto necessario eseguire il cast di un valore della misura a un particolare tipo per ottenere il comportamento desiderato. Nella query seguente viene illustrato un esempio di questa situazione:  
  
```  
WITH  
//Two calculated measures that return strings  
MEMBER MEASURES.NumericString1 AS "10"  
MEMBER MEASURES.NumericString2 AS "10"  
//In this case, the + operator acts to concatenate the strings  
MEMBER MEASURES.Concatenation AS MEASURES.NumericString1 + MEASURES.NumericString2  
//Casting one value to an integer with the CINT function causes the second measure  
//to be treated as an integer too, so that the + operator now acts to add the values  
MEMBER MEASURES.Addition AS CINT(MEASURES.NumericString1) + MEASURES.NumericString2  
SELECT  
{MEASURES.NumericString1,MEASURES.NumericString2,MEASURES.Concatenation,MEASURES.Addition }  
ON COLUMNS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; MDX &#41;](../mdx/expressions-mdx.md)  
  
  

