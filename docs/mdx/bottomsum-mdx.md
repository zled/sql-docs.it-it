---
title: BottomSum (MDX) | Documenti Microsoft
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7d36c2567ab73b299cb528430b3ede7d81cf1bc5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="bottomsum-mdx"></a>BottomSum (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

