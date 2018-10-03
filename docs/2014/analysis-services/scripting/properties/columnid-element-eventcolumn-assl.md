---
title: Elemento ColumnID (EventColumn) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ColumnID Element (EventColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnID
helpviewer_keywords:
- ColumnID element
ms.assetid: c4f4fbad-9d70-4de2-8cf7-caee80a4a1e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4eeb9954f3318a9286865454b6eb61a15f4d4236
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216391"
---
# <a name="columnid-element-eventcolumn-assl"></a>Elemento ColumnID (EventColumn) (ASSL)
  Contiene l'identificatore (ID) della colonna di informazioni da acquisire per un evento come parte di un [traccia](../objects/trace-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
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
|Elemento padre|[EventColumn](../data-type/eventcolumn-data-type-assl.md)|  
|Elementi figlio|Nessuna.|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `ColumnID` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.TraceColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Columns &#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Elemento di un evento &#40;ASSL&#41;](../objects/event-element-assl.md)   
 [Elemento Events &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
