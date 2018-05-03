---
title: TopSum (MDX) | Documenti Microsoft
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
- TOPSUM
dev_langs:
- kbMDX
helpviewer_keywords:
- TopSum function
ms.assetid: e32496fd-4897-43c9-a388-4028609f4ffb
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 75c30d2874cfdbb46823f095d14685866d3e6252
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="topsum-mdx"></a>TopSum (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ordina un set e restituisce gli elementi superiori il cui totale cumulativo è maggiore o uguale al valore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Valore*  
 Espressione numerica valida che specifica il valore in base a cui ogni tupla viene valutata.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) che restituisce una misura.  
  
## <a name="remarks"></a>Osservazioni  
 Il **TopSum** funzione calcola la somma di una misura specificata valutata su un set specificato, disponendo il set in ordine decrescente. La funzione restituisce quindi gli elementi con i valori più alti il cui totale per l'espressione numerica specificata corrisponde almeno al valore specificato. La funzione restituisce il subset più piccolo di un set il cui totale cumulativo corrisponde almeno al valore specificato. Gli elementi restituiti sono ordinati dal più grande al più piccolo.  
  
> [!IMPORTANT]  
>  Ad esempio il [BottomSum](../mdx/bottomsum-mdx.md) funzione, il **TopSum** funzione rispetta mai la gerarchia.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito per la categoria Bike il set più piccolo di membri del livello City nella gerarchia Geography della dimensione Geography il cui totale cumulativo calcolato utilizzando la misura Reseller Sales Amount corrisponde almeno alla somma di 6.000.000 (a partire dai membri di questo set con il numero di vendite più elevato).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
