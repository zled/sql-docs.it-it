---
title: sys.dm_exec_query_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/04/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_stats_TSQL
- dm_exec_query_stats
- sys.dm_exec_query_stats
- sys.dm_exec_query_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_stats dynamic management view
ms.assetid: eb7b58b8-3508-4114-97c2-d877bcb12964
caps.latest.revision: 64
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 91d7d373b0bbc3b96174fabf481a7a6c3b859b86
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecquerystats-transact-sql"></a>sys.dm_exec_query_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce le statistiche di prestazioni aggregati per i piani di query memorizzati nella cache in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La vista contiene una riga per ogni istruzione di query nel piano memorizzato nella cache e la durata delle righe è legata al piano stesso. Quando un piano viene rimosso dalla cache, le righe corrispondenti vengono eliminate da questa vista.  
  
> [!NOTE]
> Una query iniziale di **Sys.dm exec_query_stats** potrebbe produrre risultati non accurati se è presente un carico di lavoro attualmente in esecuzione nel server. La riesecuzione della query può garantire risultati più accurati.  
  
> [!NOTE]
> Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_exec_query_stats**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**sql_handle**|**varbinary(64)**  |Token che fa riferimento al batch o alla stored procedure di cui fa parte la query.<br /><br /> **valore di sql_handle**, insieme a **statement_start_offset** e **statement_end_offset**, può essere utilizzato per recuperare il testo SQL della query chiamando la **sys.dm_exec_sql_ testo** funzione a gestione dinamica.|  
|**statement_start_offset**|**int**|Indica, in byte e a partire da 0, la posizione iniziale della query descritta dalla riga all'interno del testo del batch o dell'oggetto persistente.|  
|**statement_end_offset**|**int**|Indica, in byte e a partire da 0, la posizione finale della query descritta dalla riga all'interno del testo del batch o dell'oggetto persistente. Per le versioni precedenti [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], il valore-1 indica la fine del batch. I commenti finali non sono più inclusi.|  
|**plan_generation_num**|**bigint**|Numero di sequenza utilizzabile per distinguere le istanze dei piani dopo una ricompilazione.|  
|**plan_handle**|**varbinary(64)**|Token che fa riferimento al piano compilato di cui fa parte la query. Questo valore può essere passato per il [Sys.dm exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md) funzione a gestione dinamica per ottenere il piano di query.<br /><br /> È sempre 0x000 quando una stored procedure compilata in modo nativo esegue una query su una tabella ottimizzata per la memoria.|  
|**creation_time**|**datetime**|Ora di compilazione del piano.|  
|**last_execution_time**|**datetime**|Ora dell'ultimo avvio dell'esecuzione del piano.|  
|**execution_count**|**bigint**|Numero di esecuzioni del piano a partire dall'ultima compilazione.|  
|**total_worker_time**|**bigint**|Quantità totale di tempo di CPU, espresso in microsecondi (con precisione al millisecondo), impiegato per le esecuzioni del piano a partire dalla relativa compilazione.<br /><br /> Per le stored procedure compilate in modo nativo, il valore di **total_worker_time** non può essere accurato se più esecuzioni richiedono meno di 1 millisecondo.|  
|**last_worker_time**|**bigint**|Tempo di CPU, espresso in microsecondi (con precisione al millisecondo), impiegato per l'ultima esecuzione del piano. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Tempo minimo di CPU, espresso in microsecondi (con precisione al millisecondo), mai impiegato dal piano durante una singola esecuzione. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Tempo massimo di CPU, espresso in microsecondi (con precisione al millisecondo), mai impiegato dal piano durante una singola esecuzione. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Numero totale di letture fisiche effettuate dalle esecuzioni del piano a partire dalla relativa compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_physical_reads**|**bigint**|Numero di letture fisiche eseguite durante l'ultima esecuzione del piano.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_physical_reads**|**bigint**|Numero minimo di letture fisiche effettuate dal piano durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_physical_reads**|**bigint**|Numero massimo di letture fisiche effettuate dal piano durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_logical_writes**|**bigint**|Numero totale di scritture logiche effettuate dalle esecuzioni del piano a partire dalla relativa compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_logical_writes**|**bigint**|Numero del numero di pagine del pool di buffer diventate dirty durante l'ultima esecuzione del piano. Se una pagina è già dirty (modificata) le scritture non vengono conteggiate.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_logical_writes**|**bigint**|Numero minimo di scritture logiche effettuate dal piano durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_logical_writes**|**bigint**|Numero massimo di scritture logiche effettuate dal piano durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_logical_reads**|**bigint**|Numero totale di letture logiche effettuate dalle esecuzioni del piano a partire dalla sua compilazione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**last_logical_reads**|**bigint**|Numero di letture logiche effettuate durante l'ultima esecuzione del piano.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**min_logical_reads**|**bigint**|Numero minimo di letture logiche effettuate dal piano durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**max_logical_reads**|**bigint**|Numero massimo di letture logiche effettuate dal piano durante una singola esecuzione.<br /><br /> È sempre 0 con esecuzione di query su una tabella ottimizzata per la memoria.|  
|**total_clr_time**|**bigint**|Tempo, espresso in microsecondi (con precisione al millisecondo), utilizzate in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] oggetti di common language runtime (CLR) dalle esecuzioni del piano dopo l'ultima compilazione. Gli oggetti CLR possono essere stored procedure, funzioni, trigger, tipi e aggregazioni.|  
|**last_clr_time**|**bigint**|Tempo, espresso in microsecondi (con precisione al millisecondo) utilizzati dall'esecuzione all'interno [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] oggetti CLR durante l'ultima esecuzione del piano. Gli oggetti CLR possono essere stored procedure, funzioni, trigger, tipi e aggregazioni.|  
|**min_clr_time**|**bigint**|Tempo minimo di CPU, espresso in microsecondi (con precisione al millisecondo), mai impiegato dal piano durante una singola esecuzione all'interno di oggetti CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Gli oggetti CLR possono essere stored procedure, funzioni, trigger, tipi e aggregazioni.|  
|**max_clr_time**|**bigint**|Tempo massimo di CPU, espresso in microsecondi (con precisione al millisecondo), mai impiegato dal piano durante una singola esecuzione all'interno di oggetti CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Gli oggetti CLR possono essere stored procedure, funzioni, trigger, tipi e aggregazioni.|  
|**total_elapsed_time**|**bigint**|Tempo totale trascorso, espresso in microsecondi (con precisione al millisecondo), per le esecuzioni completate di questo piano.|  
|**last_elapsed_time**|**bigint**|Tempo trascorso, espresso in microsecondi (con precisione al millisecondo), per le ultime esecuzioni completate di questo piano.|  
|**min_elapsed_time**|**bigint**|Tempo minimo trascorso, espresso in microsecondi (con precisione al millisecondo), per un'esecuzione completata di questo piano.|  
|**max_elapsed_time**|**bigint**|Tempo massimo trascorso, espresso in microsecondi (con precisione al millisecondo), per un'esecuzione completata di questo piano.|  
|**query_hash**|**Binari (8)**|Valore hash binario calcolato sulla query che consente di identificare query con logica analoga. È possibile utilizzare il valore hash della query per determinare l'utilizzo delle risorse aggregate per query che differiscono solo per valori letterali.|  
|**query_plan_hash**|**binary(8)**|Valore hash binario calcolato sul piano di esecuzione di query che consente di identificare piani di esecuzioni analoghi. È possibile utilizzare il valore hash del piano di query per individuare il costo cumulativo di query con piani di esecuzione analoghi.<br /><br /> È sempre 0x000 quando una stored procedure compilata in modo nativo esegue una query su una tabella ottimizzata per la memoria.|  
|**total_rows**|**bigint**|Numero totale di righe restituite dalla query. Non può essere null.<br /><br /> È sempre 0 quando una stored procedure compilata in modo nativo esegue una query su una tabella ottimizzata per la memoria.|  
|**last_rows**|**bigint**|Numero di righe restituite durante l'ultima esecuzione della query. Non può essere null.<br /><br /> È sempre 0 quando una stored procedure compilata in modo nativo esegue una query su una tabella ottimizzata per la memoria.|  
|**min_rows**|**bigint**|Numero minimo di righe restituito dalla query durante l'esecuzione di uno. Non può essere null.<br /><br /> È sempre 0 quando una stored procedure compilata in modo nativo esegue una query su una tabella ottimizzata per la memoria.|  
|**max_rows**|**bigint**|Numero massimo di righe restituito dalla query durante l'esecuzione di uno. Non può essere null.<br /><br /> È sempre 0 quando una stored procedure compilata in modo nativo esegue una query su una tabella ottimizzata per la memoria.|  
|**statement_sql_handle**|**varbinary(64)**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Popolato con i valori non NULL solo se l'archivio Query è attivato e raccogliere le statistiche per tale query particolare.|  
|**statement_context_id**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Popolato con i valori non NULL solo se l'archivio Query è attivato e raccogliere le statistiche per tale query particolare.|  
|**total_dop**|**bigint**|La somma totale dei gradi di parallelismo questo piano utilizzato dopo l'ultima compilazione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_dop**|**bigint**|Il grado di parallelismo quando il piano di ultima esecuzione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_dop**|**bigint**|Il grado di parallelismo minimo piano utilizzato durante l'esecuzione di uno. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_dop**|**bigint**|Il massimo grado di parallelismo piano utilizzato durante l'esecuzione di uno. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_grant_kb**|**bigint**|La quantità totale di memoria riservata concedere in KB piano ricevuto dopo l'ultima compilazione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_grant_kb**|**bigint**|Quando il piano di ultima esecuzione, la quantità di memoria riservata concedere in KB. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_grant_kb**|**bigint**|La quantità minima di memoria riservata concedere in KB mai ricevuto durante l'esecuzione di un piano. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_grant_kb**|**bigint**|La quantità massima di memoria riservata concedere in KB mai ricevuto durante l'esecuzione di un piano. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_used_grant_kb**|**bigint**|La quantità totale di memoria riservata concedere in KB questo piano utilizzato dopo l'ultima compilazione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_used_grant_kb**|**bigint**|La quantità di memoria utilizzata concessione, espressa in KB, quando il piano di ultima esecuzione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_used_grant_kb**|**bigint**|La quantità minima di memoria utilizzata concedere in KB mai utilizzato durante l'esecuzione di un piano. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_used_grant_kb**|**bigint**|La quantità massima di memoria utilizzata concedere in KB mai utilizzato durante l'esecuzione di un piano. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_ideal_grant_kb**|**bigint**|La quantità totale di concessione di memoria ideale in KB, il piano stimato dopo l'ultima compilazione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_ideal_grant_kb**|**bigint**|Quando il piano di ultima esecuzione, la quantità di memoria ideale concedere in KB. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_ideal_grant_kb**|**bigint**|Concessione della quantità minima di memoria ideale in KB, il piano stimato mai durante l'esecuzione di uno. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_ideal_grant_kb**|**bigint**|Concessione della quantità massima di memoria ideale in KB, il piano stimato mai durante l'esecuzione di uno. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_reserved_threads**|**bigint**|La somma totale dei parallelo riservato di thread di questo piano mai utilizzato dopo l'ultima compilazione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_reserved_threads**|**bigint**|Il numero di thread paralleli riservati, quando il piano di ultima esecuzione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_reserved_threads**|**bigint**|Il numero minimo di parallelo riservato thread utilizzato durante l'esecuzione di un piano.  Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_reserved_threads**|**bigint**|Il numero massimo di parallelo riservato thread utilizzato durante l'esecuzione di un piano. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_used_threads**|**bigint**|La somma totale dei utilizzato thread paralleli questo piano mai utilizzato dopo l'ultima compilazione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_used_threads**|**bigint**|Il numero di thread paralleli usato, quando il piano di ultima esecuzione. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_used_threads**|**bigint**|Il numero minimo di utilizzato thread paralleli mai utilizzato durante l'esecuzione di un piano. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_used_threads**|**bigint**|Utilizzato il numero massimo di thread paralleli mai utilizzato durante l'esecuzione di un piano. Sarà sempre 0 per l'esecuzione di query su una tabella con ottimizzazione per la memoria.<br /><br /> **Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_columnstore_segment_reads**|**bigint**|La somma totale dei segmenti columnstore lette dalla query. Non può essere null.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**last_columnstore_segment_reads**|**bigint**|Il numero di segmenti di columnstore lettura dall'ultima esecuzione della query. Non può essere null.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**min_columnstore_segment_reads**|**bigint**|Il numero minimo di segmenti di columnstore mai lette dalla query durante l'esecuzione di uno. Non può essere null.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**max_columnstore_segment_reads**|**bigint**|Il numero massimo di segmenti di columnstore mai lette dalla query durante l'esecuzione di uno. Non può essere null.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**total_columnstore_segment_skips**|**bigint**|La somma totale dei segmenti columnstore ignorato dalla query. Non può essere null.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**last_columnstore_segment_skips**|**bigint**|Il numero di segmenti di columnstore ignorati dall'ultima esecuzione della query. Non può essere null.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**min_columnstore_segment_skips**|**bigint**|Il numero minimo di segmenti di columnstore mai di ignorare la query durante l'esecuzione di uno. Non può essere null.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**max_columnstore_segment_skips**|**bigint**|Il numero massimo di segmenti di columnstore mai di ignorare la query durante l'esecuzione di uno. Non può essere null.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|
|**total_spills**|**bigint**|Il numero totale di pagine distribuite tramite l'esecuzione della query dopo l'ultima compilazione.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|Il numero di pagine distribuite l'ora dell'ultima che esecuzione della query.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|Il numero minimo di pagine che questa query è sempre distribuito durante una singola esecuzione.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|Il numero massimo di pagine che questa query è sempre distribuito durante una singola esecuzione.<br /><br /> **Si applica a**: a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**pdw_node_id**|**int**|L'identificatore per il nodo che utilizza questo tipo di distribuzione.<br /><br /> **Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]| 

> [!NOTE]
> <sup>1</sup> per le stored procedure compilate in modo nativo quando la raccolta delle statistiche è abilitata, tempo del processo viene raccolto in millisecondi. Se la query viene eseguita in meno di un millisecondo, il valore sarà 0.  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   
   
## <a name="remarks"></a>Osservazioni  
 Le statistiche nella vista vengono aggiornate quando viene completata una query.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-finding-the-top-n-queries"></a>A. Ricerca delle prime n query  
 Nell'esempio seguente vengono restituite informazioni sulle prime cinque query classificate in base al tempo medio della CPU. Nell'esempio le query vengono aggregate in base al relativo valore hash del piano, in modo da raggruppare le query logicamente equivalenti in base all'utilizzo di risorse cumulativo.  
  
```sql  
SELECT TOP 5 query_stats.query_hash AS "Query Hash",   
    SUM(query_stats.total_worker_time) / SUM(query_stats.execution_count) AS "Avg CPU Time",  
    MIN(query_stats.statement_text) AS "Statement Text"  
FROM   
    (SELECT QS.*,   
    SUBSTRING(ST.text, (QS.statement_start_offset/2) + 1,  
    ((CASE statement_end_offset   
        WHEN -1 THEN DATALENGTH(ST.text)  
        ELSE QS.statement_end_offset END   
            - QS.statement_start_offset)/2) + 1) AS statement_text  
     FROM sys.dm_exec_query_stats AS QS  
     CROSS APPLY sys.dm_exec_sql_text(QS.sql_handle) as ST) as query_stats  
GROUP BY query_stats.query_hash  
ORDER BY 2 DESC;  
```  
  
### <a name="b-returning-row-count-aggregates-for-a-query"></a>B. Restituzione di aggregazioni relative al conteggio delle righe per una query  
 Nell'esempio seguente vengono restituite le informazioni di aggregazione relative al conteggio delle righe (totale righe, numero minimo righe, numero massimo righe e ultime righe) per le query.  
  
```sql  
SELECT qs.execution_count,  
    SUBSTRING(qt.text,qs.statement_start_offset/2 +1,   
                 (CASE WHEN qs.statement_end_offset = -1   
                       THEN LEN(CONVERT(nvarchar(max), qt.text)) * 2   
                       ELSE qs.statement_end_offset end -  
                            qs.statement_start_offset  
                 )/2  
             ) AS query_text,   
     qt.dbid, dbname= DB_NAME (qt.dbid), qt.objectid,   
     qs.total_rows, qs.last_rows, qs.min_rows, qs.max_rows  
FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS qt   
WHERE qt.text like '%SELECT%'   
ORDER BY qs.execution_count DESC;  
```  
  
## <a name="see-also"></a>Vedere anche  
[Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)    
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)    
[sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)     
[sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)     
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  


