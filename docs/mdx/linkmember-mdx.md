---
title: LinkMember (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 71235953f592572bd7ac0dcb2493d97dd509f8b7
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741500"
---
# <a name="linkmember-mdx"></a>LinkMember (MDX)


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
  
## <a name="remarks"></a>Remarks  
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
 [HIERARCHIZE- &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [Ascendants &#40;MDX&#41;](../mdx/ascendants-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
