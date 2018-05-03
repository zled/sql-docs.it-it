---
title: Commento (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '*/'
- /*
dev_langs:
- kbMDX
helpviewer_keywords:
- commenting characters
- /*...*/ (comment)
ms.assetid: 64434ae4-80ce-4634-86b8-4125dfaa7f61
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 7dde934f923aa200c516132303835c6e6ac0d567
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="comment-mdx"></a>Commento (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica un testo di commento specificato dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>Parametri  
 *Comment_Text*  
 Stringa contenente il testo del commento.  
  
## <a name="remarks"></a>Osservazioni  
 Il server non valuta il testo tra i caratteri di commento / * e \*/. I commenti possono essere inseriti in una riga distinta o sulla stessa riga di un'istruzione MDX (Multidimensional Expressions). Commenti su più righe devono essere contrassegnati da /\* e \*/.  
  
 I commenti possono essere di qualsiasi lunghezza. e nidificati, ad esempio `/* Test /*Comment*/ Text*/`.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di questo operatore.  
  
```  
/* This member returns the gross profit margin for product types  
  and reseller types crossjoined by year. */  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM /* Select from the Adventure Works cube. */  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [&#40;Commento&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [-& #40; Commento & #41; & #40; MDX & #41;](../mdx/comment-mdx-operator-reference.md)   
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
