---
title: Sys.dm_tran_version_store_space_usage (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_version_store_space_usage_TSQL
- sys.dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_tran_version_store_space_usage dynamic management view
ms.assetid: 7ab44517-0351-4f91-bdd9-7cf940f03c51
caps.latest.revision: "10"
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: cfdd2caa03fdd12501580c2584d68f374ee54222
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="sysdmtranversionstorespaceusage-transact-sql"></a>Sys.dm_tran_version_store_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Restituisce una tabella che visualizza lo spazio totale in tempdb utilizzati dai record di archivio versione per ogni database. **Sys.dm_tran_version_store_space_usage** è efficiente e ad alte prestazioni per l'esecuzione non passa tramite l'archivio versione singoli record e restituisce lo spazio di archivio versione aggregati utilizzato in tempdb per ogni database.
  
Ogni record con versione viene archiviato come dato binario con alcune informazioni di rilevamento o stato. Analogamente ai record nelle tabelle di database, i record inclusi nell'archivio delle versioni vengono archiviati in pagine da 8192 byte. In caso di dimensioni superiori a 8192 byte, il record verrà suddiviso in due record distinti.  
  
Poiché il record con versione viene archiviato come dato binario, non si verificheranno problemi in presenza di diverse regole di confronto di database diversi. Utilizzare **sys.dm_tran_version_store_space_usage** per monitorare e pianificare le dimensioni di tempdb in base all'utilizzo di spazio di archivio versione del database in un'istanza di SQL Server.
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID del database del database.|  
|**reserved_page_count**|**bigint**|Conteggio totale delle pagine riservate nel database tempdb per la versione di archiviare i record del database.|  
|**reserved_space_kb**|**bigint**|Spazio totale utilizzato in kilobyte nel database tempdb per versione archiviare i record del database.|  
  
## <a name="permissions"></a>Autorizzazioni  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   

## <a name="examples"></a>Esempi  
 La query seguente consente di determinare lo spazio utilizzato in tempdb dall'archivio delle versioni di ogni database in un'istanza di SQL Server. 
  
```sql  
SELECT 
  DB_NAME(database_id) as 'Database Name',
  reserved_page_count,
  reserved_space_kb 
FROM sys.dm_tran_version_store_space_usage;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Database Name            reserved_page_count reserved_space_kb  
------------------------ -------------------- -----------  
msdb                      0                    0             
AdventureWorks2016        10                   80             
AdventureWorks2016DW      0                    0             
WideWorldImporters        20                   160             
```
 
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative alle transazioni &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
