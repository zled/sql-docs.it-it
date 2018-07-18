---
title: NonEmptyCrossjoin (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7da56ac658f57d6eb664762f9dd94351df39fe0f
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742650"
---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)


  Restituisce un set che contiene il prodotto incrociato di uno o più set, escludendo le tuple vuote e le tuple a cui non sono associati dati di tabelle dei fatti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NonEmptyCrossjoin(Set_Expression1 [ ,Set_Expression2,...] [,Count ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Conteggio*  
 Espressione numerica valida che specifica il numero di set da restituire.  
  
## <a name="remarks"></a>Remarks  
 Il **NonEmptyCrossjoin** funzione restituisce il prodotto incrociato di due o più set, escludendo le tuple vuote o le tuple senza dati ottenuti dalle tabelle dei fatti sottostanti. A causa di come **NonEmptyCrossjoin** funzione works tutte calcolate i membri vengono automaticamente esclusi.  
  
 Se *conteggio* viene omesso, la funzione cross join di tutti i set specificati e consente di escludere i membri vuoti dal set risultante. Se si specifica un numero di set, la funzione eseguirà il cross join dei numeri di set specificati, a partire dal primo set specificato. Il **NonEmptyCrossjoin** funzione utilizza tutti i set rimanenti specificati nei set successivi, ma che non sono stati cross join, per determinare quali membri sono considerati non vuoti in risultante dal cross join di set. Il **NonEmptyCrossjoin** funzione rispetta il **NON_EMPTY_BEHAVIOR** impostazione delle misure calcolate.  
  
> [!IMPORTANT]  
>  Questa funzione è deprecata e non deve essere utilizzata, poiché viene mantenuta solo per gestire la compatibilità con le versioni precedenti. Utilizzare invece il [Exists (MDX)](../mdx/exists-mdx.md) funzione con l'argomento di nome gruppo di misure o [NonEmpty (MDX)](../mdx/nonempty-mdx.md) (funzione).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
