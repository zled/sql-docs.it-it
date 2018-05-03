---
title: MemberValue (MDX) | Documenti Microsoft
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
- MEMBERVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- MemberValue function
ms.assetid: f9b2af16-2b81-48e4-ae81-99f64e4bbc98
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 488cf1ddbcc9bbb22cb0447e097178e694aafeb4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="membervalue-mdx"></a>MemberValue (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il valore di un membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.MemberValue  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore del membro restituito contiene le informazioni seguenti, elencate in base all'ordine in cui appaiono nel valore restituito:  
  
-   Associazione del valore, se definita.  
  
-   Chiave con il tipo di dati originale se non esiste un'associazione del nome oppure se la chiave e la didascalia sono associate alla stessa colonna.  
  
-   Didascalia del membro.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituiti l'associazione del valore, la chiave del membro e la didascalia della prima data nella dimensione Date del cubo Adventure Works.  
  
```  
WITH MEMBER Measures.ValueColumn as [Date].[Calendar].[July 1, 2001].MemberValue  
MEMBER Measures.KeyColumn as [Date].[Calendar].[July 1, 2001].Member_Key  
MEMBER Measures.NameColumn as [Date].[Calendar].[July 1, 2001].Member_Name  
  
SELECT {Measures.ValueColumn, Measures.KeyColumn, Measures.NameColumn}  ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
