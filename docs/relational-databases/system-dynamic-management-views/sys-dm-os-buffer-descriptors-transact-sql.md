---
title: sys.dm_os_buffer_descriptors (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_buffer_descriptors_TSQL
- dm_os_buffer_descriptors_TSQL
- sys.dm_os_buffer_descriptors
- dm_os_buffer_descriptors
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_buffer_descriptors dynamic management view
ms.assetid: 012aab95-8888-4f35-9ea3-b5dff6e3f60f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e35b3cd5c0b10bce5ed66f8c68babcebc96ae95
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosbufferdescriptors-transact-sql"></a>sys.dm_os_buffer_descriptors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni relative a tutte le pagine di dati incluse nel pool di buffer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'output di questa vista può essere utilizzato per determinare la distribuzione delle pagine del database nel pool di buffer in base al database, all'oggetto o al tipo. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] questa DMV restituisce inoltre informazioni sulle pagine di dati nel file di estensione del pool di buffer. Per ulteriori informazioni, vedere [estensione del Pool di Buffer](../../database-engine/configure-windows/buffer-pool-extension.md).  
  
 Quando una pagina di dati viene letta dal disco, viene copiata nel pool di buffer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e memorizzata nella cache per il riutilizzo. Ogni pagina di dati memorizzata nella cache è associata a un descrittore di buffer. I descrittori di buffer identificano in modo univoco ogni pagina di dati attualmente memorizzata nella cache in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. sys.dm_os_buffer_descriptors restituisce le pagine memorizzate nella cache per tutti i database utente e di sistema. incluse le pagine associate al database Resource.  
  
> **Nota:** da chiamare [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_buffer_descriptors**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database associato alla pagina nel pool di buffer. Ammette i valori Null.|  
|file_id|**int**|ID del file in cui è archiviata l'immagine persistente della pagina. Ammette i valori Null.|  
|page_id|**int**|ID della pagina all'interno del file. Ammette i valori Null.|  
|page_level|**int**|Livello di indice della pagina. Ammette i valori Null.|  
|allocation_unit_id|**bigint**|ID dell'unità di allocazione della pagina. Questo valore può essere utilizzato per unire in join sys.allocation_units. Ammette i valori Null.|  
|page_type|**nvarchar(60)**|Tipo di pagina, ad esempio pagina di dati o pagina di indice. Ammette i valori Null.|  
|row_count|**int**|Numero di righe nella pagina. Ammette i valori Null.|  
|free_space_in_bytes|**int**|Quantità di spazio disponibile, in byte, nella pagina. Ammette i valori Null.|  
|is_modified|**bit**|1 = La pagina è stata modificata dopo essere stata letta dal disco. Ammette i valori Null.|  
|numa_node|**int**|Nodo NUMA (non-uniform memory access) per il buffer. Ammette i valori Null.|  
|read_microsec|**bigint**|Tempo effettivo (in microsecondi) necessario per leggere la pagina nel buffer. Questo numero viene reimpostato quando si riutilizza il buffer. Ammette i valori Null.|  
|is_in_bpool_extension|**bit**|1 = pagina è inclusa l'estensione del pool di buffer. Ammette i valori Null.|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  
  
## <a name="remarks"></a>Osservazioni  
 Sys.dm os_buffer_descriptors restituisce le pagine che vengono utilizzate per il database delle risorse. Sys.dm os_buffer_descriptors non restituisce informazioni sulle pagine libere o prelevate, né sulle pagine in cui si sono verificati errori quando sono stati letti.  
  
|From|Per|Il|Relazione|  
|----------|--------|--------|------------------|  
|sys.dm_os_buffer_descriptors|sys.databases|database_id|molti-a-uno|  
|sys.dm_os_buffer_descriptors|\<userdb>.sys.allocation_units|allocation_unit_id|molti-a-uno|  
|sys.dm_os_buffer_descriptors|\<userdb>.sys.database_files|file_id|molti-a-uno|  
|sys.dm_os_buffer_descriptors|sys.dm_os_buffer_pool_extension_configuration|file_id|molti-a-uno|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-cached-page-count-for-each-database"></a>A. Restituzione del conteggio delle pagine memorizzate nella cache per ogni database  
 Nell'esempio seguente viene restituito il conteggio delle pagine caricate per ogni database.  
  
```  
SELECT COUNT(*)AS cached_pages_count  
    ,CASE database_id   
        WHEN 32767 THEN 'ResourceDb'   
        ELSE db_name(database_id)   
        END AS database_name  
FROM sys.dm_os_buffer_descriptors  
GROUP BY DB_NAME(database_id) ,database_id  
ORDER BY cached_pages_count DESC;  
```  
  
### <a name="b-returning-cached-page-count-for-each-object-in-the-current-database"></a>B. Restituzione del conteggio delle pagine memorizzate nella cache per ogni oggetto nel database corrente  
 Nell'esempio seguente viene restituito il conteggio delle pagine caricate per ogni oggetto nel database corrente.  
  
```  
SELECT COUNT(*)AS cached_pages_count   
    ,name ,index_id   
FROM sys.dm_os_buffer_descriptors AS bd   
    INNER JOIN   
    (  
        SELECT object_name(object_id) AS name   
            ,index_id ,allocation_unit_id  
        FROM sys.allocation_units AS au  
            INNER JOIN sys.partitions AS p   
                ON au.container_id = p.hobt_id   
                    AND (au.type = 1 OR au.type = 3)  
        UNION ALL  
        SELECT object_name(object_id) AS name     
            ,index_id, allocation_unit_id  
        FROM sys.allocation_units AS au  
            INNER JOIN sys.partitions AS p   
                ON au.container_id = p.partition_id   
                    AND au.type = 2  
    ) AS obj   
        ON bd.allocation_unit_id = obj.allocation_unit_id  
WHERE database_id = DB_ID()  
GROUP BY name, index_id   
ORDER BY cached_pages_count DESC;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 
 [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Database Resource](../../relational-databases/databases/resource-database.md)   
 [Sys.dm_os_buffer_pool_extension_configuration &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-pool-extension-configuration-transact-sql.md)  
  
  


