---
title: Elemento IncrementalProcessingNotification (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 22f3975b8f2c09a45f0d82857ced58424c4a9b74
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035602"
---
# <a name="incrementalprocessingnotification-element-assl"></a>Elemento IncrementalProcessingNotification (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene informazioni per il [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) elemento su una query da eseguire per determinare lo stato di avanzamento dell'elaborazione incrementale.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<IncrementalProcessingNotifications>  
   <IncrementalProcessingNotification xsi:type="IncrementalProcessingNotification">...</IncrementalProcessingNotification>  
</IncrementalProcessingNotifications>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[IncrementalProcessingNotification](../../../analysis-services/scripting/data-type/incrementalprocessingnotification-data-type-assl.md)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-n: elemento obbligatorio che può presentarsi più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[IncrementalProcessingNotifications](../../../analysis-services/scripting/collections/incrementalprocessingnotifications-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ProactiveCachingQueryBinding & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)   
 [Elemento ProactiveCaching &#40;ASSL&#41;](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
