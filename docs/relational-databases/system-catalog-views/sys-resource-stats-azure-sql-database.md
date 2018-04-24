---
title: Sys. resource_stats (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 28
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 947214e4b8da0d4d76ab16eb24bd73dec994aeb2
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce i dati di archiviazione e di utilizzo della CPU per un database SQL di Azure. I dati vengono raccolti e aggregati in intervalli di cinque minuti. Per ciascun database utente, è disponibile una riga per ogni finestra di segnalazione di cinque minuti in cui è presente una modifica nell'utilizzo della risorsa. I dati restituiti includono l'utilizzo della CPU, modifica delle dimensioni di archiviazione o modifica della SKU del database. I database inattivi senza modifiche potrebbero non avere righe per ogni intervallo di cinque minuti. I dati cronologici vengono mantenuti per circa 14 giorni.  
  
 Il **resource_stats** visualizzazione contiene diverse definizioni a seconda della versione del Server di Database di SQL Azure che è associato il database. Prendere in considerazione queste differenze e le eventuali modifiche richieste dall'applicazione durante l'aggiornamento a una nuova versione del server.  
  
 La tabella seguente descrive le colonne disponibili in un server v12:  
  
|Colonne|Tipo di dati|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Ora UTC che indica l'inizio dell'intervallo di segnalazione di cinque minuti.|  
|end_time|**datetime**|Ora UTC che indica la fine dell'intervallo di segnalazione di cinque minuti.|  
|database_name|**varchar**|Nome del database utente.|  
|sku|**varchar**|Livello di servizio del database. Di seguito sono indicati i valori possibili:<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium<br /><br />Utilizzo generico<br /><br />Business Critical|  
|storage_in_megabytes|**float**|Dimensioni massime di archiviazione in megabyte per il periodo di tempo, inclusi i dati del database, indici, stored procedure e metadati.|  
|avg_cpu_percent|**numeric**|Percentuale dell'utilizzo medio del calcolo del limite del livello del servizio.|  
|avg_data_io_percent|**numeric**|Percentuale dell'utilizzo medio di I/O in base al limite del livello del servizio.|  
|avg_log_write_percent|**numeric**|Percentuale dell'utilizzo medio delle risorse di scrittura del limite del livello del servizio.|  
|max_worker_percent|**decimal(5,2)**|Massimi simultanee processi di lavoro (richieste) come percentuale del limite del livello di servizio del database.<br /><br /> Massimo viene attualmente calcolato per l'intervallo di cinque minuti sulla base dei campioni di 15 secondi di conteggi di lavoro simultanei.|  
|max_session_percent|**decimal(5,2)**|Numero massimo di sessioni simultaneo espresso come percentuale del limite del livello di servizio del database.<br /><br /> Numero massimo è attualmente calcolato per l'intervallo di cinque minuti sulla base dei campioni di 15 secondi di conteggio di sessioni simultanee.|  
|dtu_limit|**int**|Max database DTU impostazione corrente per il database durante questo intervallo. |  
  
> [!TIP]  
>  Per ulteriori informazioni di contesto su questi limiti e i livelli di servizio, vedere gli argomenti [livelli di servizio](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/).  
    
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni per connettersi al virtuale **master** database.  
  
## <a name="remarks"></a>Osservazioni  
 I dati restituiti da **Sys. resource_stats** espressa come percentuale del valore massimo consentito i limiti del livello di servizio/prestazioni livello sia in esecuzione.  
  
 Quando un database è un membro di un pool elastico, presentate come i valori percentuali, le statistiche di risorse sono espressi come percentuale del limite massimo per i database impostati nella configurazione del pool elastico.  
  
 Per una vista più granulare di questi dati, usare **Sys.dm db_resource_stats** vista a gestione dinamica in un database utente. Questa vista acquisisce dati ogni 15 secondi e conserva i dati cronologici per 1 ora.  Per altre informazioni, vedere [db_resource_stats &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti i database che hanno una media di almeno l'80% di utilizzo del calcolo nell'ultima settimana.  
  
```sql  
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
    
## <a name="see-also"></a>Vedere anche  
 [Livelli di servizio](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Limiti e delle funzionalità di livello di servizio](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
