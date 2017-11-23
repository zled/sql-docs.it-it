---
title: Categoria di eventi di blocco | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: trace-events
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 06427f8e-89bb-4710-a0c1-dc5e42b7e95e
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8b2e6ba2dc66621bd74026f8aceb8c35eed4f0b1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="lock-events-category"></a>Categoria di eventi relativa ai blocchi
  Nella categoria di eventi relativa agli eventi di blocco sono incluse le classi di eventi descritte nella tabella seguente.  
  
|Event Class|ID evento|Description|  
|-----------------|--------------|-----------------|  
|Deadlock|50|Vengono raccolti tutti gli eventi di deadlock dei blocchi a livello di metadati dall'avvio della traccia.|  
|Lock timeout|51|Vengono raccolti tutti gli eventi di timeout di blocco dei metadati dall'avvio della traccia.|  
|Lock Acquired|52|Vengono raccolte le informazioni sui blocchi acquisiti dall'avvio della traccia.|  
|Lock Released|53|Vengono raccolte le informazioni sui blocchi rilasciati dall'avvio della traccia.|  
|Lock Waiting|54|Vengono raccolte le informazioni sui blocchi in stato di attesa dall'avvio della traccia.|  
  
 Per informazioni sulle colonne associate a ogni classe degli eventi di blocco, vedere [Lock Events Data Columns](../../analysis-services/trace-events/lock-events-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
