---
title: Lag (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3c5479aa3ce855b554f34f72c5c86aa86eb04b9f
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740880"
---
# <a name="lag-mdx"></a>Lag (MDX)


  Restituisce il membro che precede il membro specificato del numero specificato di posizioni al livello del membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Index*  
 Espressione numerica valida che specifica il numero di posizioni tra i membri.  
  
## <a name="remarks"></a>Remarks  
 Le posizioni dei membri all'interno di un livello vengono determinate dall'ordine naturale della gerarchia dell'attributo. La numerazione delle posizioni è in base zero.  
  
 Se il numero di posizioni specificato è uguale a zero, il **Lag** funzione restituisce il membro specificato.  
  
 Se il numero di posizioni specificato è negativo, il **Lag** funzione restituisce un membro successivo.  
  
 `Lag(1)` equivale ai [PrevMember](../mdx/prevmember-mdx.md) (funzione). `Lag(-1)` equivale ai [NextMember](../mdx/nextmember-mdx.md) (funzione).  
  
 Il **Lag** funzione è simile al [causare](../mdx/lead-mdx.md) funzione, con la differenza che il **causare** funzione Cerca nella direzione opposta al **Lag** (funzione). In altre parole, `Lag(n)` equivale a `Lead(-n)`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il valore per dicembre 2001:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(2) ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il valore per marzo 2002:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(-1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
