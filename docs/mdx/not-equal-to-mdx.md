---
title: '&lt;&gt;(Non uguale a) (MDX) | Documenti Microsoft'
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <>
dev_langs: kbMDX
helpviewer_keywords:
- not equal to operator (<>)
- <> (not equal to operator)
ms.assetid: b4eb3f1c-8b68-4530-a8f3-e3b8414ac789
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 36e366f4dc72b540ce3ba70e12fadc6d9a99aadf
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt;(Non uguale a) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue un'operazione di confronto che determina se il valore di un'espressione MDX (Multidimensional Expression) è diverso da quello di un'altra espressione MDX.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
MDX_Expression <> MDX_Expression  
```  
  
#### <a name="parameters"></a>Parametri  
 *MDX_Expression*  
 Espressione MDX valida.  
  
## <a name="return-value"></a>Valore restituito  
 Valore booleano basato sulle condizioni seguenti:  
  
-   **true** se entrambi i parametri sono non null e il primo parametro non è uguale al secondo parametro.  
  
-   **false** se entrambi i parametri sono non null e il primo parametro è uguale al secondo parametro.  
  
-   Null se uno o entrambi i parametri restituiscono un valore Null.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
