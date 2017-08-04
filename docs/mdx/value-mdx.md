---
title: Valore (MDX) | Documenti Microsoft
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
- Value
dev_langs:
- kbMDX
helpviewer_keywords:
- Value function
ms.assetid: ff76628e-2d49-49f6-a6cb-f6da07d83d65
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 63e24e0f701332747e3129a57768bfe1b6fbb45d
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="value-mdx"></a>Value (MDX)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il valore del membro corrente della dimensione di tipo misure che si interseca con il membro corrente delle gerarchie dell'attributo nel contesto della query.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression[.Value]   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Il **valore** funzione restituisce il valore del membro specificato sotto forma di stringa. Il **valore** argomento è facoltativo perché la proprietà predefinita di un membro, il valore di un membro e valore restituito per un membro se non viene specificato nessun altro valore. Per ulteriori informazioni sulle proprietà dei membri, vedere [proprietà intrinseche dei membri &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) e [le proprietà dei membri definite dall'utente &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il valore di un membro, così come viene esplicitamente restituito il nome di tale membro.  
  
```  
WITH MEMBER [Date].[Calendar].NumericValue as [Date].[Calendar].[July 1, 2001].Value  
MEMBER [Date].[Calendar].MemberName AS [Date].[Calendar].[July 1, 2001].Name  
  
SELECT {[Date].[Calendar].NumericValue, [Date].[Calendar].MemberName} ON 0  
from [Adventure Works]  
```  
  
 Nell'esempio seguente viene restituito il valore di un membro, come valore predefinito restituito per un membro su un asse.  
  
```  
SELECT {[Date].[Calendar].[July 1, 2001]} ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [MemberValue &#40; MDX &#41;](../mdx/membervalue-mdx.md)   
 [Proprietà &#40; MDX &#41;](../mdx/properties-mdx.md)   
 [Nome &#40; MDX &#41;](../mdx/name-mdx.md)   
 [UniqueName &#40; MDX &#41;](../mdx/uniquename-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
