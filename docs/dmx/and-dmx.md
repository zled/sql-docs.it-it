---
title: E (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AND
dev_langs:
- DMX
helpviewer_keywords:
- AND, DMX
ms.assetid: d337b20c-f80e-48be-9354-371367e53735
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bcb67e3b5c16a9bee84271eebc2083a065e924d9
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="and-dmx"></a>AND (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue la congiunzione logica di due espressioni numeriche.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>Parametri  
 *Expression1*  
 Espressione DMX (Data Mining Extensions) valida che restituisce un valore numerico.  
  
 *Expression2*  
 Espressione DMX valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Valore booleano che restituisce TRUE se entrambi i parametri restituiscono TRUE, FALSE in caso contrario.  
  
## <a name="remarks"></a>Osservazioni  
 Per consentire all'operatore di eseguire la congiunzione logica, entrambi i parametri vengono gestiti come valori booleani, per cui 0 equivale a FALSE e tutti gli altri valori a TRUE. Nella tabella seguente sono elencati i valori restituiti per le varie combinazioni dei valori dei parametri.  
  
|Valore di Expression1|Valore di Expression2|Valore restituito|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|FALSE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logica operatori &#40; DMX &#41;](../dmx/operators-logical.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  

