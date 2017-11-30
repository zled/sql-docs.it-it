---
title: Cousin (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COUSIN
dev_langs: kbMDX
helpviewer_keywords: Cousin function
ms.assetid: 9a416685-d35d-4d9c-a9f6-4574cbe59aea
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: fee1f82f0ed706a2ce75eedcb0968f007a0037c3
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="cousin-mdx"></a>Cousin (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il membro figlio con la stessa posizione relativa del membro figlio specificato rispetto a un membro padre.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Cousin( Member_Expression , Ancestor_Member_Expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Ancestor_Member_Expression*  
 Espressione di membro MDX (Multidimensional Expression) valida che restituisce un membro predecessore.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione agisce sull'ordine e sulla posizione dei membri all'interno dei livelli. Se sono presenti due gerarchie la prima delle quali dispone di quattro livelli e la seconda di cinque, il membro cousin del terzo livello della prima gerarchia è costituito dal terzo livello della seconda gerarchia.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene recuperato il membro cousin del quarto trimestre dell'anno fiscale 2002, in base al relativo predecessore a livello di anno nell'anno fiscale 2003. Il membro cousin recuperato è costituito dal quarto trimestre dell'anno fiscale 2003.  
  
```  
SELECT Cousin   
   ( [Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002],  
     [Date].[Fiscal].[FY 2003]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene recuperato il membro cousin del mese di luglio dell'anno fiscale 2002, in base al relativo predecessore a livello di trimestre nel secondo trimestre dell'anno fiscale 2004. Il membro cousin recuperato è costituito dal mese di ottobre 2003.  
  
```  
SELECT Cousin   
   ([Date].[Fiscal].[Month].[July 2002] ,  
    [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2004]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
