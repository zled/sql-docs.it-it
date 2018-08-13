---
title: Sys.sql_modules (Transact-SQL) | Documenti di Microsoft
ms.custom: ''
ms.date: 01/09/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sql_modules_TSQL
- sql_modules
- sql_modules_TSQL
- sys.sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_modules catalog view
ms.assetid: 23d3ccd2-f356-4d89-a2cd-bee381243f99
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 7277009805307ed5f9208227cc98c72df3fc3e2a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39542351"
---
# <a name="syssqlmodules-transact-sql"></a>sys.sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni oggetto che è un modulo SQL definita dal linguaggio in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], inclusi in modo nativo compilato funzione scalare definita dall'utente. Agli oggetti di tipo P, RF, V, TR, FN, IF, TF e R è associato un modulo SQL. In questa vista anche agli oggetti predefiniti autonomi, ovvero gli oggetti di tipo D, sono associati a una definizione di modulo SQL. Per una descrizione di questi tipi, vedere la **tipo** colonna di [sys](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) visualizzazione catalogo.  
  
 Per altre informazioni, vedere [Funzioni scalari definite dall'utente per OLTP in memoria](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto contenitore. Valore univoco all'interno di un database.|  
|**Definizione**|**nvarchar(max)**|Testo SQL che definisce il modulo. Questo valore può essere ottenuto anche utilizzando il [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) funzione incorporata.<br /><br /> NULL = Crittografato.|  
|**uses_ansi_nulls**|**bit**|Modulo creato con SET ANSI_NULLS ON.<br /><br /> È sempre = 0 per regole e impostazioni predefinite.|  
|**uses_quoted_identifier**|**bit**|Modulo creato con SET QUOTED_IDENTIFIER ON.|  
|**is_schema_bound**|**bit**|Modulo creato con l'opzione SCHEMABINDING.<br /><br /> Contiene sempre il valore 1 per le stored procedure compilate in modo nativo.|  
|**uses_database_collation**|**bit**|1 = La definizione del modulo associato a uno schema dipende dalle regole di confronto predefinite del database per una corretta valutazione; altrimenti, 0. Tale dipendenza impedisce la modifica delle regole di confronto predefinite del database.|  
|**is_recompiled**|**bit**|Procedura creata con l'opzione WITH RECOMPILE.|  
|**null_on_null_input**|**bit**|Modulo dichiarato per restituire un output NULL per ogni input NULL.|  
|**execute_as_principal_id**|**Int**|ID dell'entità database EXECUTE AS.<br /><br /> Questo valore è NULL per impostazione predefinita e se viene utilizzato EXECUTE AS CALLER.<br /><br /> ID dell'oggetto specificato se principal EXECUTE AS SELF o EXECUTE AS \<principale >.<br /><br /> -2 = EXECUTE AS OWNER.|  
|**uses_native_compilation**|**bit**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].<br /><br /> 0 = non compilata in modo nativo<br /><br /> 1 = compilata in modo nativo<br /><br /> Il valore predefinito è 0.|  
  
## <a name="remarks"></a>Note  
 L'espressione SQL per un vincolo predefinito, l'oggetto di tipo D, si trova nella [sys.default_constraints](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md) visualizzazione catalogo. L'espressione SQL per un vincolo CHECK, oggetto di tipo C, si trova nella [sys.check_constraints](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md) visualizzazione catalogo.  
  
 Questa informazione è descritta anche in [sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti il nome, il tipo e la definizione di ogni modulo del database corrente.  
  
```  
SELECT sm.object_id, OBJECT_NAME(sm.object_id) AS object_name, o.type, o.type_desc, sm.definition  
FROM sys.sql_modules AS sm  
JOIN sys.objects AS o ON sm.object_id = o.object_id  
ORDER BY o.type;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [L'esecuzione di query nel catalogo di sistema SQL Server domande frequenti](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
