---
title: Tipo di dati ProactiveCachingObjectNotificationBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ProactiveCachingObjectNotificationBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingObjectNotificationBinding data type
ms.assetid: b3cf5fb6-6121-4f25-8de6-f171792c440d
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72b45eae800790497b661a82e079255651bec4d5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330331"
---
# <a name="proactivecachingobjectnotificationbinding-data-type-assl"></a>Tipo di dati ProactiveCachingObjectNotificationBinding (ASSL)
  Definisce un tipo di dati derivato astratto che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento sulle modifiche dell'origine dati, in tabelle e viste specificate o in tabelle e nelle viste identificate tramite le associazioni dati esistenti che richiedono la ricompilazione della cache.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCachingObjectNotificationBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingObjectNotificationBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|Tipi di dati derivati|[ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md), [ProactiveCachingTablesBinding](proactivecachingtablesbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[NotificationTechnique](../properties/notificationtechnique-element-assl.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sul `ProactiveCachingBinding` tipo, inclusa una tabella della gerarchia di ereditarietà di `ProactiveCachingBinding` tipi, vedere [tipo di dati ProactiveCachingBinding &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per altre informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ProactiveCachingObjectNotificationBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
