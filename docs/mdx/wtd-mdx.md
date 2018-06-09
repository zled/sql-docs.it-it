---
title: Wtd (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a548f25d9114e9032f2462bbc97bda637abd6d9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743781"
---
# <a name="wtd-mdx"></a>Wtd (MDX)


  Restituisce un set di membri di pari livello dallo stesso livello di un membro dato, iniziando dal primo membro di pari livello e terminando con il membro dato, in base al vincolo imposto dal livello Settimana della dimensione temporale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Se un'espressione di membro non è specificata, il valore predefinito è il membro corrente della prima gerarchia con un livello di tipo settimane nella prima dimensione di tipo Time (**CurrentMember**) nel gruppo di misure.  
  
 Il **Wtd** è una funzione di scelta rapida per il [PeriodsToDate](../mdx/periodstodate-mdx.md) funzione in cui il livello è impostato su *settimane*. In altre parole, `Wtd(Member_Expression)` equivale a `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>Vedere anche  
 [QTD &#40;MDX&#41;](../mdx/qtd-mdx.md)   
 [/MTd &#40;MDX&#41;](../mdx/mtd-mdx.md)   
 [YTD &#40;MDX&#41;](../mdx/ytd-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
