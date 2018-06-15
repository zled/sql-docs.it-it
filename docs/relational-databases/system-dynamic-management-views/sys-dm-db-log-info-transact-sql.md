---
title: sys.dm_db_log_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_db_log_info
- sys.dm_db_log_info_TSQL
- dm_db_log_info
- dm_db_log_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_info dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: 4
author: savjani
ms.author: pariks
manager: ajayj
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e2b99ce1a417c31b4ca81eb9f538acda0edfc517
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34464657"
---
# <a name="sysdmdbloginfo-transact-sql"></a>sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Restituisce [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) informazioni del log delle transazioni. Nota di che tutti i file di log delle transazioni vengono combinati nell'output della tabella. Ogni riga nell'output rappresenta un VLF nel log delle transazioni e fornisce informazioni rilevanti per tale VLF nel log.

## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_db_log_info ( database_id )  
``` 

## <a name="arguments"></a>Argomenti  
 *database_id* | NULL | VALORE PREDEFINITO  
 ID del database. *database_id* è di tipo **int**. Gli input validi sono il numero di ID di un database, NULL o DEFAULT. Il valore predefinito è NULL. NULL e DEFAULT sono valori equivalenti nel contesto del database corrente.
 
 Specificare NULL per restituire informazioni VLF del database corrente.

 La funzione predefinita [DB_ID](../../t-sql/functions/db-id-transact-sql.md) può essere specificato. Quando si utilizza `DB_ID` senza specificare un nome di database, il livello di compatibilità del database corrente deve essere maggiore o uguale a 90.  

## <a name="table-returned"></a>Tabella restituita  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database.|
|file_id|**smallint**|Id di file del log delle transazioni.|  
|vlf_begin_offset|**bigint** |Posizione di offset il [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) dall'inizio del file di log delle transazioni.|
|vlf_size_mb |**float** |[file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) dimensione in MB, arrotondato a 2 cifre decimali.|     
|vlf_sequence_number|**bigint** |[file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) progressivo nell'ordine creato. Utilizzato per identificare in modo univoco i VLF nel file di log.|
|vlf_active|**bit** |Indica se [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) è in uso o non. <br />0 - VLF non è in uso.<br />1 - VLF è attiva.|
|vlf_status|**int** |Stato di [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). I valori possibili includono <br />0 - VLF è inattivo <br />1 - VLF è inizializzata ma non utilizzati <br /> 2 - VLF è attiva.|
|vlf_parity|**tinyint** |Parità di [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Utilizzata internamente per determinare l'entità finale del log all'interno di un VLF.|
|vlf_first_lsn|**nvarchar(48)** |[Sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) del primo record del log nel [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|
|vlf_create_lsn|**nvarchar(48)** |[Sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) del Registro di record che ha creato il [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|

## <a name="remarks"></a>Osservazioni
Il `sys.dm_db_log_info` funzione a gestione dinamica sostituisce il `DBCC LOGINFO` istruzione.    
 
## <a name="permissions"></a>Autorizzazioni  
Richiede il `VIEW DATABASE STATE` autorizzazione per il database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Metodo database in un'istanza di SQL Server con un numero elevato di VLF
La query seguente determina i database con più di 100 VLF nei file di log, che possono influenzare l'ora di avvio, ripristino e ripristino di database.

```sql
SELECT [name], COUNT(l.database_id) AS 'vlf_count' 
FROM sys.databases s
CROSS APPLY sys.dm_db_log_info(s.database_id) l
GROUP BY [name]
HAVING COUNT(l.database_id) > 100
```

### <a name="b-determing-the-position-of-the-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>B. Determinare la posizione dell'ultimo `VLF` nel log delle transazioni prima di compattazione del file di log

La query seguente consente di determinare la posizione dell'ultimo VLF attivo prima di eseguire shrinkfile nel log delle transazioni per determinare se è possibile ridurre il log delle transazioni.

```sql
USE AdventureWorks2016
GO

;WITH cte_vlf AS (
SELECT ROW_NUMBER() OVER(ORDER BY vlf_begin_offset) AS vlfid, DB_NAME(database_id) AS [Database Name], vlf_sequence_number, vlf_active, vlf_begin_offset, vlf_size_mb
    FROM sys.dm_db_log_info(DEFAULT)),
cte_vlf_cnt AS (SELECT [Database Name], COUNT(vlf_sequence_number) AS vlf_count,
    (SELECT COUNT(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 0) AS vlf_count_inactive,
    (SELECT COUNT(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS vlf_count_active,
    (SELECT MIN(vlfid) FROM cte_vlf WHERE vlf_active = 1) AS ordinal_min_vlf_active,
    (SELECT MIN(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS min_vlf_active,
    (SELECT MAX(vlfid) FROM cte_vlf WHERE vlf_active = 1) AS ordinal_max_vlf_active,
    (SELECT MAX(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS max_vlf_active
    FROM cte_vlf
    GROUP BY [Database Name])
SELECT [Database Name], vlf_count, min_vlf_active, ordinal_min_vlf_active, max_vlf_active, ordinal_max_vlf_active,
((ordinal_min_vlf_active-1)*100.00/vlf_count) AS free_log_pct_before_active_log,
((ordinal_max_vlf_active-(ordinal_min_vlf_active-1))*100.00/vlf_count) AS active_log_pct,
((vlf_count-ordinal_max_vlf_active)*100.00/vlf_count) AS free_log_pct_after_active_log
FROM cte_vlf_cnt
GO
```

## <a name="see-also"></a>Vedere anche  
[Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)

