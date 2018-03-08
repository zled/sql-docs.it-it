---
title: NON (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NOT
dev_langs: DMX
helpviewer_keywords: NOT operator [DMX]
ms.assetid: 6d91b3d9-270c-4a68-b41f-169cff5faa0e
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c242a6767e60b04249d69d340806d0cf78a374e2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Operatore logico che esegue la negazione logica di un'espressione numerica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Parametri  
 *Expression1*  
 Espressione DMX valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Valore booleano che restituisce FALSE se l'argomento restituisce TRUE e viceversa.  
  
## <a name="remarks"></a>Osservazioni  
 Per consentire all'operatore di eseguire la negazione logica, l'argomento viene gestito come valore booleano, per cui 0 equivale a FALSE e tutti gli altri valori a TRUE. Se *Expression1* è TRUE, l'operatore restituisce FALSE. Se *Expression1* è FALSE, l'operatore restituisce TRUE. La tabella seguente illustra come viene eseguita la negazione logica.  
  
|Valore di Expression1|Valore restituito|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logica operatori &#40; DMX &#41;](../dmx/operators-logical.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  
