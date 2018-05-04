---
title: sys.pdw_nodes_column_store_row_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 17a4c925-d4b5-46ee-9cd6-044f714e6f0e
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f4c40def23a19ca7d2817acdc6abb66680663770
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwnodescolumnstorerowgroups-transact-sql"></a>sys.pdw_nodes_column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Fornisce informazioni sull'indice columnstore cluster in base al segmento per facilitare l'amministratore di system management in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. **Sys.pdw_nodes_column_store_row_groups** dispone di una colonna per il numero totale di righe archiviate fisicamente (incluse quelle contrassegnate come eliminate) e una colonna per il numero di righe contrassegnate come eliminate. Utilizzare **sys.pdw_nodes_column_store_row_groups** per determinare quale riga gruppi hanno una percentuale elevata di righe eliminate e deve essere ricompilati.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID della tabella sottostante. Questa è la tabella fisica sul nodo di calcolo, non object_id per la tabella logica nel nodo di controllo. Ad esempio, object_id corrisponde a object_id in sys. Tables.<br /><br /> Per creare un join con Sys. Tables, utilizzare sys.pdw_index_mappings.|  
|**index_id**|**int**|ID dell'indice columnstore cluster in *object_id* tabella.|  
|**partition_number**|**int**|ID di partizione della tabella che contiene il gruppo di righe *row_group_id*. È possibile utilizzare *numero_partizione* per unire questa DMV a Sys. Partitions.|  
|**row_group_id**|**int**|ID del gruppo di righe. Univoco all'interno della partizione.|  
|**dellta_store_hobt_id**|**bigint**|Hobt_id per i gruppi di righe delta o NULL se il tipo del gruppo di righe non è delta. Un gruppo di righe delta è un gruppo di righe di lettura/scrittura che accetta nuovi record. È un gruppo di righe delta di **aprire** stato. Un gruppo di righe delta presenta ancora il formato rowstore e non è stato compresso nel formato columnstore.|  
|**state**|**tinyint**|Numero ID associato a state_description.<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED|  
|**state_desccription**|**nvarchar(60)**|Descrizione dello stato persistente del gruppo di righe:<br /><br /> OPEN: un gruppo di righe di lettura/scrittura che accetta nuovi record. Un gruppo di righe aperto presenta ancora il formato rowstore e non è stato compresso nel formato columnstore.<br /><br /> CLOSED: un gruppo di righe riempito, ma non ancora compresso dal processo tuple-mover.<br /><br /> COMPRESSED: un gruppo di righe riempito e compresso.|  
|**total_rows**|**bigint**|Righe totali archiviate fisicamente nel gruppo di righe. È possibile che alcune siano state eliminate, ma risultano comunque archiviate. Il numero massimo di righe in un gruppo di righe è 1.048.576 (esadecimale FFFFF).|  
|**deleted_rows**|**bigint**|Numero di righe archiviate fisicamente nel gruppo di righe contrassegnate per l'eliminazione.<br /><br /> Sempre 0 per DELTA i gruppi di righe.|  
|**size_in_bytes**|**int**|Dimensioni combinate, in byte, di tutte le pagine di questo gruppo di righe. Questa dimensione non include la dimensione necessaria per archiviare i metadati o i dizionari condivisi.|  
|**pdw_node_id**|**int**|Id univoco di un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nodo.|  
|**distribution_id**|**int**|Id univoco della distribuzione.|
  
## <a name="remarks"></a>Osservazioni  
 Restituisce una riga per ogni gruppo di righe columnstore per ogni tabella che dispone di un indice columnstore cluster o non cluster.  
  
 Utilizzare **sys.pdw_nodes_column_store_row_groups** per determinare il numero di righe incluse nel gruppo di righe e le dimensioni del gruppo di righe.  
  
 Quando il numero delle righe eliminate in un gruppo di righe diventa una percentuale elevata delle righe totali, la tabella diventa meno efficiente. Ricompilare l'indice columnstore per ridurre le dimensioni della tabella, riducendo le operazioni di I/O del disco necessarie per leggere la tabella. Per ricompilare l'indice columnstore, utilizzare il **RICOMPILARE** opzione del **ALTER INDEX** istruzione.  
  
 L'indice columnstore aggiornabile inserisce prima nuovi dati in un **aprire** rowgroup, che è in formato rowstore e talvolta anche detto tabella delta.  Quando un rowgroup aperto è pieno, il relativo stato cambia da **chiuso**. Un gruppo di righe chiuso viene compresso nel formato columnstore per il processo tuple-mover e lo stato cambia in **COMPRESSED**.  Il processo tuple-mover è un processo in background che si riattiva periodicamente per verificare se esistano gruppi di righe chiusi pronti per essere compressi in un gruppo di righe columnstore.  Il processo tuple-mover dealloca i gruppi di righe in cui sono state eliminate tutte le righe. Gruppi di righe deallocati vengono contrassegnati come **RITIRATO**. Per eseguire immediatamente dal motore di tuple, usare il **RIORGANIZZARE** opzione del **ALTER INDEX** istruzione.  
  
 Quando un gruppo di righe columnstore risulta riempito, viene compresso e non accetta più nuove righe. Quando vengono eliminate righe da un gruppo compresso, vengono contrassegnate come eliminate, ma risultano ancora presenti. Gli aggiornamenti a un gruppo compresso vengono implementati come un'eliminazione dal gruppo compresso e come un inserimento in un gruppo aperto.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione **VIEW SERVER STATE**.  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 I join di esempio seguente il **sys.pdw_nodes_column_store_row_groups** tabella ad altre tabelle di sistema per restituire informazioni su tabelle specifiche. La colonna `PercentFull` calcolata è una stima dell'efficienza del gruppo di righe. Per informazioni su un singola tabella, rimuovere i trattini di commento davanti alla clausola WHERE e fornire un nome di tabella.  
  
```  
SELECT IndexMap.object_id,   
  object_name(IndexMap.object_id) AS LogicalTableName,   
  i.name AS LogicalIndexName, IndexMap.index_id, NI.type_desc,   
  IndexMap.physical_name AS PhyIndexNameFromIMap,   
  CSRowGroups.*,  
  100*(ISNULL(deleted_rows,0))/total_rows AS PercentDeletedRows   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.pdw_index_mappings AS IndexMap  
    ON i.object_id = IndexMap.object_id  
    AND i.index_id = IndexMap.index_id  
JOIN sys.pdw_nodes_indexes AS NI  
    ON IndexMap.physical_name = NI.name  
    AND IndexMap.index_id = NI.index_id  
JOIN sys.pdw_nodes_column_store_row_groups AS CSRowGroups  
    ON CSRowGroups.object_id = NI.object_id   
    AND CSRowGroups.pdw_node_id = NI.pdw_node_id  
AND CSRowGroups.index_id = NI.index_id      
--WHERE t.name = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, IndexMap.physical_name, pdw_node_id;  
```  

Le operazioni seguenti [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] esempio conta le righe per partizione per l'istogramma archivia anche come numero di righe si trovano in gruppi di apertura, chiuso o la riga compressa:  

```
SELECT
    s.name AS [Schema Name]
    ,t.name AS [Table Name]
    ,rg.partition_number AS [Partition Number]
    ,SUM(rg.total_rows) AS [Total Rows]
    ,SUM(CASE WHEN rg.State = 1 THEN rg.Total_rows Else 0 END) AS [Rows in OPEN Row Groups]
    ,SUM(CASE WHEN rg.State = 2 THEN rg.Total_Rows ELSE 0 END) AS [Rows in Closed Row Groups]
    ,SUM(CASE WHEN rg.State = 3 THEN rg.Total_Rows ELSE 0 END) AS [Rows in COMPRESSED Row Groups]
FROM sys.pdw_nodes_column_store_row_groups rg
JOIN sys.pdw_nodes_tables pt
ON rg.object_id = pt.object_id AND rg.pdw_node_id = pt.pdw_node_id AND pt.distribution_id = rg.distribution_id
JOIN sys.pdw_table_mappings tm
ON pt.name = tm.physical_name
INNER JOIN sys.tables t
ON tm.object_id = t.object_id
INNER JOIN sys.schemas s
ON t.schema_id = s.schema_id
GROUP BY s.name, t.name, rg.partition_number
ORDER BY 1, 2
```
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [CREARE l'indice COLUMNSTORE &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  
