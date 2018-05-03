---
title: Elemento TableNotification (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TableNotification Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- TableNotification element
ms.assetid: 3afd075a-74f9-428c-b527-ee497cbe71e7
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0aa85b773c80b98b1b5d9f2114828f0f4b36a462
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="tablenotification-element-assl"></a>Elemento TableNotification (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene informazioni per il [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) elemento su una tabella o vista in un'origine dati che è stata modificata.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TableNotifications>  
   <TableNotification>  
      <DbTableName>...</DbTableName>  
      <DbSchemaName>...</DbSchemaName>  
...</TableNotification>  
</TableNotifications>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-n: elemento obbligatorio che può presentarsi più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[TableNotifications](../../../analysis-services/scripting/collections/tablenotifications-element-assl.md)|  
|Elementi figlio|[DbSchemaName](../../../analysis-services/scripting/properties/dbschemaname-element-assl.md), [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TableNotification>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ProactiveCachingTablesBinding &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingtablesbinding-data-type-assl.md)   
 [Tipo di dati ProactiveCachingObjectNotificationBinding &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)   
 [Tipo di dati ProactiveCachingBinding &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
