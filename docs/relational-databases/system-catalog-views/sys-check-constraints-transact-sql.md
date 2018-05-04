---
title: Sys. CHECK_CONSTRAINTS (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.check_constraints
- sys.check_constraints_TSQL
- check_constraints_TSQL
- check_constraints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.check_constraints catalog view
ms.assetid: 940ebc5e-44ba-4dae-8b29-da94f2d1d6c4
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 43ccc527143be26d4cee4d2e4ce55e8fb37d3abb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syscheckconstraints-transact-sql"></a>sys.check_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni oggetto che rappresenta un vincolo CHECK, con **sys** = "C".  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<Colonne ereditate da Sys. Objects >**||Per un elenco delle colonne ereditate da questa vista, vedere [Sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_disabled**|**bit**|Il vincolo CHECK è disabilitato.|  
|**is_not_for_replication**|**bit**|Il vincolo CHECK è stato creato con l'opzione NOT FOR REPLICATION.|  
|**is_not_trusted**|**bit**|Il vincolo CHECK non è stato verificato dal sistema per tutte le righe.|  
|**parent_column_id**|**int**|0 indica un vincolo CHECK a livello di tabella.<br /><br /> Un valore diverso da zero indica che si tratta di un vincolo CHECK a livello di colonna definito nella colonna con il valore ID specificato.|  
|**Definizione**|**nvarchar(max)**|Espressione SQL che definisce questo vincolo CHECK.|  
|**uses_database_collation**|**bit**|1 = La corretta valutazione della definizione del vincolo dipende dalle regole di confronto predefinite del database; altrimenti, 0. Tale dipendenza impedisce la modifica delle regole di confronto predefinite del database.|  
|**is_system_named**|**bit**|1 = Il nome è stato generato dal sistema.<br /><br /> 0 = Nome specificato dall'utente.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
