---
title: LinkMember (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: LINKMEMBER
dev_langs: kbMDX
helpviewer_keywords: LinkMember function
ms.assetid: b9106f07-8ea2-4933-aed3-ee9c63acf7ac
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b9122e0ae4aec51fe2e554f4e5d667fb9225e4d0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="linkmember-mdx"></a>LinkMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il membro equivalente a un membro specificato in una gerarchia specifica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LinkMember(Member_Expression, Hierarchy_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
## <a name="remarks"></a>Osservazioni  
 Il **LinkMember** funzione restituisce il membro della gerarchia specificata che corrisponde ai valori chiavi a ogni livello del membro specificato in una gerarchia correlata. Gli attributi a ogni livello devono disporre della stessa cardinalità delle chiavi e dello stesso tipo di dati. Nelle gerarchie non naturali, in presenza di più corrispondenze per un valore di chiave di un attributo, il risultato sarà indeterminato o verrà restituito un errore.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa il **LinkMember** funzione per restituire la misura predefinita nel cubo di Adventure Works per i predecessori del membro 1 luglio 2002 della gerarchia dell'attributo date nella gerarchia Calendar.  
  
```  
SELECT  Hierarchize  
   (Ascendants   
      (LinkMember   
         ([Date].[Date].[July 1, 2002], [Date].[Calendar]  
         )  
       )  
    ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [HIERARCHIZE &#40; MDX &#41;](../mdx/hierarchize-mdx.md)   
 [Ascendants &#40; MDX &#41;](../mdx/ascendants-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
