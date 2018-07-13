---
title: sys.pdw_replicated_table_cache_state (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 8d78a537bb2de2ee880551afd3667f308b49ce83
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926052"
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Restituisce lo stato della cache associata a una tabella replicata dal **object_id**.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|L'ID di oggetto per la tabella. Visualizzare [Sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** è la chiave per questa visualizzazione.||  
|state|**nvarchar(40)**|Lo stato della cache di tabella replicata per questa tabella.|Non 'pronto', 'Pronto'|  
  
## <a name="example"></a>Esempio
In questo esempio crea un join pdw_replicated_table_cache_state con Sys. Tables per recuperare il nome della tabella e lo stato della cache di tabella replicata.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Passaggi successivi  
 Per un elenco di tutte le viste del catalogo per SQL Data Warehouse e Parallel Data Warehouse, vedere [viste del catalogo di Parallel Data Warehouse e SQL Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  
