---
title: Lag (MDX) | Documenti Microsoft
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
- LAG
dev_langs:
- kbMDX
helpviewer_keywords:
- Lag function
ms.assetid: 08c704ea-35d8-44ee-abe5-93bd24b99906
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: eedeae82c5b7566f0c59a6876fc6743c61794de0
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="lag-mdx"></a>Lag (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il membro che precede il membro specificato del numero specificato di posizioni al livello del membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Indice*  
 Espressione numerica valida che specifica il numero di posizioni tra i membri.  
  
## <a name="remarks"></a>Osservazioni  
 Le posizioni dei membri all'interno di un livello vengono determinate dall'ordine naturale della gerarchia dell'attributo. La numerazione delle posizioni è in base zero.  
  
 Se il numero di posizioni specificato è uguale a zero, il **Lag** funzione restituisce il membro specificato.  
  
 Se il numero di posizioni specificato è negativo, il **Lag** funzione restituisce un membro successivo.  
  
 `Lag(1)`equivale al [PrevMember](../mdx/prevmember-mdx.md) (funzione). `Lag(-1)`equivale al [NextMember](../mdx/nextmember-mdx.md) (funzione).  
  
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
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

