---
title: Sys.pdw_replicated_table_cache_state (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
author: ronortloff
ms.author: rortloff;barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 700ebe6ee06ebbcccf9c1388cb3a4f8015a26669
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>Sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Restituisce lo stato della cache associata a una tabella replicata da **object_id**.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|L'ID di oggetto per la tabella. Vedere [Sys. Objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** è la chiave per la visualizzazione.||  
|state|**nvarchar (40)**|Lo stato della cache di tabella replicata per questa tabella.|'Nonpronto', 'Pronto'|  
  
## <a name="example"></a>Esempio
In questo esempio crea un join sys.pdw_replicated_table_cache_state con Sys. Tables per recuperare il nome della tabella e lo stato della cache tabella replicata.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Passaggi successivi  
 Per un elenco di tutte le viste del catalogo per SQL Data Warehouse e Parallel Data Warehouse, vedere [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  
