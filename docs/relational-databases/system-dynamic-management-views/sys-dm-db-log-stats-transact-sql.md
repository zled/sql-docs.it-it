---
title: sys.dm_db_log_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_log_stats_TSQL
- sys.dm_db_log_stats
- sys.dm_db_log_stats_TSQL
- dm_db_log_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_stats dynamic management function
ms.assetid: ''
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 3c8498cf841152d942ed44a21ba4b525af011180
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmdblogstats-transact-sql"></a>sys.dm_db_log_stats (Transact-SQL)   
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Restituisce attributi a livello di riepilogo e le informazioni sul file di log delle transazioni di database. Utilizzare queste informazioni per il monitoraggio e diagnostica di integrità di log delle transazioni.   
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
 sys.dm_db_log_stats ( database_id )
```  
  
## <a name="arguments"></a>Argomenti  

*database_id* | NULL | **Predefinito**

ID del database. `database_id` è `int`. Gli input validi sono il numero di ID di un database, `NULL`, o `DEFAULT`. Il valore predefinito è `NULL`. `NULL` e `DEFAULT` sono valori equivalenti nel contesto del database corrente.  
La funzione predefinita [DB_ID](../../t-sql/functions/db-id-transact-sql.md) può essere specificato. Quando si utilizza `DB_ID` senza specificare un nome di database, il livello di compatibilità del database corrente deve essere maggiore o uguale a 90.

  
## <a name="tables-returned"></a>Tabelle restituite  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id    |**int**    |ID database |  
|recovery_model |**nvarchar(60)**   |   Modello di recupero del database. I valori possibili includono: <br /> SIMPLE<br /> BULK_LOGGED <br /> FULL |  
|log_min_lsn    |**nvarchar(24)**   |   Inizio corrente [sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) nel log delle transazioni.|  
|log_end_lsn    |**nvarchar(24)**   |   [sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) dell'ultimo record di log nel log delle transazioni.|  
|current_vlf_sequence_number    |**bigint** |   Corrente [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) numero di sequenza durante la fase di esecuzione.|  
|current_vlf_size_mb    |**float**  |   Corrente [file di log virtuale (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) dimensione in MB.|   
|total_vlf_count    |**bigint** |   Numero totale di [il file di log virtuali (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) nel log delle transazioni. |  
|total_log_size_mb  |**float**  |   Dimensioni del log delle transazioni totale in MB. |  
|active_vlf_count   |**bigint** |   Numero totale di attivo [il file di log virtuali (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) nel log delle transazioni.|  
|active_log_size_mb |**float**  |   Dimensioni del log delle transazioni attivo totale in MB.|  
|log_truncation_holdup_reason   |**nvarchar(60)**   |   Motivo di arresto il troncamento del log. Il valore è uguale a `log_reuse_wait_desc` colonna di `sys.databases`.  (Per ulteriori spiegazioni di questi valori, vedere [Log delle transazioni](../../relational-databases/logs/the-transaction-log-sql-server.md)). <br />I valori possibili includono: <br />NOTHING<br />CHECKPOINT<br />LOG_BACKUP<br />ACTIVE_BACKUP_OR_RESTORE<br />ACTIVE_TRANSACTION<br />DATABASE_MIRRORING<br />REPLICATION<br />DATABASE_SNAPSHOT_CREATION<br />LOG_SCAN<br />AVAILABILITY_REPLICA<br />OLDEST_PAGE<br />XTP_CHECKPOINT<br />ALTRO TEMPORANEO |  
|log_backup_time    |**datetime**   |   Transaction log backup ora dell'ultima.|   
|log_backup_lsn |**nvarchar(24)**   |   Ultimo backup del log delle transazioni [sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|   
|log_since_last_log_backup_mb   |**float**  |   Dimensioni log in MB dall'ultimo backup del log delle transazioni [sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_checkpoint_lsn |**nvarchar(24)**   |   Ultimo checkpoint [sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_since_last_checkpoint_mb   |**float**  |   Dimensioni log in MB dall'ultimo checkpoint [sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_recovery_lsn   |**nvarchar(24)**   |   Ripristino [sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) del database. Se `log_recovery_lsn` si verifica prima del LSN, checkpoint `log_recovery_lsn` è la transazione attiva meno recente LSN, in caso contrario `log_recovery_lsn` è del LSN checkpoint.|  
|log_recovery_size_mb   |**float**  |   Dimensioni log in MB dopo il recupero di log [sequenza numero di log (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|recovery_vlf_count |**bigint** |   Numero totale di [il file di log virtuali (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) da recuperare, se si è verificato il riavvio del server o del failover. |  


## <a name="permissions"></a>Autorizzazioni  
Richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
  
## <a name="examples"></a>Esempi  

### <a name="a-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-high-number-of-vlfs"></a>A. Determinare i database in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza con un numero elevato di VLF   
La query seguente restituisce i database con più di 100 VLF nei file di log. Un numero elevato di VLF può influenzare l'ora di avvio, ripristino e ripristino di database.

```sql  
SELECT name AS 'Database Name', total_vlf_count AS 'VLF count' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id) 
WHERE total_vlf_count  > 100;
```   

### <a name="b-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-transaction-log-backups-older-than-4-hours"></a>B. Determinare i database in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza con un backup del log delle transazioni meno di 4 ore   
La query seguente determina le ultime volte in backup log per i database nell'istanza.

```sql  
SELECT name AS 'Database Name', log_backup_time AS 'last log backup time' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id); 
```

## <a name="see-also"></a>Vedere anche  
[Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_info & #40; Transact-SQL & #41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)    
  
