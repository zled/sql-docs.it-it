---
title: Elemento OnlineMode (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- OnlineMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OnlineMode
helpviewer_keywords:
- OnlineMode element
ms.assetid: 0bbac4e2-002f-4be4-8dd6-ccd7034f5f93
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7a4469a522b1364df645fc1dcb0362647397a89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196841"
---
# <a name="onlinemode-element-assl"></a>Elemento OnlineMode (ASSL)
  Specifica se il database ritorna immediatamente online quando la ricompilazione della cache è iniziata, o solo quando la ricompilazione della cache è completa.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <OnlineMode>...</OnlineMode>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Controllo immediato*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Controllo immediato*|La modalità online del database viene riattivata immediatamente all'avvio della ricompilazione della cache.|  
|*OnCacheComplete*|La modalità online del database viene riattivata solo al termine della ricompilazione della cache.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `OnlineMode` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ProactiveCaching &#40;ASSL&#41;](../objects/proactivecaching-element-assl.md)  
  
  
