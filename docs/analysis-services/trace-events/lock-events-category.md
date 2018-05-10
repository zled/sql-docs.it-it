---
title: Categoria di eventi di blocco | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 46148326b3351340a57a26d445a225cbbea35220
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="lock-events-category"></a>Categoria di eventi relativa ai blocchi
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
  
