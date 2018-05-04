---
title: MSdbms_map (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdbms_map
- MSdbms_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_map system table
ms.assetid: df67e691-3a50-450a-99c5-8c4a041749ae
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c2845e39b33818e3dd14f6feb0ce88a01d4c8f62
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msdbmsmap-transact-sql"></a>MSdbms_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSdbms_map** tabella contiene informazioni sul tipo di dati di origine, nonché un collegamento per impostazione predefinita informazioni sul tipo di dati di destinazione per le coppie DBMS di origine e di destinazione. Questa tabella è archiviata nel **msdb** database e viene utilizzato per la pubblicazione eterogenea.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**map_id**|**int**|Identifica in modo univoco un mapping di tipi di dati.|  
|**src_dbms_id**|**int**|Identifica il DBMS di origine specificando il relativo **dbms_id** nel [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) tabella.|  
|**dest_dbms_id**|**int**|Identifica il DBMS di destinazione, specificando il relativo **dbms_id** nel [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) tabella.|  
|**src_datatype_id**|**int**|Identifica la **datatype_id** dal [MSdbms_datatype](../../relational-databases/system-tables/msdbms-datatype-transact-sql.md) tabella per il tipo di dati di origine.|  
|**src_len_min**|**bigint**|Lunghezza minima del tipo di dati nel DBMS di origine. Il valore NULL indica che la lunghezza non viene utilizzata.|  
|**src_len_max**|**bigint**|Lunghezza massima del tipo di dati nel DBMS di origine. Il valore NULL indica che la lunghezza non viene utilizzata.|  
|**src_prec_min**|**bigint**|Precisione minima del tipo di dati nel DBMS di origine. Il valore NULL indica che la precisione non viene utilizzata.|  
|**src_prec_max**|**bigint**|Precisione massima del tipo di dati nel DBMS di origine. Il valore NULL indica che la precisione non viene utilizzata.|  
|**src_scale_min**|**int**|Scala minima del tipo di dati nel DBMS di origine. Il valore NULL indica che la scala non viene utilizzata.|  
|**src_scale_max**|**int**|Scala massima del tipo di dati nel DBMS di origine. Il valore NULL indica che la scala non viene utilizzata.|  
|**src_nullable**|**bit**|Specifica se la colonna di destinazione nel mapping ammette valori NULL. Il valore NULL indica che questa definizione non è necessaria.|  
|**default_datatype_mapping_id**|**int**|Identifica il mapping dei tipi di dati predefinito tramite il relativo **map_id** nella tabella [MSdbms_datatype_mapping](../../relational-databases/system-tables/msdbms-datatype-mapping-transact-sql.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Specificare i mapping dei tipi di dati per un server di pubblicazione Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
