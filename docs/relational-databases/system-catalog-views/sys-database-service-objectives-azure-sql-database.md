---
title: Sys.database_service_objectives (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 08/30/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- Pool elastico
- pool elastico, gestione
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: d222a06a64d53ab26d19206f846edadf69e613ba
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>Sys.database_service_objectives (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Restituisce l'edizione (livello di servizio), l'obiettivo di servizio (livello di prezzo) e nome del pool elastico, se presente, per un database SQL di Azure o un Data Warehouse di SQL Azure. Se connessi al database master in un server di Database SQL di Azure, restituisce informazioni su tutti i database. Per Azure SQL Data Warehouse, è necessario essere connessi al database master.  
  
  
 Per informazioni sui prezzi, vedere [opzioni del Database SQL e le prestazioni: prezzi di Database SQL](https://azure.microsoft.com/en-us/pricing/details/sql-database/) e [SQL Data Warehouse prezzi](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Per modificare le impostazioni del servizio, vedere [ALTER DATABASE (Database SQL di Azure)](../../t-sql/statements/alter-database-azure-sql-database.md) e [ALTER DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
  
 La vista sys.database_service_objectives contiene le colonne seguenti.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|int|L'ID del database, univoco all'interno di un'istanza del server di Database SQL di Azure. Attive con [Sys. Databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|edition|sysname|Il livello di servizio per il database o data warehouse: **base**, **Standard**, **Premium**, **generale**,  **Business critico**, o **Data Warehouse**.|  
|service_objective|sysname|Il piano tariffario del database. Se il database è in un pool elastico, restituisce **ElasticPool**.<br /><br /> Nel **base** livello, restituisce **base**.<br /><br /> Solo i database in un livello di servizio standard restituisce i valori validi correnti per questo livello.<br /><br /> Solo i database in un livello premium restituisce i valori validi correnti per questo livello di servizio.<br /><br />Singolo database nel livello di servizio generico restituisce i valori validi correnti per questo livello di servizio.<br /><br />Singolo database nel livello di servizio Business Critical restituisce i valori validi correnti per questo livello di servizio.<br /><br /> SQL Data Warehouse restituisce i valori validi correnti per SQL Data Warehouse.|  
|elastic_pool_name|sysname|Il nome del [pool elastico](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) al quale appartiene il database. Restituisce **NULL** se il database è un singolo database o un warehoue di dati.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede **dbManager** autorizzazione per il database master.  A livello di database, l'utente deve essere l'autore o il proprietario.  
  
## <a name="examples"></a>Esempi  
 Questo esempio può essere eseguito nel database master o nei database utente. La query restituisce il nome del servizio e informazioni di livello delle prestazioni dei database.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
