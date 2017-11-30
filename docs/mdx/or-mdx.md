---
title: O (MDX) | Documenti Microsoft
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
f1_keywords: OR
dev_langs: kbMDX
helpviewer_keywords: OR operator
ms.assetid: 7634c08a-5b70-44cd-9422-6555fed6ae05
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eb87411a86aad46ed3fcd00737f8ae46b99f5999
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="or-mdx"></a>OR (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Osservazioni  
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
 [Riferimento agli operatori MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
