---
title: '&lt;&gt; (Non uguale a) (MDX) | Documenti Microsoft'
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0ccccc64c4a6b2048a50ac1099c4a31b07537ae0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580553"
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt; (Non uguale a) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
