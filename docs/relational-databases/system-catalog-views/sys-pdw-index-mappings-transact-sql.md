---
title: Sys.pdw_index_mappings (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62e71a9468c54f5d921f630d920dfaf4aa222b80
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwindexmappings-transact-sql"></a>Sys.pdw_index_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Gli indici logici viene eseguito il mapping al nome fisico usato sui nodi di calcolo, come evidenziato da una combinazione univoca di **object_id** della tabella che contiene l'indice e **index_id** di un determinato indice all'interno di esso tavolo.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|L'ID di oggetto per la tabella logica in cui è presente l'indice. Vedere [Sys. Objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **physical_name** e **object_id** formano la chiave per la visualizzazione.||  
|index_id|**nvarchar(32)**|ID dell'indice. Vedere [Sys. Indexes &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).||  
|physical_name|**nvarchar(36)**|Il nome dell'indice nei database sui nodi di calcolo.<br /><br /> **physical_name** e **object_id** formano la chiave per la visualizzazione.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Sys.pdw_table_mappings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [Sys.pdw_database_mappings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  
