---
title: Lead (MDX) | Documenti Microsoft
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
- LEAD
dev_langs:
- kbMDX
helpviewer_keywords:
- Lead function
ms.assetid: f3250092-7b98-40b5-8dca-77e3b50734a0
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 127c84f38fe85453fa3da7ae2b1c9752b05b6ba7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="lead-mdx"></a>Lead (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il membro che segue il membro specificato del numero specificato di posizioni nel livello del membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Indice*  
 Espressione numerica valida che specifica il numero di posizioni dei membri.  
  
## <a name="remarks"></a>Osservazioni  
 Le posizioni dei membri all'interno di un livello vengono determinate dall'ordine naturale della gerarchia dell'attributo. La numerazione delle posizioni è in base zero.  
  
 Se il valore specificato è zero (0), il **causare** funzione restituisce il membro specificato.  
  
 Se il valore specificato è negativo, il **causare** funzione restituisce un membro precedente.  
  
 `Lead(1)`equivale al [NextMember](../mdx/nextmember-mdx.md) (funzione). `Lead(-1)`equivale al [PrevMember](../mdx/prevmember-mdx.md) (funzione).  
  
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
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

