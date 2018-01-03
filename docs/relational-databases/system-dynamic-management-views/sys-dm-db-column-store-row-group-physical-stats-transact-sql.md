---
title: db_column_store_row_group_physical_stats (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_column_store_row_group_physical_stats_TSQL
- sys.dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_db_column_store_row_group_physical_stats
- sys.dm_db_column_store_row_group_physical_stats dynamic management view
caps.latest.revision: "15"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 86b9d5993b3108fd1b89bf7be10477ffaeb22d7b
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="sysdmdbcolumnstorerowgroupphysicalstats-transact-sql"></a>db_column_store_row_group_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Vengono fornite informazioni a livello di gruppo di righe corrente su tutti gli indici columnstore nel database corrente.  
  
 Estende la vista del catalogo [column_store_row_groups &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID della tabella sottostante.|  
|**index_id**|**int**|ID dell'indice columnstore in *object_id* tabella.|  
|**numero_partizione**|**int**|ID della partizione della tabella che contiene *row_group_id*. È possibile utilizzare il partition_number per creare un join di questa DMV a sys.partitions.|  
|**row_group_id**|**int**|ID del gruppo di righe. Per le tabelle partizionate, è univoco all'interno della partizione.<br /><br /> -1 per una coda in memoria.|  
|**delta_store_hobt_id**|**bigint**|Hobt_id per un gruppo di righe nell'archivio delta.<br /><br /> NULL se il gruppo di righe non è presente nell'archivio delta.<br /><br /> NULL per la parte finale di una tabella in memoria.|  
|**state**|**tinyint**|Numero di ID associato *a state_description*.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED<br /><br /> 4 = RIMOZIONE DEFINITIVA<br /><br /> COMPRESSED è l'unico stato che si applica alle tabelle in memoria.|  
|**state_desc**|**nvarchar(60)**|Descrizione dello stato del gruppo di righe:<br /><br /> INVISIBILE: un gruppo di righe che si sta compilando. Ad esempio <br />Un gruppo di righe nel columnstore è INVISIBILE, mentre i dati da comprimere. Al termine della compressione è un'opzione Cambia metadati lo stato della riga columnstore gruppo da INVISIBILE a COMPRESSED e lo stato del gruppo di righe deltastore da chiuso a TOMBSTONE.<br /><br /> OPEN: un gruppo di righe deltastore che accetta nuove righe. Un gruppo di righe aperto presenta ancora il formato rowstore e non è stato compresso nel formato columnstore.<br /><br /> CLOSED: un gruppo di righe nell'archivio delta che contiene il numero massimo di righe ed è in attesa per il processo tuple-mover eseguirne la compressione nel columnstore.<br /><br /> COMPRESSED: un gruppo di righe che verrà compressi con la compressione columnstore e archiviato nel columnstore.<br /><br /> TOMBSTONE: un gruppo di righe che è stato in precedenza nel deltastore e non più utilizzato.|  
|**total_rows**|**bigint**|Numero di righe fisiche archiviato nel gruppo di righe. Per i gruppi di righe compressi, incluse le righe contrassegnate eliminate.|  
|**deleted_rows**|**bigint**|Numero di righe archiviate fisicamente in un gruppo di righe compresso vengono contrassegnati per l'eliminazione.<br /><br /> 0 per i gruppi di righe presenti nell'archivio delta.|  
|**size_in_bytes**|**bigint**|Dimensioni combinate, in byte, di tutte le pagine di questo gruppo di righe. Questa dimensione non include la dimensione necessaria per archiviare i metadati o i dizionari condivisi.|  
|**trim_reason**|**tinyint**|Motivo che ha attivato il gruppo di righe compressi avere minore il numero massimo di righe.<br /><br /> 0 – UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1 - NO_TRIM<br /><br /> 2 - BULKLOAD<br /><br /> 3 – REORG<br /><br /> 4-DICTIONARY_SIZE<br /><br /> 5-MEMORY_LIMITATION<br /><br /> 6-RESIDUAL_ROW_GROUP<br /><br /> 7 - STATS_MISMATCH<br /><br /> 8 - ECCESSO|  
|**trim_reason_desc**|**nvarchar(60)**|Descrizione di *trim_reason*.<br /><br /> 0 – UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION: si è verificato durante l'aggiornamento dalla versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 - NO_TRIM: Il gruppo di righe non eliminato. Il gruppo di righe è stata compressa con un massimo di 1,048,476 righe.  Il numero di righe potrebbe essere inferiore se è stato eliminato un subsset di righe dopo che è stato chiuso il rowgroup delta<br /><br /> 2: caricamento BULK: La dimensione del batch di caricamento bulk limitato il numero di righe.<br /><br /> 3 – REORG: Forzare la compressione come parte del comando REORG.<br /><br /> 4-DICTIONARY_SIZE: Dimensioni del dizionario di aumento delle dimensioni troppo grandi per comprimere tutte le righe contemporaneamente.<br /><br /> 5-MEMORY_LIMITATION: Non disponibile memoria sufficiente per comprimere tutte le righe contemporaneamente.<br /><br /> 6-RESIDUAL_ROW_GROUP: Chiuso come parte dell'ultimo gruppo di righe con milioni di righe < 1 durante l'operazione di compilazione indice<br /><br /> STATS_MISMATCH: solo per columnstore nella tabella in memoria. Se indicato in modo non corretto statistiche > = 1 milione di righe completi della parte finale ma è stato rilevato un numero inferiore, disporrà di < 1 milioni di righe nel rowgroup compresso<br /><br /> ECCESSO: solo per columnstore nella tabella in memoria. Se coda dispone di milioni di righe completo > 1, le ultime righe rimanenti batch vengono compressi se il numero è compreso tra 100 KB e 1 milione|  
|**transition_to_compressed_state**|TINYINT|Viene illustrato come il rowgroup è stata spostata dal deltastore in uno stato compresso nel columnstore.<br /><br /> 1 - NOT_APPLICABLE<br /><br /> 2 – INDEX_BUILD<br /><br /> 3 – TUPLE_MOVER<br /><br /> 4-REORG_NORMAL<br /><br /> 5-REORG_FORCED<br /><br /> 6 - BULKLOAD<br /><br /> 7 - UNIONE|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE: l'operazione non è applicabile per il deltastore. O, il rowgroup è stato compresso prima di eseguire l'aggiornamento a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] nel qual caso non viene mantenuta la cronologia.<br /><br /> Creare un indice INDEX_BUILD – o ricostruzione dell'indice compresso il rowgroup.<br /><br /> TUPLE_MOVER: il motore di tuple in esecuzione in background compressa il rowgroup. Ciò si verifica dopo che il rowgroup stato cambia da OPEN a chiuso.<br /><br /> REORG_NORMAL: l'operazione di riorganizzazione, ALTER INDEX... RIORGANIZZA spostato il rowgroup chiuso dal deltastore nel columnstore. Questo si è verificato prima che il motore di tuple avuto tempo per spostare il gruppo di righe.<br /><br /> REORG_FORCED: questo gruppo di righe è stato aperto nel deltastore e che è stato terminato nel columnstore prima conteneva un numero di righe completo.<br /><br /> BULKLOAD-un'operazione di caricamento bulk compressi i rowgroup direttamente senza usare il deltastore.<br /><br /> MERGE: un'operazione di unione consolidati uno o più gruppi di righe in questo gruppo di righe e quindi eseguita la compressione columnstore.|  
|**has_vertipaq_optimization**|bit|Ottimizzazione di Vertipaq la modifica dell'ordine delle righe nel gruppo di righe per ottenere la compressione maggiore migliora la compressione columnstore. Questa ottimizzazione viene eseguita automaticamente nella maggior parte dei casi. Esistono due casi Vertipaq ottimizzazione non viene utilizzato:<br/>  A. Quando un rowgroup delta viene spostato nel columnstore e sono presenti uno o più indici non cluster per l'indice columnstore, in questo caso ottimizzazione Vertipaq viene ignorata per ridurre al minimo le modifiche per l'indice di mapping;<br/> B. per gli indici columnstore nelle tabelle con ottimizzazione per la memoria. <br /><br /> 0 = No<br /><br /> 1 = Sì|  
|**generazione**|BIGINT|Generazione di gruppo di righe associata a questo gruppo di righe.|  
|**created_time**|datetime2|Ora di creazione di questo gruppo di righe.<br /><br /> NULL per un indice columnstore in una tabella in memoria.|  
|**closed_time**|datetime2|Ora di chiusura di questo gruppo di righe.<br /><br /> NULL per un indice columnstore in una tabella in memoria.|  
  
## <a name="results"></a>Risultati  
 Restituisce una riga per ogni gruppo di righe nel database corrente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Queste autorizzazioni sono necessarie:  
  
-   Autorizzazione CONTROL per la tabella.  
  
-   Autorizzazione VIEW DATABASE STATE nel database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calculate-fragmentaton-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. Calcolare fragmentaton per decidere quando riorganizzare o ricompilare un indice columnstore.  
 Per gli indici columnstore, la percentuale di righe eliminate è un metodo efficace per la frammentazione di un gruppo di righe. Quando la frammentazione è 20% o più che si consiglia di rimuovere le righe eliminate.  Per esempi, vedere [deframmentazione degli indici Columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md).  
  
 In questo esempio unisce **db_column_store_row_group_physical_stats** con altri sistemi di tabelle e quindi calcola il `Fragmentation` colonna come stima dell'efficienza di ogni gruppo di righe nel database corrente.     Per trovare informazioni su una singola tabella, rimuovere il commento trattini davanti il **dove** clausola e specificare un nome di tabella.  
  
```sql  
SELECT i.object_id,   
    object_name(i.object_id) AS TableName,   
    i.name AS IndexName,   
    i.index_id,   
    i.type_desc,   
    CSRowGroups.*,  
    100*(ISNULL(deleted_rows,0))/total_rows AS 'Fragmentation'  
FROM sys.indexes AS i  
JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id AND i.index_id = CSRowGroups.index_id   
-- WHERE object_name(i.object_id) = 'table_name'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [L'esecuzione di query di catalogo di sistema SQL Server domande frequenti](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Sys.ALL_COLUMNS &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [Sys. computed_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guida agli indici columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [Sys. column_store_dictionaries &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
