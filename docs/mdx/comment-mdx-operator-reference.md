---
title: -(Commento) (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- --
dev_langs:
- kbMDX
helpviewer_keywords:
- commenting characters
- -- (comment character)
ms.assetid: 02aec133-6809-4829-b9a2-102c376e21da
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 2d988fe442b0bc7c00e56aa08e8a9a421f214c6c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="comment---mdx-operator-reference"></a>Commento - riferimento agli operatori MDX
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica un testo di commento specificato dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Parametri  
 *Comment_Text*  
 Stringa contenente il testo del commento.  
  
## <a name="remarks"></a>Osservazioni  
 I commenti possono essere inseriti su una riga distinta oppure nidificati alla fine di una riga di script MDX (Multidimensional Expressions) o in un'istruzione MDX. Nel server il commento non viene valutato.  
  
 Utilizzare questo operatore per commenti su una sola riga o nidificati. I commenti inseriti con -- sono delimitati dal carattere di nuova riga.  
  
 I commenti possono essere di qualsiasi lunghezza.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di questo operatore.  
  
```  
-- This member returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM -- Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Commento & #40; MDX & #41;](../mdx/comment-mdx.md)   
 [&#40;Commento&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
