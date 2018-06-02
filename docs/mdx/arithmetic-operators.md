---
title: Operatori aritmetici | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4bf4a182c73acb18d649de3888f735f8842964dc
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576953"
---
# <a name="arithmetic-operators"></a>Operatori aritmetici
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Nel linguaggio MDX (Multidimensional Expressions) è possibile utilizzare gli operatori aritmetici per eseguire qualsiasi tipo di calcolo aritmetico, incluse addizioni, sottrazioni, moltiplicazioni e divisioni.  
  
 MDX supporta gli operatori aritmetici elencati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[+ (addizione)](../mdx/add-mdx.md)|Esegue la somma di due numeri.|  
|[/ (Divide)](../mdx/divide-mdx-operator-reference.md)|Esegue una divisione di un numero per un altro.|  
|[* (moltiplicazione)](../mdx/multiply-mdx.md)|Moltiplica due numeri.|  
|[- (sottrazione)](../mdx/subtract-mdx.md)|Sottrae un numero da un altro.|  
|^ (elevamento a potenza)|Eleva un numero a un altro numero.|  
  
> [!NOTE]  
>  In MDX non sono incluse funzioni per ottenere la radice quadrata di un numero. Per ottenere la radice quadrata di un numero, elevarlo alla potenza di 0,5 utilizzando l'operatore ^.  
  
## <a name="order-of-precedence"></a>Ordine di precedenza  
 L'ordine di precedenza per gli operatori aritmetici in un'espressione MDX è determinato dalle regole seguenti:  
  
-   Se un'espressione include più operatori aritmetici, verranno eseguite per prime le operazioni di moltiplicazione e divisione, seguite da sottrazione e addizione.  
  
-   Se tutti gli operatori aritmetici in un'espressione hanno la stessa precedenza, verranno applicati procedendo da sinistra a destra.  
  
-   Le espressioni tra parentesi hanno la precedenza su tutte le altre operazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Gli operatori &#40;sintassi MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
