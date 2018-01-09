---
title: Sys.dm_db_log_info (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_log_info
- sys.dm_db_log_info_TSQL
- dm_db_log_info
- dm_db_log_info_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_info dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: "4"
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: 661647715d2fcff3a4821250dfaa65e0fea07d6e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="sysdmdbloginfo-transact-sql"></a>Sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Restituisce [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) informazioni del log delle transazioni. Nota di che tutti i file di log delle transazioni vengono combinati nell'output della tabella. Ogni riga nell'output rappresenta un VLF nel log delle transazioni e fornisce informazioni rilevanti per tale VLF nel log.

## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_db_log_info ( database_id )  
```  
## <a name="arguments"></a>Argomenti  
 *database_id* | NULL | IMPOSTAZIONE PREDEFINITA  
 ID del database. *database_id* è **int**. Gli input validi sono il numero di ID di un database, NULL o DEFAULT. Il valore predefinito è NULL. NULL e DEFAULT sono valori equivalenti nel contesto del database corrente.
 
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

### <a name="b-determing-the-status-of-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>B. Determinare lo stato dell'ultimo `VLF` nel log delle transazioni prima di compattazione del file di log

La query seguente consente di determinare lo stato dell'ultimo VLF prima di eseguire shrinkfile nel log delle transazioni per determinare se è possibile ridurre il log delle transazioni.

```sql
USE AdventureWorks2016
GO

SELECT TOP 1 DB_NAME(database_id) AS "Database Name", file_id, vlf_size_mb, vlf_sequence_number, vlf_active, vlf_status
FROM sys.dm_db_log_info(DEFAULT)
ORDER BY vlf_sequence_number DESC
```


## <a name="see-also"></a>Vedere anche  
[Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Viste a gestione dinamica &#40; correlati al database Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[Sys.dm_db_log_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)

