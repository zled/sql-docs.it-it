---
title: Se l'istruzione (MDX Multidimensional) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- statements [MDX], IF
ms.assetid: 8830cce5-9e06-4f89-a555-295bb0d0a8a1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1d29f1f62214f669367aed255699825ccac0b6ee
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-scripting---if"></a>Creazione di script MDX - IF
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue una determinata istruzione se la condizione specificata è soddisfatta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Espressione MDX (Multidimensional Expression) che restituisce un valore booleano, true o false.  
  
 *assegnazione*  
 Espressione MDX che assegna un valore a un sottocubo o a una proprietà calcolata.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare l'istruzione IF per flusso di controllo, ovvero a differenza di [IIf &#40; MDX &#41; ](../mdx/iif-mdx.md) funzione e [istruzione CASE &#40; MDX &#41; ](../mdx/case-statement-mdx.md) che può essere utilizzato solo per restituire oggetti o valori.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'ambito è limitato al livello Country della gerarchia Geography nella dimensione Customers. Se la misura corrente è Internet Sales Amount, Internet Sales Amount viene impostato su 10:  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

