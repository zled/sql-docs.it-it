---
title: Se l'istruzione (MDX Multidimensional) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e7426c609de80ab249cd71e4364979ff07165598
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579863"
---
# <a name="mdx-scripting---if"></a>Creazione di script MDX - IF
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue una determinata istruzione se la condizione specificata è soddisfatta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 Espressione MDX (Multidimensional Expression) che restituisce un valore booleano, true o false.  
  
 *Assegnazione*  
 Espressione MDX che assegna un valore a un sottocubo o a una proprietà calcolata.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare l'istruzione IF per flusso di controllo, ovvero a differenza di [IIf &#40;MDX&#41; ](../mdx/iif-mdx.md) (funzione) e il [istruzione CASE &#40;MDX&#41; ](../mdx/case-statement-mdx.md) che può essere utilizzato solo per restituire oggetti o valori.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'ambito è limitato al livello Country della gerarchia Geography nella dimensione Customers. Se la misura corrente è Internet Sales Amount, Internet Sales Amount viene impostato su 10:  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
