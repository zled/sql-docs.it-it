---
title: Set di righe DISCOVER_INSTANCES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DISCOVER_INSTANCES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_INSTANCES rowset
ms.assetid: e0842e63-089d-468d-869f-634da343d9fb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a0f716f32898668e019db15aef62e140e9c0d09
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198586"
---
# <a name="discoverinstances-rowset"></a>Set di righe DISCOVER_INSTANCES
  Descrive le istanze nel server.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_INSTANCES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`INSTANCE_NAME`|`DBTYPE_WSTR`||Nome dell’istanza.|  
|`INSTANCE_PORT_NUMBER`|`DBTYPE_I4`||Numero di porta su cui l'istanza resta in attesa.|  
|`INSTANCE_STATE`|`DBTYPE_I4`||Stato dell'istanza del server:<br /><br /> -   `Started`<br />-   `Stopped`<br />-   `Starting`<br />-   `Stopping`<br />-   `Paused`|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_INSTANCES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`INSTANCE_NAME`|`DBTYPE_WSTR`|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
