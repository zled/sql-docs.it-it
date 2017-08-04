---
title: /MTd (MDX) | Documenti Microsoft
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
- MTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Mtd function
ms.assetid: 07d8fd65-f9e6-42d4-868d-fccfac6bdb70
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b177ad5ade9a3c73299fa675674eb5c783df79d4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mtd-mdx"></a>Mtd (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un set di membri di pari livello dallo stesso livello di un membro dato, iniziando dal primo membro di pari livello e terminando con il membro dato, in base al vincolo imposto dal livello Anno della dimensione temporale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Se un'espressione di membro non è specificata, il valore predefinito è il membro corrente della prima gerarchia con un livello di tipo *mesi* nella prima dimensione di tipo *ora* nel gruppo di misure.  
  
 Il **/MTd** è una funzione di scelta rapida per il [PeriodsToDate](../mdx/periodstodate-mdx.md) funziona quando la proprietà Type della gerarchia dell'attributo in cui si basa il livello è impostata su *mesi*. In altre parole, `Mtd(Member_Expression)` equivale a `PeriodsToDate(Month_Level_Expression,Member_Expression)`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la somma dei costi di spedizione nell'ultimo mese per le vendite Internet effettuate fino al 20 luglio 2002.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Somma &#40; MDX &#41;](../mdx/sum-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

