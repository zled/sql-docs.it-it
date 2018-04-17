---
title: Sys.dm_resource_governor_resource_pool_volumes (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
ms.assetid: fa692e56-c561-4533-97c5-bc12c600553f
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f06bd0a3c3c116d616c73a1b2e14708f1c7fa29d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmresourcegovernorresourcepoolvolumes-transact-sql"></a>sys.dm_resource_governor_resource_pool_volumes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle statistiche di I/O del pool di risorse corrente per ogni volume del disco. Queste informazioni sono disponibili anche a livello di pool di risorse in [DM resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|ID del pool di risorse. Non ammette i valori Null.|  
|volume_name|**sysname**|Nome del volume del disco. Non ammette i valori Null.|  
|read_io_queued_total|**int**|Il totale degli I/O letti accodati dalla reimpostazione di Resource Govenor. Non ammette i valori Null.|  
|read_io_issued_total|**int**|Il totale degli I/O di lettura generati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|read_ios_completed_total|**int**|Il totale degli I/O di lettura completati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|read_ios_throttled_total|**int**|Il totale degli I/O di lettura limitati dalla reimpostazione delle statistiche di Resource Governor. Non ammette i valori Null.|  
|read_bytes_total|**bigint**|Il numero totale di byte letti dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|read_io_stall_total_ms|**bigint**|Il tempo totale espresso in millisecondi tra l'arrivo e il completamento degli I/O di lettura. Non ammette i valori Null.|  
|read_io_stall_queued_ms|**bigint**|Il tempo totale espresso in millisecondi tra l'arrivo degli I/O di lettura e il problema. Si tratta del ritardo introdotto dalla governance delle risorse di I/O. Non ammette i valori Null.|  
|write_io_queued_total|**int**|Il totale degli I/O di scrittura accodati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|write_io_issued_total|**int**|Il totale degli I/O di scrittura generati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|write_io_completed_total|**int**|Il totale degli I/O di scrittura completati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null|  
|write_io_throttled_total|**int**|Il totale degli I/O di scrittura limitati dalla reimpostazione delle statistiche di Resource Governor. Non ammette i valori Null|  
|write_bytes_total|**bigint**|Il numero totale di byte scritti dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|write_io_stall_total_ms|**bigint**|Il tempo totale espresso in millisecondi tra la generazione e il completamento degli I/O di scrittura. Non ammette i valori Null.|  
|write_io_stall_queued_ms|**bigint**|Il tempo totale espresso in millisecondi tra l'arrivo degli I/O di scrittura e il problema. Si tratta del ritardo introdotto dalla governance delle risorse di I/O. Non ammette i valori Null.|  
|io_issue_violations_total|**int**|Totale delle violazioni di generazione di I/O. Vale a dire, il numero di volte che la frequenza di generazione di I/O era inferiore alla frequenza riservata. Non ammette i valori Null.|  
|io_issue_delay_total_ms|**bigint**|Il tempo totale espresso in millisecondi tra la generazione pianificata e quella effettiva degli I/O. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

