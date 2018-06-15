---
title: Categoria di eventi di blocco | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 62804b077f43b5123b1992a6f52b29af288e2821
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040335"
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
  
  
