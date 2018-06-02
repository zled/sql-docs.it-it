---
title: SetToArray (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2239249c7372c7132861fbcb74dbe5079a4ae4eb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581003"
---
# <a name="settoarray-mdx"></a>SetToArray (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Converte uno o più set in una matrice da utilizzare in una funzione definita dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Remarks  
 Il **SetToArray** funzione converte uno o più set in una matrice da utilizzare in una funzione definita dall'utente. Il numero di dimensioni nella matrice risultante corrisponde al numero di set specificati.  
  
 L'espressione numerica facoltativa può specificare i valori per le celle della matrice. Se non viene specificata un'espressione numerica, il cross join dei set viene valutato nel contesto corrente.  
  
 Le coordinate delle celle nella matrice risultante corrispondono alla posizione dei set nell'elenco. Ad esempio, per i tre set `SA`, `SB` e `SC`, ognuno dei quali contiene due elementi, l'istruzione MDX `SetToArray(SA, SB, SC)` crea la matrice tridimensionale seguente:  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  Il tipo restituito del **SetToArray** funzione è di tipo VARIANT VT_ARRAY. Pertanto, l'output del **SetToArray** funzione deve essere usata solo come input per una funzione definita dall'utente.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita una matrice.  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
