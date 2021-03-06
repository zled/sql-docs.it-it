---
title: sys.database_query_store_options (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0d9d04832b09d357725dc7a4986d4ed074469559
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775129"
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>sys.database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Restituisce le opzioni di Query Store per questo database.  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|Indica la modalità operativa desiderata di Query Store, impostare in modo esplicito dall'utente.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(60)**|Descrizione testuale della modalità operativa desiderata di Query Store:<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|Indica la modalità operativa di Query Store. Oltre all'elenco degli stati desiderati necessarie per l'utente, lo stato effettivo può essere uno stato di errore.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = ERRORE|  
|**actual_state_desc**|**nvarchar(60)**|Descrizione testuale della modalità di operazione effettiva di Query Store.<br />OFF<br />READ_ONLY<br />READ_WRITE<br />error<br /><br /> Esistono situazioni quando lo stato effettivo è diverso dallo stato desiderato:<br /><br /> Query Store potrebbe funzionare in modalità di sola lettura, anche se in lettura / scrittura è stata specificata dall'utente. Questa situazione potrebbe verificarsi, ad esempio, se il database è in modalità sola lettura o se le dimensioni di Query Store superano la quota.<br /><br /> È estremamente raro che Query Store possono finire in stato di errore a causa di errori interni. In questo caso, Query Store è stato possibile ripristinare tramite l'esecuzione **sp_query_store_consistency_check** stored procedure nel database interessato.|  
|**readonly_reason**|**int**|Quando la **desired_state_desc** è READ_WRITE e il **actual_state_desc** viene impostato come READ_ONLY, **readonly_reason** restituisce mappare un po' per indicare il motivo per cui la Query Store è in modalità di sola lettura.<br /><br /> 1 – database è in modalità di sola lettura<br /><br /> 2 – database si trova in modalità utente singolo<br /><br /> 4-database si trova in modalità di emergenza<br /><br /> 8 – database è una replica secondaria (si applica a Always On e Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)] replica geografica). Questo valore può essere osservato in modo efficace solo nei **leggibile** repliche secondarie<br /><br /> 65536: Store la Query ha raggiunto il limite di dimensione impostato dall'opzione MAX_STORAGE_SIZE_MB.<br /><br /> 131072 - il numero di istruzioni diverse in Query Store ha raggiunto il limite di memoria interna. Provare a rimuovere le query che non è necessario o l'aggiornamento a un livello di servizio superiore per consentire il trasferimento di Query Store in modalità lettura / scrittura.<br />Si applica solo a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> 262144 – le dimensioni degli elementi in memoria in attesa di essere resi persistenti su disco ha raggiunto il limite di memoria interna. Query Store sarà in modalità di sola lettura temporaneamente fino a quando gli elementi in memoria sono persistenti sul disco. <br />Si applica solo a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br />524288 – database ha raggiunto il limite di dimensioni del disco. Query Store è parte del database utente, pertanto se è presente spazio non è più disponibile per un database, il che significa che Query Store non è possibile aumenti ulteriormente più.<br />Si applica solo a [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. <br /> <br /> Per passare le operazioni di Query Store back in modalità lettura / scrittura, vedere **verificare che Query Store è la raccolta di Query dei dati in modo continuativo** sezione [procedure consigliate per la Query Store](../../relational-databases/performance/best-practice-with-the-query-store.md).|  
|**current_storage_size_mb**|**bigint**|Dimensioni di Query Store su disco in megabyte.|  
|**flush_interval_seconds**|**bigint**|Definisce periodo per regolare lo scaricamento dei dati di Query Store al disco. Valore predefinito è 900 (15 min).<br /><br /> Modifica tramite la `ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)` istruzione.|  
|**interval_length_minutes**|**bigint**|Intervallo di aggregazione delle statistiche. Non sono consentiti valori arbitrari. Usare uno dei seguenti: 1, 5, 10, 15, 30, 60 e 1440 minuti. Il valore predefinito è 60 minuti.|  
|**max_storage_size_mb**|**bigint**|Dimensione massima del disco per la Query Store. Valore predefinito è 100 MB.<br />Per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition il valore predefinito è 1Gb, mentre per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition il valore predefinito è 10Mb.<br /><br /> Modifica tramite la `ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)` istruzione.|  
|**stale_query_threshold_days**|**bigint**|Numero di giorni che esegue una query con le impostazioni di criteri non viene mantenuto in Query Store. Valore predefinito è 30. Impostare su 0 per disabilitare i criteri di conservazione.<br />Per l'edizione [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic, l'impostazione predefinita è 7 giorni.<br /><br /> Modifica tramite la `ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )` istruzione.|  
|**max_plans_per_query**|**bigint**|Limita il numero massimo di piani stored. Valore predefinito è 200. Se il valore massimo viene raggiunto, Query Store interrompe l'acquisizione di nuovi piani per tale query. Impostazione su 0 consente di rimuovere le limitazioni per quanto riguarda il numero di piani acquisiti.<br /><br /> Modifica tramite la `ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)` istruzione.|  
|**query_capture_mode**|**smallint**|La modalità di acquisizione query attualmente attiva:<br /><br /> 1 = ALL - vengono acquisite tutte le query. Questo è il valore di configurazione predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> 2 = AUTO - acquisite le query pertinenti in base l'esecuzione numero e consumo delle risorse. Questo è il valore di configurazione predefinito per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].<br /><br /> 3 = Nessuna: arrestare l'acquisizione di nuove query. Query Store continuerà a raccogliere le statistiche di compilazione e runtime per le query che sono già state acquisite. Usare questa configurazione con cautela in quanto si potrebbero perdere per query importanti.|  
|**query_capture_mode_desc**|**nvarchar(60)**|Descrizione testuale della modalità di acquisizione effettivi di Query Store:<br /><br /> TUTTE (impostazione predefinita per [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> AUTO (impostazione predefinita per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> Nessuno|  
|**size_based_cleanup_mode**|**smallint**|Determina se la pulizia viene attivata automaticamente quando la quantità totale dei dati ha quasi raggiunto le dimensioni massime:<br /><br /> 0 = OFF, le dimensioni di pulizia basata sulle non verranno attivata automaticamente.<br /><br /> 1 = AUTO - pulizia basata sulle sarà attivata automaticamente quando le dimensioni su disco raggiunge il 90% delle dimensioni **max_storage_size_mb**. Si tratta del valore di configurazione predefinito.<br /><br />La pulizia basata sulle dimensioni rimuove per prime le query meno recenti e meno dispendiose. Si ferma in corrispondenza di circa l'80% di max_storage_size_mb.|  
|**size_based_cleanup_mode_desc**|**nvarchar(60)**|Descrizione testuale della modalità di pulizia basato sulle dimensioni effettive di Query Store:<br /><br /> OFF <br /><br /> AUTO (impostazione predefinita)|  
|**wait_stats_capture_mode**|**smallint**|Controlla se Query Store esegue l'acquisizione delle statistiche di attesa: <br /><br /> 0 = OFF <br /><br /> 1 = ON<br /> **Si applica a**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|**wait_stats_mode_capture_desc**|**nvarchar(60)**|Descrizione testuale della modalità di acquisizione delle statistiche di attesa effettivo: <br /><br /> OFF <br /><br /> (Impostazione predefinita)<br /> **Si applica a**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
  
## <a name="permissions"></a>Permissions  
 Richiede la **VIEW DATABASE STATE** l'autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [Query Store Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
