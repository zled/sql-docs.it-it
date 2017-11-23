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
ms.openlocfilehash: b7250943f4e92d60888a75d9e577388f3cc6b1ed
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbloginfo-transact-sql"></a>Sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Restituisce `VLF` informazioni dei file di log delle transazioni. (Tutti i file di log vengono combinati nell'output della tabella). Nell'output di ogni riga rappresenta un `VLF` nel log delle transazioni e vengono fornite informazioni rilevanti per tale VLF nel log.

## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_db_log_info ( database_id )  
```  
## <a name="arguments"></a>Argomenti  
 *database_id* | NULL | IMPOSTAZIONE PREDEFINITA  
 ID del database. *database_id* è **int**. Gli input validi sono il numero di ID di un database, NULL o DEFAULT. Il valore predefinito è NULL. NULL e DEFAULT sono valori equivalenti nel contesto del database corrente.
 
 Specificare NULL per restituire `VLF` informazioni del database corrente.

 La funzione predefinita [DB_ID](../../t-sql/functions/db-id-transact-sql.md) può essere specificato. Quando si utilizza DB_ID senza specificare un nome di database, il livello di compatibilità del database corrente deve essere 90 o un valore superiore.  

## <a name="table-returned"></a>Tabella restituita  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database.|
|file_id|**smallint**|Id di file del log delle transazioni.|  
|vlf_begin_offset|**bigint** |Posizione di offset il `VLF` dall'inizio del file di log delle transazioni.|
|vlf_size_mb |**float** |`VLF`dimensioni in MB, arrotondato a 2 cifre decimali.|     
|vlf_sequence_number|**bigint** |`VLF`numero di sequenza nell'ordine creato. Utilizzato per identificare univocamente `VLFs` nel file di log.|
|vlf_active|**bit** |Indica se VLF è in uso o meno. <br />0 - vlf non è in uso.<br />1 - `VLF` è attiva.|
|vlf_status|**int** |Stato di `VLF`. I valori possibili includono <br />0 - `VLF` è inattivo <br />1 - vlf è inizializzata ma non utilizzati <br /> 2 - `VLF` è attiva.|
|vlf_parity|**tinyint** |Parità di `VLF`. Utilizzata internamente per determinare l'entità finale del log all'interno di un `VLF`.|
|vlf_first_lsn|**nvarchar(48)** |LSN del primo record del log nel `VLF`.|
|vlf_create_lsn|**nvarchar(48)** |LSN del log di record che ha creato il `VLF`.|

## <a name="remarks"></a>Osservazioni
 Il `sys.dm_db_log_info` funzione a gestione dinamica sostituisce il `DBCC LOGINFO` istruzione. 
 
## <a name="permissions"></a>Permissions  
 Richiede il `VIEW DATABASE STATE` autorizzazione per il database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Metodo database in un'istanza di SQL Server con un numero elevato di`VLFs`
La query seguente determina i database con più di 100 `VLFs` nei file di log, che possono influire sull'ora di avvio, ripristino e ripristino di database.

```sql
SELECT name,count(l.database_id) as 'vlf_count' from sys.databases s
cross apply sys.dm_db_log_info(s.database_id) l
group by name
having count(l.database_id)> 100
```

### <a name="b-determing-the-status-of-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>B. Determinare lo stato dell'ultimo `VLF` nel log delle transazioni prima di compattazione del file di log

La query seguente può essere utilizzata per determinare lo stato dell'ultimo `VLF` prima di eseguire shrinkfile nel log delle transazioni per determinare se è possibile compattare il log delle transazioni.

```sql
USE <database name>
GO

SELECT top 1 DB_NAME(database_id) as "Database Name",file_id,vlf_size_mb,vlf_sequence_number, vlf_active, vlf_status
from sys.dm_db_log_info(DEFAULT)
order by vlf_sequence_number desc
```


## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica &#40; correlati al database Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_log_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)    
  



