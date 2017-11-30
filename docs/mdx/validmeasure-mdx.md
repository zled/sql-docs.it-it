---
title: ValidMeasure (MDX) | Documenti Microsoft
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
f1_keywords: VALIDMEASURE
dev_langs: kbMDX
helpviewer_keywords: ValidMeasure function
ms.assetid: ecf20a86-c45e-4521-84ce-3a466e0c1136
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9309b0b62994e6d3199a7aa565d9edd2e88c5f73
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="validmeasure-mdx"></a>ValidMeasure (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il valore di una misura in un cubo forzando le dimensioni inapplicabili al livello Totale (o al membro predefinito se non aggregabile) al momento della restituzione del risultato per una tupla specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ValidMeasure(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Tuple_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una tupla.  
  
## <a name="remarks"></a>Osservazioni  
 Il **ValidMeasure** funzione restituisce il valore di una tupla, ignorando attributi alcuna relazione con il gruppo di misure della misura il cui valore restituisce la tupla. Un attributo può non essere correlato a una misura per i due motivi riportati di seguito:  
  
-   La dimensione dell'attributo non ha alcuna relazione con il gruppo di misure della misura nella tupla.  
  
-   La dimensione dell'attributo non ha alcuna relazione con il gruppo di misure della misura, ma l'attributo di granularità non è l'attributo chiave e l'attributo di granularità non ha alcuna relazione diretta con l'attributo nella tupla.  
  
 Il comportamento specificato da questa funzione sul lato server per impostazione predefinita ed è controllato dal **IgnoreUnrelatedDimensions** proprietà sull'oggetto gruppo di misure.  
  
 Per ogni attributo nella tupla specificata con granularità, ovvero in una tupla in cui il membro non corrisponde a quello Totale), la coordinata corrente viene spostata nel modo seguente:  
  
-   Gli attributi correlati al membro dell'attributo specificato vengono spostati al membro esistente con il membro corrente.  
  
-   Gli attributi che stabiliscono una correlazione con il membro dell'attributo specificato vengono spostati al membro Totale oppure al membro predefinito se la gerarchia non è aggregabile.  
  
-   Gli attributi non correlati vengono spostati al membro Totale (in base alla misura).  
  
## <a name="example"></a>Esempio  
 La query seguente illustra il modo in cui la funzione ValidMeasure può essere utilizzata per eseguire l'override del comportamento della proprietà IgnoreUnrelatedDimensions. Nel cubo Adventure Works la proprietà IgnoreUnrelatedDimensions del gruppo di misure Sales Targets è impostata su False. Poiché il join tra la dimensione Date e questo gruppo di misure viene eseguito a livello di granularità Calendar Quarter, per impostazione predefinita la misura Sales Quota restituirà Null sotto il valore Calendar Quarter, sebbene sia presente un calcolo nello script MDX che alloca valori oltre il livello Month. La funzione ValidMeasure può essere utilizzata in una misura calcolata per fare in modo che la misura Sales Quota si comporti come se la proprietà IgnoreUnrelatedDimensions fosse impostata su True e per imporre la visualizzazione del valore dell'elemento Calendar Quarter corrente.  
  
```  
WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])  
SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,  
[Date].[Calendar].MEMBERS ON 1  
FROM [Adventure Works]  
```  
  
 In modo analogo, poiché il gruppo di misure Sales Targets non ha alcuna relazione con la dimensione Promotion, sotto il membro Totale di ogni gerarchia relativa a Promotion restituirà Null. Come indicato in precedenza, questo comportamento può essere modificato tramite la funzione ValidMeasure:  
  
 `WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])`  
  
 `SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,`  
  
 `[Promotion].[Promotions].members ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
