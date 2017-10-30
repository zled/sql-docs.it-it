---
title: Utilizzo delle funzioni membro | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- member functions [MDX]
ms.assetid: 094c443f-0daa-4af7-801c-d2e1d686d755
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9354c2e6a83918742f1c2de1dea943be4b21e844
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="using-member-functions"></a>Utilizzo delle funzioni membro
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Una funzione membro è una funzione MDX (Multidimensional Expressions) che restituisce un membro. Le funzioni membro, come le funzioni di tupla e le funzioni sui set, sono essenziali per la negoziazione delle strutture multidimensionali che si trovano in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Delle molte funzioni membro in MDX, la più importante è il **CurrentMember** funzione, viene utilizzato per determinare il membro corrente in una gerarchia. La query seguente viene illustrato come utilizzare, insieme al **padre**, **predecessore**, e **Prevmember** funzioni:  
  
 `WITH`  
  
 `//Returns the name of the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[CurrentMemberDemo] AS [Date].[Calendar].CurrentMember.Name`  
  
 `//Returns the name of the parent of the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[ParentDemo] AS [Date].[Calendar].CurrentMember.Parent.Name`  
  
 `//Returns the name of the ancestor of the currentmember on the Calendar hierarchy at the Year level`  
  
 `MEMBER MEASURES.[AncestorDemo] AS ANCESTOR([Date].[Calendar].CurrentMember, [Date].[Calendar].[Calendar Year]).Name`  
  
 `//Returns the name of the member before the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[PrevMemberDemo] AS [Date].[Calendar].CurrentMember.Prevmember.Name`  
  
 `SELECT{MEASURES.[CurrentMemberDemo],MEASURES.[ParentDemo],MEASURES.[AncestorDemo],MEASURES.[PrevMemberDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; La sintassi MDX &#41;](../mdx/functions-mdx-syntax.md)   
 [Utilizzo di funzioni di tupla](../mdx/using-tuple-functions.md)   
 [Utilizzo di Set di funzioni](../mdx/using-set-functions.md)  
  
  

