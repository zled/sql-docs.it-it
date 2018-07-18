---
title: sys.dm_column_store_object_pool (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a8a58ca7-0a7d-4786-bfd9-e8894bd345dd
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 18faadc4dbcd4b2966c8e922aed01127b13c8baa
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmcolumnstoreobjectpool-transact-sql"></a>sys.dm_column_store_object_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Restituisce i conteggi di diversi tipi di utilizzo di pool di oggetti della memoria per gli oggetti indice columnstore.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|`database_id`|`int`|ID del database. È univoco all'interno di un'istanza di un database di SQL Server o un server di database SQL di Azure. |  
|`object_id`|`int`|ID dell'oggetto. L'oggetto è uno degli oggetti di object_type. | 
|`index_id`|`int`|ID dell'indice columnstore.|  
|`partition_number`|`bigint`|Numero di partizione in base 1 all'interno dell'indice o heap. Ogni tabella o vista che include almeno una partizione.| 
|`column_id`|`int`|ID della colonna columnstore. È NULL per DELETE_BITMAP.| 
|`row_group_id`|`int`|ID del gruppo di righe.|
|`object_type`|`smallint`|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|`object_type_desc`|`nvarchar(60)`|COLUMN_SEGMENT – un segmento di colonna. `object_id` è l'ID del segmento. Un segmento archivia tutti i valori per una colonna all'interno di un gruppo di righe. Ad esempio, se una tabella ha 10 colonne, esistono 10 segmenti di colonna per ogni gruppo di righe. <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY – dizionario globale contenente informazioni per tutti i segmenti di colonna nella tabella di ricerca.<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY - un dizionario locale associato a una colonna.<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY: un'altra rappresentazione del dizionario globale. Fornisce una ricerca inversa del valore dictionary_id. Utilizzato per la creazione di segmenti compressi come parte del motore di Tuple o il caricamento Bulk.<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP: Elimina una bitmap che tiene traccia di segmento. È una bitmap di eliminazione per ogni partizione.|  
|`access_count`|`int`|Numero di lettura o scrittura accede a questo oggetto.|  
|`memory_used_in_bytes`|`bigint`|Memoria utilizzata da questo oggetto nel pool di oggetti.|  
|`object_load_time`|`datetime`|Ora per Quando object_id è stato introdotto nel pool di oggetti.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
 
## <a name="see-also"></a>Vedere anche  
  
 [Funzioni a gestione dinamica e DMV correlate all'indice &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  
