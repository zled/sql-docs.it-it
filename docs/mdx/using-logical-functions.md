---
title: Utilizzo di funzioni logiche | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: logical functions [MDX]
ms.assetid: 0cb34d53-9146-4924-9c9b-607afcb7a2be
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5ef44399a37c1b404e4ec9693baedb3a97d413f6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="using-logical-functions"></a>Utilizzo di funzioni logiche
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Una funzione logica esegue un confronto o un'operazione logica su oggetti ed espressioni e restituisce un valore booleano. Le funzioni logiche sono fondamentali nelle espressioni MDX per determinare la posizione di un membro.  
  
 La funzione logica utilizzata più di frequente è il **IsEmpty** (funzione). Per ulteriori informazioni su come utilizzare il **IsEmpty** funzione, vedere [funziona con i valori vuoti](../mdx/working-with-empty-values.md).  
  
 La query seguente viene illustrato come utilizzare il **IsLeaf** e **IsAncestor** funzioni:  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; La sintassi MDX &#41;](../mdx/functions-mdx-syntax.md)  
  
  
