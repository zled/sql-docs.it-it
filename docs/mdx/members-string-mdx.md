---
title: I membri (String) (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 36d5d3a8573346d164c77881ff80b17feacf8191
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580513"
---
# <a name="members-string-mdx"></a>Members (String) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un membro specificato da un'espressione stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Name*  
 Espressione stringa valida che specifica il nome di un membro.  
  
## <a name="remarks"></a>Remarks  
 Il **membri (String)** funzione restituisce un singolo membro il cui nome è specificato. In genere, si utilizza il **membri (String)** funzione con funzioni esterne, fornendo al **membri (String)** funzione una stringa che identifica un membro, e **membri (String)** funzione restituisce il valore per tale membro specificato.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa il **membri (String)** funzione per convertire la stringa specificata in un membro valido e quindi restituisce la misura predefinita per il membro specificato nella stringa. La stringa specificata è racchiusa tra virgolette singole. La misura predefinita è Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
