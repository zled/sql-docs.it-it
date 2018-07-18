---
title: O (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 668e8f1955290c31ee63ca5b81fc5e9c286d54c4
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742450"
---
# <a name="or-mdx"></a>OR (MDX)


  Esegue la disgiunzione logica di due espressioni numeriche.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Expression1 OR Expression2   
```  
  
#### <a name="parameters"></a>Parametri  
 Expression1  
 Espressione MDX (Multidimensional Expression) valida che restituisce un valore numerico.  
  
 Expression2  
 Espressione MDX valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Un valore booleano che restituisce **true** se uno o entrambi gli argomenti restituiscono **true**; in caso contrario, **false**.  
  
## <a name="remarks"></a>Remarks  
 Il **o** gestisce entrambi gli argomenti come valori booleani (zero, 0, come **false**; in caso contrario, **true**) prima di eseguire la disgiunzione logica. Nella tabella seguente viene illustrato come la **o** operatore esegue la disgiunzione logica.  
  
|*Expression1*|*Expression2*|Valore restituito|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Esempio  
 La query seguente contiene una misura calcolata che restituisce la stringa "MARRIED OR MALE" se il membro corrente della gerarchia Gender della dimensione Customer è maschio o se il membro corrente della gerarchia Marital Status della dimensione Customer è sposato. In caso contrario, restituisce la stringa "UNMARRIED OR FEMALE".  
  
```  
WITH  
MEMBER MEASURES.ORDEMO AS  
IIF(  
([Customer].[Gender].CURRENTMEMBER IS [Customer].[Gender].&[M])  
OR  
([Customer].[Marital Status].CURRENTMEMBER IS [Customer].[Marital Status].&[M]),  
"MARRIED OR MALE",  
"UNMARRIED OR FEMALE")  
SELECT [Customer].[Gender].[Gender].MEMBERS ON 0,  
[Customer].[Marital Status].[Marital Status].MEMBERS ON 1  
FROM [Adventure Works]  
WHERE(MEASURES.ORDEMO)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
