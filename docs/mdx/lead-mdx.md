---
title: Lead (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d72af1bf0b671eeb2bd4b84c194f129ed1ce6bfe
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741030"
---
# <a name="lead-mdx"></a>Lead (MDX)


  Restituisce il membro che segue il membro specificato del numero specificato di posizioni nel livello del membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Index*  
 Espressione numerica valida che specifica il numero di posizioni dei membri.  
  
## <a name="remarks"></a>Remarks  
 Le posizioni dei membri all'interno di un livello vengono determinate dall'ordine naturale della gerarchia dell'attributo. La numerazione delle posizioni è in base zero.  
  
 Se il valore specificato è zero (0), il **causare** funzione restituisce il membro specificato.  
  
 Se il valore specificato è negativo, il **causare** funzione restituisce un membro precedente.  
  
 `Lead(1)` equivale ai [NextMember](../mdx/nextmember-mdx.md) (funzione). `Lead(-1)` equivale ai [PrevMember](../mdx/prevmember-mdx.md) (funzione).  
  
 Il **causare** funzione è simile al [Lag](../mdx/lag-mdx.md) funzione, con la differenza che il **Lag** funzione Cerca nella direzione opposta al **causare** (funzione). In altre parole, `Lead(n)` equivale a `Lag(-n)`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il valore per dicembre 2001:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(-2) ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il valore per marzo 2002:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
