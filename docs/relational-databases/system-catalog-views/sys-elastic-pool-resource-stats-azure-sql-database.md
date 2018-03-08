---
title: Sys.elastic_pool_resource_stats (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 09/30/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- Azure SQL Database
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7af69bdd1f98560d3a6ae9699551b4f3062f68c6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="syselasticpoolresourcestats-azure-sql-database"></a>Sys.elastic_pool_resource_stats (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce statistiche di utilizzo delle risorse per tutti i pool di database elastico in un server logico. Per ogni pool di database elastico è disponibile una riga per ogni 15 secondi reporting finestra (quattro righe al minuto). Sono inclusi CPU, IO, Log, il consumo di archiviazione e utilizzo/sessione di richieste simultanee da tutti i database nel pool. Questi dati vengono mantenuti per 14 giorni. 
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] (V12).|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Ora UTC indicante l'inizio dell'intervallo di reporting di 15 secondi.|  
|**end_time**|**datetime2**|Ora UTC che indica la fine del 15 secondo intervallo di reporting.|  
|**elastic_pool_name**|**nvarchar(128)**|Nome del pool di database elastico.|  
|**avg_cpu_percent**|**decimal(5,2)**|Utilizzo di calcolo Media in percentuale del limite del pool.|  
|**avg_data_io_percent**|**decimal(5,2)**|Utilizzo dei / o medio espresso come percentuale del limite del pool.|  
|**avg_log_write_percent**|**decimal(5,2)**|Medio di scrittura in percentuale del limite del pool di utilizzo delle risorse.|  
|**avg_storage_percent**|**decimal(5,2)**|Utilizzo di archiviazione medio, espresso in percentuale del limite di archiviazione del pool.|  
|**max_worker_percent**|**decimal(5,2)**|Massimi simultanee processi di lavoro (richieste) espresso come percentuale del limite del pool.|  
|**max_session_percent**|**decimal(5,2)**|Numero massimo di sessioni simultaneo espresso come percentuale del limite del pool.|  
|**elastic_pool_dtu_limit**|**int**|Max pool elastico DTU impostazione corrente per questo pool elastico durante questo intervallo.|  
|**elastic_pool_storage_limit_mb**|**bigint**|L'impostazione per questo pool elastico in megabyte durante questo intervallo corrente limite di archiviazione massima del pool elastico.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa vista è presente nel database master del server logico. È necessario essere connessi al database master per query **sys.elastic_pool_resource_stats**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **dbmanager** ruolo.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce i dati di utilizzo delle risorse ordinati in base l'ora più recente per tutti i pool di database elastico nel server logico corrente.  
  
```  
SELECT * FROM sys.elastic_pool_resource_stats   
ORDER BY end_time DESC;  
```  
  
 L'esempio seguente calcola la media DTU percentuale di utilizzo per un pool specificato.  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.elastic_pool_resource_stats   
WHERE elastic_pool_name = '<your pool name>'   
ORDER BY end_time DESC;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Crescita esponenziale AppSense con i database elastici](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Creare e gestire un pool di database elastico del Database SQL (anteprima)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [Sys. resource_stats &#40; Database SQL di Azure &#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Sys.dm db_resource_stats &#40; Database SQL di Azure &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
