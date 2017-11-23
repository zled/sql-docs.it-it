---
title: Sys. Partitions (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- partitions
- partitions_TSQL
- sys.partitions_TSQL
- sys.partitions
dev_langs: TSQL
helpviewer_keywords: sys.partitions catalog view
ms.assetid: 1c19e1b1-c925-4dad-a652-581692f4ab5e
caps.latest.revision: "60"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 658d0d22bf2dc757854626f792cc49429ab98916
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitions-transact-sql"></a>sys.partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Contiene una riga per ogni partizione di tutte le tabelle e per gran parte degli indici nel database. I tipi di indici speciali, ad esempio Full-Text, Spatial e XML, non sono inclusi in questa vista. Tutti gli indici e le tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contengono almeno una partizione, anche se non esplicitamente partizionati.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|Indica l'ID della partizione. Valore univoco all'interno di un database.|  
|object_id|**int**|Indica l'ID dell'oggetto a cui appartiene la partizione. Ogni tabella o vista è costituita da almeno una partizione.|  
|index_id|**int**|Indica l'ID dell'indice nell'oggetto a cui appartiene la partizione.<br /><br /> 0 = heap<br />1 = indice cluster<br />2 o maggiore = indice non cluster|  
|partition_number|**int**|Numero di partizione in base 1 all'interno dell'indice o dell'heap di appartenenza. Per le tabelle o gli indici non partizionati, il valore di questa colonna è 1.|  
|hobt_id|**bigint**|Indica l'ID dell'heap di dati o dell'albero B contenente le righe per la partizione.|  
|rows|**bigint**|Indica il numero approssimativo di righe nella partizione.|  
|filestream_filegroup_id|**smallint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Indica l'ID del filegroup FILESTREAM archiviato su questa partizione.|  
|data_compression|**tinyint**|Indica lo stato di compressione per ogni partizione:<br /><br /> 0 = NONE <br />1 = ROW <br />2 = PAGE <br />3 = COLUMNSTORE: **si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />4 = COLUMNSTORE_ARCHIVE: **si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> **Nota:** indici Full-text verranno compressi in qualsiasi edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|data_compression_desc|**nvarchar(60)**|Indica lo stato di compressione per ogni partizione. I valori possibili per le tabelle rowstore sono NONE, ROW e PAGE. I valori possibili per le tabelle columnstore sono COLUMNSTORE e COLUMNSTORE_ARCHIVE.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** . Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query nel catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
