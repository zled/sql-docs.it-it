---
title: sys.index_resumable_operations (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.reviewer: 
ms.service: 
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.index_resumable_operations_TSQL
- sys.indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes
- sys.index_resumable_operations
ms.assetid: 
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53b6aad214f3d1760bb03ff340e5a5dab30c1067
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="indexresumableoperations-transact-sql"></a>index_resumable_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**Sys.index_resumable_operations** è una vista di sistema che esegue il monitoraggio e controlla lo stato di esecuzione corrente per la ricompilazione dell'indice può essere ripristinato.  
**Si applica a**: SQL Database SQL Server 2017 e Azure 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto a cui appartiene (non ammette valori null) dell'indice.|  
|**index_id**|**int**|ID dell'indice (non ammette valori null). **index_id** è univoco solo all'interno dell'oggetto.|
|**name**|**sysname**|Nome dell'indice. **nome** è univoco solo all'interno dell'oggetto.|  
|**sql_text**|**nvarchar(max)**|Testo dell'istruzione DDL T-SQL|
|**last_max_dop**|**smallint**|Ultimo MAX_DOP utilizzato (predefinito = 0)|
|**partition_number**|**int**|Numero di partizione all'interno dell'indice o heap di appartenenza. Per gli indici e tabelle non partizionate o in caso di tutte le partizioni vengono ricompila il valore di questa colonna è NULL.|
|**state**|**tinyint**|Stato operativo per l'indice può essere ripristinato:<br /><br />0 = in esecuzione<br /><br />1=Pause|
|**state_desc**|**nvarchar(60)**|Descrizione dello stato operativo per l'indice può essere ripristinato (in esecuzione o sospesa)|  
|**start_time**|**datetime**|Ora di inizio operazione indice (non ammette valori null)|
|**last_pause_time**|**datatime**| Operazione sull'indice ultimo tempo di sospensione (ammette valori null). NULL se l'operazione è in esecuzione e mai in pausa.|
|**total_execution_time**|**int**|Tempo totale di esecuzione dall'ora di inizio in minuti (non ammette valori null)|
|**percent_complete**|**real**|Indice completamento lo stato di avanzamento dell'operazione nel % (non ammette valori null).|
|**page_count**|**bigint**|Numero totale di pagine di indice allocata per l'operazione di compilazione per il nuovo indice e gli indici di mapping (non ammette valori null). 

## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
   
## <a name="example"></a>Esempio  
 Elencare tutte le operazioni di ricompilazione dell'indice può essere ripristinato che sono in stato di sospensione. 
  
```  
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```  
  
## <a name="see-also"></a>Vedere anche 
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)    
 [Viste del catalogo &#40; Transact-SQL &#41; ](catalog-views-transact-sql.md) [Oggetto viste del catalogo &#40; Transact-SQL &#41; ](object-catalog-views-transact-sql.md) [Sys. Indexes &#40; Transact-SQL &#41; ](sys-xml-indexes-transact-sql.md) [index_columns &#40; Transact-SQL &#41;](sys-index-columns-transact-sql.md)   
 [sys.xml_indexes &#40;Transact-SQL&#41;](sys-xml-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](sys-index-columns-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL&#41;](sys-key-constraints-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](sys-filegroups-transact-sql.md)   
 [sys.partition_schemes &#40;Transact-SQL&#41;](sys-partition-schemes-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query nel catalogo di sistema di SQL Server](querying-the-sql-server-system-catalog-faq.md)   
  
