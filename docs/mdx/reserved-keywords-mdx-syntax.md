---
title: Parole chiave (sintassi MDX) riservate | Documenti Microsoft
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
- reserved words [MDX]
- Multidimensional Expressions [Analysis Services], reserved words
- MDX [Analysis Services], reserved words
ms.assetid: 0baab5fb-bd04-4ab3-b99a-9f91f3470fbb
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fe6d331df302b14d46ed643adaee879b2a0f4dd1
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="reserved-keywords-mdx-syntax"></a>Parole chiave riservate (sintassi MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] riserva determinate parole chiave per l'utilizzo esclusivo. Per un elenco di parole chiave riservate, vedere [parole riservate MDX](../mdx/mdx-reserved-words.md).  
  
 Di seguito sono riportate le linee guida per l'utilizzo delle parole chiave riservate:  
  
-   Non è possibile includere parole chiave riservate in un'istruzione MDX (Multidimensional Expressions) in posizioni diverse da quella definita da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Non è possibile assegnare agli oggetti di database nomi uguali a parole chiave riservate. Se esistono oggetti con nomi di questo tipo, per farvi riferimento sarà sempre necessario utilizzare identificatori delimitati. Anche se in questo modo è possibile assegnare agli oggetti nomi costituiti da parole riservate, è comunque preferibile evitare di utilizzare parole chiave come nomi per gli oggetti.  
  
-   Adottare una convenzione di denominazione che evita l'utilizzo di parole chiave riservate. Se è necessario attribuire a un oggetto un nome simile a una parola chiave riservata, eliminare le consonanti o le vocali da tale parola.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli elementi della sintassi MDX &#40; MDX &#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  

