---
title: Sys.pdw_table_mappings (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 1af14fe0-e562-4f48-a7f0-783f300a88ac
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 90b54eb0c5d844a1f6ecd747e46cc7bbd863262d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwtablemappings-transact-sql"></a>Sys.pdw_table_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Collega tabelle utente ai nomi di oggetto interno per **object_id**.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar(36)**|Il nome fisico per la tabella.<br /><br /> **physical_name** e **object_id** formano la chiave per la visualizzazione.||  
|object_id|**int**|L'ID di oggetto per la tabella. Vedere [Sys. Objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **physical_name** e **object_id** formano la chiave per la visualizzazione.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Sys.pdw_index_mappings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [Sys.pdw_database_mappings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  
