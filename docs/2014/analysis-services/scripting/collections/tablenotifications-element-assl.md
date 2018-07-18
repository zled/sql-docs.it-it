---
title: Elemento TableNotifications (ASSL) | Microsoft Docs
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
- TableNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- TableNotifications element
ms.assetid: 4cecdfea-0d4d-4bd6-bbb3-4d0d2284c665
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8c146f223d0819c8570b051d77d5764ae384d1b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163402"
---
# <a name="tablenotifications-element-assl"></a>Elemento TableNotifications (ASSL)
  Contiene la raccolta di [TableNotification](../objects/tablenotification-element-assl.md) gli elementi che forniscono informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento sulle tabelle o viste in un'origine dati che sono state modificate.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCachingTablesBinding>  
   <TableNotifications>  
      <TableNotification>...</TableNotification>  
...</TableNotifications>  
</ProactiveCachingTablesBinding>  
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
|Elementi padre|[ProactiveCachingTablesBinding](../data-type/binding-data-type-assl.md)|  
|Elementi figlio|[TableNotification](../objects/tablenotification-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TableNotificationCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ProactiveCachingBinding &#40;ASSL&#41;](../data-type/proactivecachingbinding-data-type-assl.md)   
 [Tipo di dati ProactiveCachingObjectNotificationBinding &#40;ASSL&#41;](../data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
