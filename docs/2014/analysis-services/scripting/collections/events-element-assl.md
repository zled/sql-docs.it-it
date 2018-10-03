---
title: Elemento Events (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Events Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Events
helpviewer_keywords:
- Events element
ms.assetid: de887998-dc4b-44dc-8fec-08d67b92f96d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f336d2a265a6a427d2b2674ac233c0468fb63e8f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197777"
---
# <a name="events-element-assl"></a>Elemento Events (ASSL)
  Definisce la raccolta di elementi [Event](../objects/event-element-assl.md) da acquisire tramite un elemento [Trace](../objects/trace-element-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Trace>  
   ...  
   <Events>  
      <Event>...</Event>  
   </Events>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Traccia](../objects/trace-element-assl.md)|  
|Elementi figlio|[Evento](../objects/event-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TraceEventCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analizza l'elemento &#40;ASSL&#41;](traces-element-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
