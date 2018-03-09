---
title: XTP Storage di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2bb4803233db54eea8d3acfb5cb5e2284cc606fb
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-xtp-storage"></a>Archiviazione XTP di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L'oggetto prestazione dell'archiviazione XTP di SQL Server include i contatori correlati all'archiviazione su disco per OLTP in memoria in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Nella tabella seguente sono descritti i contatori dell' **archiviazione XTP di SQL Server** .  
  
|Contatore|Description|  
|-------------|-----------------|  
|**Checkpoint chiusi**|Conteggio di checkpoint chiusi eseguiti dall'agente online.|  
|**Checkpoint completati**|Conteggio di checkpoint elaborati dal thread offline dei checkpoint.|  
|**Operazioni di unioni principali completate**|Numero di operazioni di unioni principali completate dal thread di lavoro di tipo merge. Queste operazioni devono ancora essere installate.|  
|**Valutazioni dei criteri di unione**|Numero di valutazioni dei criteri di unione dall'avvio del server.|  
|**Richieste di tipo merge in sospeso**|Numero di richieste di tipo merge in sospeso dall'avvio del server.|  
|**Operazioni di unione abbandonate**|Numero di operazioni di unione abbandonate a causa di un errore.|  
|**Operazioni di unione installate**|Numero di operazioni di unione installate correttamente.|  
|**File totali uniti**|Numero totale di file di origine uniti. Questo numero può essere utilizzato per trovare il numero medio di file di origine nell'unione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Contatori delle prestazioni XTP &#40;OLTP in memoria&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
