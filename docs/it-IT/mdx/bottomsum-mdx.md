---
title: BottomSum (MDX) | Documenti Microsoft
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
- BOTTOMSUM
dev_langs:
- kbMDX
helpviewer_keywords:
- BottomSum function
ms.assetid: b3b10e68-2a36-4c38-85f4-3bb7917d5ae8
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f2080c608bc80f9d86f9b74e3ba2deebff8f837d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dispone un set specificato in ordine crescente e restituisce un set di tuple con i valori più bassi la cui somma è uguale o inferiore a un valore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Valore*  
 Espressione numerica valida che specifica il valore in base a cui ogni tupla viene valutata.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Il **BottomSum** funzione calcola la somma di una misura specificata valutata su un set specificato, disponendo il set in ordine crescente. La funzione restituisce quindi gli elementi con i valori più bassi il cui totale per l'espressione numerica specificata corrisponde almeno al valore specificato (somma). La funzione restituisce il subset più piccolo di un set il cui totale cumulativo corrisponde almeno al valore specificato. Gli elementi restituiti sono ordinati dal più piccolo al più grande.  
  
> [!IMPORTANT]  
>  Il **BottomSum** funzione, come il [TopSum](../mdx/topsum-mdx.md) funzione, non rispetta mai la gerarchia.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito per la categoria Bike il set più piccolo di membri del livello City nella gerarchia Geography della dimensione Geography per l'anno fiscale 2003 il cui totale cumulativo, utilizzando la misura Reseller Sales Amount, corrisponde almeno alla somma di 50.000 (a partire dai membri di questo set con il numero di vendite più basso):  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
