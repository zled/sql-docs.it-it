---
title: Elemento EventID (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EventID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EventID
helpviewer_keywords:
- EventID element
ms.assetid: a6b2ee50-1753-496c-af5c-206d63f2542b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d8f1f785d365b1899185297d903c81871fc3df41
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218887"
---
# <a name="eventid-element-assl"></a>Elemento EventID (ASSL)
  Identifica in modo univoco un' [evento](../objects/event-element-assl.md) elemento che deve essere acquisito come parte di un [traccia](../objects/trace-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Event>  
  
      <EventID>...</EventID>  
  
</Event>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Evento](../objects/event-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `EventID` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.TraceEvent>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Events &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
