---
title: Divisione (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 86b4d8c97996733396e3062e134b2e31d2819ec0
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739800"
---
# <a name="divide-mdx"></a>Divisione (MDX)


  Esegue una divisione e restituisce il risultato alternativo o BLANK() della divisione per 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeratore*  
 Dividendo o numero da dividere.  
  
 *denominatore*  
 Divisore o numero per cui dividere.  
  
 *alternateresult*  
 (Facoltativo) Il valore restituito se la divisione per zero genera un errore. Se non viene fornito, il valore predefinito è BLANK().  
  
## <a name="remarks"></a>Remarks  
 Il risultato alternativo nelle divisione per 0 deve essere una costante.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
