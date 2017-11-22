---
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords: ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 39e10a6563e33ae1d1235bc220d7bd82826be853
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Per un servizio dati di riferimento [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto, specifica la priorità di esecuzione del thread asincrona che recupera i dati.  
  
 Utilizzare queste costanti con il **Recordset** "**priorità di Thread in Background**" proprietà dinamiche, che viene fatto riferimento nell'indice per ADO, OLE DB di proprietà dinamiche e documentata nel [ Servizio di cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) documentazione.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|Imposta la priorità tra normale e massimo.|  
|**adPriorityBelowNormal**|2|Imposta la priorità tra più basso e normale.|  
|**adPriorityHighest**|5|Imposta la priorità più elevata possibile.|  
|**AdPriorityLowest**|1|Imposta la priorità sul livello minimo.|  
|**adPriorityNormal**|3|Imposta la priorità normale.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|
