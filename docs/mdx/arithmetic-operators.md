---
title: Operatori aritmetici | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: arithmetic operators
ms.assetid: 1dff3e20-fe9d-4155-bf06-27d6458188e9
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6e835905fb1d51d4918c3d382ad6268925d469e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="arithmetic-operators"></a>Operatori aritmetici
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Nel linguaggio MDX (Multidimensional Expressions) è possibile utilizzare gli operatori aritmetici per eseguire qualsiasi tipo di calcolo aritmetico, incluse addizioni, sottrazioni, moltiplicazioni e divisioni.  
  
 MDX supporta gli operatori aritmetici elencati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[+ (addizione)](../mdx/add-mdx.md)|Esegue la somma di due numeri.|  
|[/ (Divisione)](../mdx/divide-mdx-operator-reference.md)|Esegue una divisione di un numero per un altro.|  
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
 [Riferimento agli operatori MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatori &#40; La sintassi MDX &#41;](../mdx/operators-mdx-syntax.md)  
  
  
