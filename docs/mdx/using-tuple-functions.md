---
title: Utilizzo di funzioni di tupla | Documenti Microsoft
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
- tuple functions
ms.assetid: fe41e3e5-a675-4169-a966-b42c18e8d741
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b92f048f50f26d6ba5c98e28193a44a68e3ceb39
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="using-tuple-functions"></a>Utilizzo delle funzioni di tupla
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Una funzione di tupla recupera una tupla da un set o mediante la risoluzione della rappresentazione stringa di una tupla.  
  
 Le funzioni di tupla, come le funzioni membro e le funzioni sui set, sono essenziali per la negoziazione delle strutture multidimensionali che si trovano in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Esistono tre funzioni di tupla MDX, [corrente &#40; MDX &#41; ](../mdx/current-mdx.md), [Elemento &#40; Tupla &#41; &#40; MDX &#41; ](../mdx/item-tuple-mdx.md) e [StrToTuple &#40; MDX &#41; ](../mdx/strtotuple-mdx.md). Nell'esempio di query seguente viene illustrato l'utilizzo di ciascuna di queste funzioni:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; La sintassi MDX &#41;](../mdx/functions-mdx-syntax.md)   
 [Utilizzo delle funzioni membro](../mdx/using-member-functions.md)   
 [Utilizzo di Set di funzioni](../mdx/using-set-functions.md)  
  
  

