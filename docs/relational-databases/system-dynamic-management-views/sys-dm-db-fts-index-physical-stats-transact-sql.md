---
title: Sys.dm_db_fts_index_physical_stats (Transact-SQL) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_fts_index_physical_stats_TSQL
- dm_db_fts_index_physical_stats
- dm_db_fts_index_physical_stats_TSQL
- sys.dm_db_fts_index_physical_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_fts_index_physical_stats dynamic management view
ms.assetid: 997c3278-3630-47f6-ada3-190b6c16ce0e
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 38cb567f71714f528a20a6983c7f45a82c4ec306
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39541822"
---
# <a name="sysdmdbftsindexphysicalstats-transact-sql"></a>sys.dm_db_fts_index_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni indice full-text o semantico in ogni tabella a cui è associato un indice full-text o semantico.  
  
||||  
|-|-|-|  
|**Nome colonna**|**Tipo**|**Descrizione**|  
|**object_id**|INT|ID oggetto della tabella contenente l'indice.|  
|**fulltext_index_page_count**|**bigint**|Dimensione logica dell'estrazione in numero di pagine di indice.|  
|**keyphrase_index_page_count**|**bigint**|Dimensione logica dell'estrazione in numero di pagine di indice.|  
|**similarity_index_page_count**|**bigint**|Dimensione logica dell'estrazione in numero di pagine di indice.|  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Per altre informazioni, vedere [gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md).  
  
## <a name="metadata"></a>Metadati  
 Per informazioni sullo stato dell'indicizzazione semantica, eseguire una query sulle DMV seguenti:  
  
-   [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="permissions"></a>Permissions

Sul [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario `VIEW SERVER STATE` autorizzazione.   
Sul [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], è necessario il `VIEW DATABASE STATE` autorizzazione nel database.   

## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come eseguire una query per la dimensione logica di ogni indice full-text o semantico in ogni tabella cui è associato un indice full-text o semantico:  
  
```  
SELECT * FROM sys.dm_db_fts_index_physical_stats;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire e monitorare la ricerca semantica](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
