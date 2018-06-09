---
title: VarP (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc1e6276de9a03af9800b9e242d54130c4241732
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743752"
---
# <a name="varp-mdx"></a>VarP (MDX)


  Restituisce la varianza della popolazione di un'espressione numerica valutata su un set, utilizzando la formula della popolazione distorta (dividendo *n*-1).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Remarks  
 Il **VarP** funzione restituisce la varianza distorta di un'espressione numerica specificata, valutata su un set specificato.  
  
 Il **VarP** funzione utilizza la formula della popolazione distorta formula, durante il [Var](../mdx/var-mdx.md) funzione utilizza la formula della popolazione non distorta.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
