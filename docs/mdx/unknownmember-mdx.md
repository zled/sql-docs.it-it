---
title: UnknownMember (MDX) | Documenti Microsoft
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
- UnknownMember
dev_langs:
- kbMDX
helpviewer_keywords:
- UnknownMember function
ms.assetid: 5ae39cbe-65c8-4a59-9548-71b28ecf6eb5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 131993b1038229138df3e7d084b5d842693b7f0f
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il membro sconosciuto associato a un livello o a un membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] crea un membro sconosciuto per associare i dati della tabella dei fatti a una gerarchia quando la gerarchia non è noto. Il membro sconosciuto può trovarsi a uno dei livelli seguenti:  
  
-   Al livello principale per le gerarchie di attributi non aggregate.  
  
-   Al primo livello sotto il **tutti** livello per le gerarchie naturali.  
  
-   A qualsiasi livello per le gerarchie non naturali.  
  
 Se viene specificata un'espressione di membro, il **UnknownMember** funzione restituisce il membro sconosciuto figlio del membro specificato. Se il membro specificato non esiste, la funzione restituirà Null.  
  
 Se viene specificata un'espressione di gerarchia, il **UnknownMember** funzione restituisce il membro sconosciuto al livello superiore, se presente.  
  
 Se il membro sconosciuto non esiste sul livello o membro, il **UnknownMember** funzione crea un membro null.  
  
> [!NOTE]  
>  Se il membro sconosciuto non esiste sulla gerarchia o sul membro, verrà generato un errore.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il membro sconosciuto per il membro All Products nella gerarchia dell'attributo Product per tutti i membri della dimensione Measures.  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il membro sconosciuto per la gerarchia Product Categories per tutti i membri della dimensione Measures.  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

