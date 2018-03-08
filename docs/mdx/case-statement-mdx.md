---
title: Istruzione CASE (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: statements [MDX], CASE
ms.assetid: 0aee3b4a-d5f7-4c9a-87b8-e5efc2da6b6d
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: a4dbcc7ab42a0e044be0c7561adff4049fd8d1b9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="case-statement-mdx"></a>Istruzione CASE (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Consente di restituire valori specifici da più confronti in base a condizioni specifiche. Esistono due tipi di istruzioni CASE:  
  
-   Un'istruzione CASE semplice che esegue un confronto tra un'espressione e un set di espressioni semplici per restituire valori specifici.  
  
-   Un'istruzione CASE avanzata che valuta un set di espressioni booleane per restituire valori specifici.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Simple Case Statement  
CASE [input_expression]  
WHEN when_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
  
Search Case Statement  
CASE   
WHEN Boolean_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
```  
  
## <a name="arguments"></a>Argomenti  
 *input_expression*  
 Espressione MDX (Multidimensional Expression) che viene risolta in valore scalare.  
  
 *when_expression*  
 Valore scalare rispetto al quale specificato il *input_expression* viene valutata, che, quando valutata come true, restituisce il valore scalare del *else_result_expression*.  
  
 *when_true_result_expression*  
 Valore scalare restituito quando la clausola WHEN restituisce true.  
  
 *else_result_expression*  
 Valore scalare restituito quando nessuna delle clausole WHEN restituisce true.  
  
 *Espressione Boolean_expression*  
 Espressione MDX che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Se non ci sono clausole ELSE e tutte le clausole WHEN restituiscono False, il risultato sarà una cella vuota.  
  
## <a name="simple-case-expression"></a>Espressione CASE semplice  
 MDX valuta un'espressione case semplice risolvendo il *input_expression* su un valore scalare. Questo valore scalare viene quindi confrontato con il valore scalare del *when_expression*. Se i due valori scalari corrispondono, l'istruzione CASE restituisce il valore della *when_true_expression*. Se i due valori scalari non corrispondono, viene valutata la clausola WHEN successiva. Se tutte le clausole WHEN restituiscono false, il valore di *else_result_expression* dalla clausola ELSE, se presente, viene restituito.  
  
 Nell'esempio seguente, la misura Reseller Order Count viene valutata in base a diverse clausole WHEN e restituisce un risultato basato sul valore della misura Reseller Order Count per ogni anno. Per i valori di Reseller Order Count che non corrispondono a un valore scalare specificato in un *when_expression* in una clausola WHEN, il valore scalare del *else_result_expression* viene restituito.  
  
```  
WITH MEMBER [Measures].x AS   
CASE [Measures].[Reseller Order Count]  
   WHEN 0 THEN 'NONE'  
   WHEN 1 THEN 'SMALL'  
   WHEN 2 THEN 'SMALL'  
   WHEN 3 THEN 'MEDIUM'  
   WHEN 4 THEN 'MEDIUM'  
   WHEN 5 THEN 'LARGE'  
   WHEN 6 THEN 'LARGE'  
      ELSE 'VERY LARGE'  
END  
SELECT Calendar.[Calendar Year] on 0  
, NON EMPTY [Geography].[Postal Code].Members ON 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="searched-case-expression"></a>Espressione CASE avanzata  
 Per utilizzare l'espressione CASE per eseguire valutazioni più complesse, utilizzare l'espressione CASE avanzata. Questa variante dell'espressione di ricerca consente di valutare se un'espressione di input è compresa in un intervallo di valori. Nel linguaggio MDX le clausole WHEN vengono valutate nell'ordine in cui si presentano nell'istruzione CASE.  
  
 Nell'esempio seguente, la misura Reseller Order Count viene valutata rispetto al messaggio specificato *argomento Boolean_expression* per ognuna di più clausole WHEN. Viene restituito un risultato basato sul valore della misura Reseller Order Count per ogni anno. Poiché le clausole WHEN sono valutate nell'ordine in cui vengono visualizzate, è possibile assegnare a tutti i valori superiori a 6 il valore "VERY LARGE" senza dover specificare ogni valore in modo esplicito. Per i valori di Reseller Order Count che non sono specificati in una clausola WHEN, il valore scalare del *else_result_expression* viene restituito.  
  
```  
WITH MEMBER [Measures].x AS   
CASE   
   WHEN [Measures].[Reseller Order Count] > 6 THEN 'VERY LARGE'  
   WHEN [Measures].[Reseller Order Count] > 4 THEN 'LARGE'  
   WHEN [Measures].[Reseller Order Count] > 2 THEN 'MEDIUM'  
   WHEN [Measures].[Reseller Order Count] > 0 THEN 'SMALL'  
   ELSE "NONE"  
END  
SELECT Calendar.[Calendar Year] on 0,  
NON EMPTY [Geography].[Postal Code].Members on 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni di Scripting MDX &#40; MDX &#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
