---
title: Sys. resource_stats (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 05/23/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72b0dc0c526198dc49047f44be0cce47ea7f3455
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce i dati di archiviazione e di utilizzo della CPU per un database SQL di Azure. I dati vengono raccolti e aggregati in intervalli di cinque minuti. Per ciascun database utente, è disponibile una riga per ogni finestra di segnalazione di cinque minuti in cui è presente una modifica nell'utilizzo della risorsa. Sono inclusi l'utilizzo della CPU, la variazione delle dimensioni di archiviazione o la modifica della SKU del database. I database inattivi senza modifiche potrebbero non avere righe per ogni intervallo di cinque minuti. I dati cronologici vengono mantenuti per circa 14 giorni.  
  
 Il **resource_stats** visualizzazione contiene diverse definizioni a seconda della versione del Server di Database di SQL Azure che è associato il database. Prendere in considerazione queste differenze e le eventuali modifiche richieste dall'applicazione durante l'aggiornamento a una nuova versione del server.  
  
 La tabella seguente descrive le colonne disponibili in un server v12:  
  
|Colonne (server v12)|Tipo di dati|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Ora UTC che indica l'inizio dell'intervallo di reporting di 5 minuti.|  
|end_time|**datetime**|Ora UTC che indica la fine dell'intervallo di reporting di 5 minuti.|  
|database_name|**varchar**|Nome del database utente.|  
|sku|**varchar**|Livello di servizio del database. Di seguito sono indicati i valori possibili:<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium|  
|storage_in_megabytes|**float**|Dimensioni massime di archiviazione in megabyte per il periodo di tempo, inclusi i dati del database, gli indici, le stored procedure e i metadati.|  
|avg_cpu_percent|**numeric**|Percentuale dell'utilizzo medio del calcolo del limite del livello del servizio.|  
|avg_data_io_percent|**numeric**|Percentuale dell'utilizzo medio di I/O in base al limite del livello del servizio.|  
|avg_log_write_percent|**numeric**|Percentuale dell'utilizzo medio delle risorse di scrittura del limite del livello del servizio.|  
|max_worker_percent|**decimal(5,2)**|Massimi simultanee processi di lavoro (richieste) come percentuale del limite del livello di servizio del database.<br /><br /> Massimo viene attualmente calcolato per l'intervallo di 5 minuti sulla base dei campioni secondo 15 dei conteggi di lavoro simultanei.|  
|max_session_percent|**decimal(5,2)**|Numero massimo di sessioni simultaneo espresso come percentuale del limite del livello di servizio del database.<br /><br /> Massimo viene attualmente calcolato per l'intervallo di 5 minuti sulla base dei campioni secondo 15 del numero di sessioni simultanee.|  
|dtu_limit|**int**|Max database DTU impostazione corrente per il database durante questo intervallo.|  
  
> [!TIP]  
>  Per ulteriori informazioni di contesto su questi limiti e i livelli di servizio, vedere gli argomenti [livelli di servizio](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) e [funzionalità di livello e i limiti del servizio](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/).  
  
 La tabella seguente descrive le colonne disponibili in un server v11:  
  
|Colonne (server v11)|Tipo di dati|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Ora UTC che indica l'inizio dell'intervallo di reporting di 5 minuti.|  
|end_time|**datetime**|Ora UTC che indica la fine dell'intervallo di reporting di 5 minuti.|  
|database_name|**nvarchar**|Nome del database.|  
|sku|**nvarchar**|Livello di servizio del database. Di seguito sono indicati i valori possibili:<br /><br /> Web<br /><br /> Business<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium|  
|usage_in_seconds|**int**|*Nota: Questa colonna è deprecata per v11 e il relativo valore è sempre impostato su 0.*<br /><br /> Tempo della CPU utilizzato dopo l'ultima misurazione.<br /><br /> Per la misurazione della CPU, è consigliabile utilizzare il **avg_cpu_cores_used** colonna anziché questa colonna.|  
|storage_in_megabytes|**decimal**|Dimensioni massime di archiviazione in megabyte per il periodo di tempo, inclusi i dati del database, gli indici, le stored procedure e i metadati.|  
|avg_cpu_cores_used|**decimal**|*Nota: Questa colonna è deprecata per v11 e il relativo valore è sempre impostato su 0.*<br /><br /> Core della CPU medi utilizzati in questo intervallo.|  
|avg_physical_read_iops|**decimal**|*Nota: Questa colonna è deprecata per v11 e il relativo valore è sempre impostato su 0.*<br /><br /> IOPS di lettura medie in questo intervallo.|  
|avg_physical_write_iops|**decimal**|*Nota: Questa colonna è deprecata per v11 e il relativo valore è sempre impostato su 0.*<br /><br /> IOPS di scrittura medie in questo intervallo.|  
|active_memory_used_kb|**bigint**|*Nota: Questa colonna è deprecata per v11 e il relativo valore è sempre impostato su 0.*<br /><br /> Conteggio di memoria attiva utilizzata alla fine di questo intervallo.|  
|active_session_count|**int**|Conteggio di sessioni attive alla fine di questo intervallo.|  
|active_worker_count|**int**|Conteggio di dipendenti attivi alla fine di questo intervallo.|  
|avg_cpu_percent|**decimal**|Percentuale dell'utilizzo medio del calcolo del limite del livello del servizio.|  
|avg_physical_data_read_percent|**decimal**|Percentuale dell'utilizzo medio di I/O in base al limite del livello del servizio.|  
|avg_log_write_percent|**decimal**|Percentuale dell'utilizzo medio delle risorse di scrittura del limite del livello del servizio.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni per connettersi al virtuale **master** database.  
  
## <a name="remarks"></a>Osservazioni  
 I dati restituiti da **resource_stats** è espressa come percentuale del valore massimo consentito di limiti DTU del livello di servizio/prestazioni livello in esecuzione per i database Basic, Standard e Premium.  Per i livelli Web e Business questi numeri indicano le percentuali in termini di livello di prestazioni Standard S2.  Ad esempio, quando l'esecuzione avviene su un database Web, se avg_cpu_percent restituisce 70%, tale valore indica il 70% del limite per il livello S2. Inoltre, per i livelli Web e Business le percentuali possono riflettere un numero oltre il 100%, basato anch'esso sul limite per il livello S2.  
  
 Quando un database è un membro di un pool elastico, presentate come valori percentuali, le statistiche di risorse sono espressi come percentuale del limite di DTU massimo per i database come set di configurazione del pool elastico.  
  
 Per una vista più granulare di questi dati, usare **Sys.dm db_resource_stats** vista a gestione dinamica in un database utente. Questa vista acquisisce i dati ogni 15 secondi e conserva i dati cronologici per 1 ora.  Per ulteriori informazioni, vedere [Sys.dm db_resource_stats &#40; Database SQL di Azure &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti i database che hanno una media di almeno l'80% di utilizzo del calcolo nell'ultima settimana.  
  
```  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT database_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY database_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
  
 L'esempio seguente calcola la percentuale di utilizzo medio di DTU per un database specifico. Questa query funziona solo se viene eseguita in un server v11.  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
   FROM (VALUES (avg_cpu_percent), (avg_physical_data_read_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.resource_stats   
WHERE database_name = '<your db name>'   
ORDER BY end_time DESC;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Livelli di servizio](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Limiti e delle funzionalità di livello di servizio](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
