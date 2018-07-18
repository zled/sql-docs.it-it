---
title: /MTd (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 74c8748ae02df8747be5670f09ec11c7dfa8e882
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742220"
---
# <a name="mtd-mdx"></a>Mtd (MDX)


  Restituisce un set di membri di pari livello dallo stesso livello di un membro dato, iniziando dal primo membro di pari livello e terminando con il membro dato, in base al vincolo imposto dal livello Anno della dimensione temporale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
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
 [Somma &#40;MDX&#41;](../mdx/sum-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
