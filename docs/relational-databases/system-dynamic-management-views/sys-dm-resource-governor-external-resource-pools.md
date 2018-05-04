---
title: Sys.dm_resource_governor_external_resource_pools (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 05/02/2018
ms.suite: sql
ms.prod: sql
ms.prod_service: database-engine
ms.technology: machine-learning
ms.component: dmv's
ms.reviewer: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pools_TSQL
- sys.dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_external_resource_pools
- sys.dm_resource_governor_external_resource_pools
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7a499aaa0c1377d1f64df4a5aed645c31ca3ebbf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmresourcegovernorexternalresourcepools-transact-sql"></a>Sys.dm_resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Restituisce informazioni sullo stato corrente del pool risorsa esterna, la configurazione corrente del pool di risorse e statistiche del pool di risorse. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Nome colonna      |Tipo di dati      |Description|  
|----------------|---------------|-----------------| 
| external_pool_id|**int**|ID del pool di risorse. Non ammette i valori Null. |
| name|**sysname**|Nome del pool di risorse. Non ammette i valori Null. 
| pool_version|**int**|numero di versione nterno.|
| max_cpu_percent|**int**|Configurazione corrente per la larghezza di banda media massima della CPU concessa per tutte le richieste nel pool di risorse, in caso di contesa di CPU. Non ammette i valori Null. |
| max_processes|**int**|Numero massimo di processi esterni simultanei. Il valore predefinito, 0, non specifica alcun limite. Non ammette i valori Null.|
| max_memory_percent|**int**|Configurazione corrente della percentuale di memoria totale del server utilizzabile dalle richieste in questo pool di risorse. Non ammette i valori Null. |
| statistics_start_time|**datetime**|Ora di reimpostazione delle statistiche per questo pool. Non ammette i valori Null. 
| peak_memory_kb|**bigint**|quantità massima zza di memoria utilizzata, in kilobyte, per il pool di risorse. Non ammette i valori Null. |
| write_io_count|**int**|Il totale degli I/O di scrittura generati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null. |
| read_io_count|**int**|Il totale degli I/O di lettura generati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null. |
| total_cpu_kernel_ms|**bigint**|Tempo totale CPU di un utente in millisecondi dalla reimpostazione delle statistiche di Resource Governor. Non ammette i valori Null. |
| total_cpu_user_ms|**bigint**|Tempo totale CPU di un utente in millisecondi dalla reimpostazione delle statistiche di Resource Governor. Non ammette i valori Null. |
| active_processes_count|**int**|Il numero di processi esterni in esecuzione al momento della richiesta. Non ammette i valori Null. |

 
## <a name="permissions"></a>Autorizzazioni

È richiesta l'autorizzazione `VIEW SERVER STATE`.

## <a name="see-also"></a>Vedere anche  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
