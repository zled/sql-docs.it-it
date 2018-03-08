---
title: sys.pdw_nodes_indexes (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 261bcb7f-a906-4979-b274-bc5f1aa66426
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 77d90e50801abe9a8d9bd6c9ed67223486630b9e
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwnodesindexes-transact-sql"></a>sys.pdw_nodes_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Restituisce gli indici per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|ID dell'oggetto a cui appartiene l'indice.||  
|name|**sysname**|Nome dell'indice. Nome è univoco solo all'interno dell'oggetto. NULL = Heap||  
|index_id|**int**|ID dell'indice. index_ID è univoco solo all'interno dell'oggetto.<br /><br /> 0 = heap<br /><br /> 1 = indice cluster<br /><br /> > 1 = indice Non cluster||  
|tipo|**tinyint**|Tipo di indice:<br /><br /> 0 = heap<br /><br /> 1 = Cluster<br /><br /> 2 = Non cluster<br /><br /> 5 = indice columnstore ottimizzati memoria xVelocity di cluster|  
|type_desc|**nvarchar(60)**|Descrizione del tipo di indice:<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> COLUMNSTORE CLUSTER||  
|is_unique|**bit**|0 = Indice non univoco.|Sempre 0.|  
|data_space_id|**int**|ID dello spazio dati per l'indice. Lo spazio dati può essere un filegroup o uno schema di partizione.<br /><br /> 0 = object_id è una funzione con valori di tabella.||  
|ignore_dup_key|**bit**|0 = IGNORE_DUP_KEY è OFF.|Sempre 0.|  
|is_primary_key|**bit**|1 = L'indice fa parte di un vincolo PRIMARY KEY.|Sempre 0.|  
|is_unique_constraint|**bit**|1 = L'indice fa parte di un vincolo UNIQUE.|Sempre 0.|  
|fill_factor|**tinyint**|> 0 = Percentuale FILLFACTOR utilizzata al momento della creazione o ricostruzione dell'indice.<br /><br /> 0 = Valore predefinito|Sempre 0.|  
|is_padded|**bit**|0 = PADINDEX è OFF.|Sempre 0.|  
|is_disabled|**bit**|1 = L'indice è disabilitato.<br /><br /> 0 = L'indice non è disabilitato.||  
|is_hypothetical|**bit**|0 = L'indice non è ipotetico.|Sempre 0.|  
|allow_row_locks|**bit**|1 = L'indice consente blocchi di riga.|Sempre 1.|  
|allow_page_locks|**bit**|1 = L'indice consente blocchi di pagina.|Sempre 1.|  
|has_filter|**bit**|0 = L'indice non dispone di un filtro.|Sempre 0.|  
|filter_definition|**nvarchar(max)**|Espressione per il subset di righe incluso nell'indice filtrato.|Sempre NULL.|  
|pdw_node_id|**int**|Identificatore univoco di un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nodo.|NOT NULL|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
