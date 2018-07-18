---
title: Elemento IncrementalProcessingNotifications (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IncrementalProcessingNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotifications element
ms.assetid: 46f3c9d0-46cc-4833-8f15-7831207f57ce
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 14d49b5e7a4d86aec5a2ac555cb67094b30b2fef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230001"
---
# <a name="incrementalprocessingnotifications-element-assl"></a>Elemento IncrementalProcessingNotifications (ASSL)
  Contiene la raccolta di [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md) gli elementi che forniscono informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) sulle query da eseguire per determinare lo stato dell'elemento elaborazione incrementale.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCachingIncrementalProcessingBinding>  
   <IncrementalProcessingNotifications>  
      <IncrementalProcessingNotification>...  
   ...</IncrementalProcessingNotification>  
   </IncrementalProcessingNotifications>  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md)|  
|Elementi figlio|[IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.IncrementalProcessingNotificationCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
