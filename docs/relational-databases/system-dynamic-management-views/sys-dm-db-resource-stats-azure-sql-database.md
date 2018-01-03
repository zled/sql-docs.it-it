---
title: Sys.dm db_resource_stats (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
caps.latest.revision: "11"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b1fa8f540e8f16d901eb41138bc7ee153339cb5a
ms.sourcegitcommit: 6e016a4ffd28b09456008f40ff88aef3d911c7ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2017
---
# <a name="sysdmdbresourcestats-azure-sql-database"></a>sys.dm_db_resource_stats (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce il consumo di CPU, i/o e memoria per un [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] database. È presente una riga per ogni 15 secondi, anche se non esiste alcuna attività nel database. I dati cronologici vengono mantenuti per un'ora.  
  
|Colonne|Tipo di dati|Description|  
|-------------|---------------|-----------------|  
|end_time|**datetime**|Ora UTC che indica la fine dell'intervallo di reporting corrente.|  
|avg_cpu_percent|**Decimal (5,2)**|Percentuale dell'utilizzo medio del calcolo del limite del livello del servizio.|  
|avg_data_io_percent|**Decimal (5,2)**|Media di dati utilizzo i/o in percentuale del limite del livello del servizio.|  
|avg_log_write_percent|**Decimal (5,2)**|Percentuale dell'utilizzo medio delle risorse di scrittura del limite del livello del servizio.|  
|avg_memory_usage_percent|**Decimal (5,2)**|Percentuale dell'utilizzo medio della memoria del limite del livello del servizio.<br /><br /> Ciò include la memoria utilizzata per l'archiviazione di oggetti di OLTP In memoria.|  
|xtp_storage_percent|**Decimal (5,2)**|Utilizzo di archiviazione per OLTP In memoria in percentuale del limite del livello del servizio (alla fine dell'intervallo di reporting). Ciò include la memoria utilizzata per l'archiviazione degli oggetti OLTP In memoria: le tabelle con ottimizzazione per la memoria, indici e le variabili di tabella. Include inoltre la memoria utilizzata per l'elaborazione di operazioni ALTER TABLE.<br /><br /> Restituisce 0 se OLTP In memoria non viene utilizzato nel database.|  
|max_worker_percent|**Decimal (5,2)**|Massimi simultanee processi di lavoro (richieste) in percentuale del limite del livello di servizio del database.|  
|max_session_percent|**Decimal (5,2)**|Numero massimo di sessioni simultaneo espresso come percentuale del limite del livello di servizio del database.|  
|dtu_limit|**int**|Max database DTU impostazione corrente per il database durante questo intervallo.|  
  
> [!TIP]  
>  Per ulteriori informazioni di contesto su questi limiti e i livelli di servizio, vedere gli argomenti [livelli di servizio](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) e [funzionalità di livello e i limiti del servizio](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/).  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista richiede l'autorizzazione VIEW DATABASE STATE.  
  
## <a name="remarks"></a>Osservazioni  
 I dati restituiti da **Sys.dm db_resource_stats** è espressa come percentuale del valore massimo consentito di limiti DTU del livello di servizio/prestazioni livello in esecuzione per i database Basic, Standard e Premium. Per i livelli Web e Business questi numeri indicano le percentuali in termini di livello di prestazioni Standard S2. Ad esempio, quando l'esecuzione avviene in un database Web o Business, se avg_cpu_percent restituisce 70%, tale valore indica il 70% del limite per il livello S2. Inoltre, per i livelli Web e Business le percentuali possono riflettere un numero oltre il 100%, basato anch'esso sul limite per il livello S2.  
  
 Se è stato effettuato il failover del database in un altro server negli ultimi 60 minuti, la vista restituirà solo i dati relativi al tempo in cui il database è stato primario dopo il failover.  
  
 Per una vista meno dettagliata di questi dati, utilizzare **resource_stats** vista del catalogo di **master** database. Questa vista acquisisce i dati ogni 5 minuti e conserva i dati cronologici per 14 giorni.  Per ulteriori informazioni, vedere [resource_stats &#40; Database SQL di Azure &#41; ](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md).  
  
 Quando un database è un membro di un pool elastico, presentate come valori percentuali, le statistiche di risorse sono espressi come percentuale del limite di DTU massimo per i database come set di configurazione del pool elastico.  
  
## <a name="example"></a>Esempio  
  
> [!NOTE]  
>  Per i livelli Web e Business questi numeri indicano le percentuali in termini di livello di prestazioni Standard S2. Ad esempio, quando l'esecuzione avviene in un database Web o Business, se avg_cpu_percent restituisce 70%, tale valore indica il 70% del limite per il livello S2. Inoltre, per i livelli Web e Business le percentuali possono riflettere un numero oltre il 100%, basato anch'esso sul limite per il livello S2.  
  
 L'esempio seguente restituisce i dati di utilizzo delle risorse ordinati in base l'ora più recente per il database attualmente connesso.  
  
```  
SELECT * FROM sys.dm_db_resource_stats ORDER BY end_time DESC;  
  
```  
  
 L'esempio seguente identifica il consumo medio di DTU in termini di percentuale del limite massimo consentito di DTU nel livello di prestazioni per il database utente nell'ora precedente. Provare ad aumentare il livello di prestazioni se queste percentuali si avvicinano in modo continuativo al 100%.  
  
```  
SELECT end_time,   
  (SELECT Max(v)    
   FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS    
   value(v)) AS [avg_DTU_percent]   
FROM sys.dm_db_resource_stats;  
  
```  
  
 L'esempio seguente restituisce i valori medi e massimi relativi alla percentuale di utilizzo della CPU, all'utilizzo di dati e I/O del log e al consumo di memoria nell'ultima ora.  
  
```  
SELECT    
    AVG(avg_cpu_percent) AS 'Average CPU Utilization In Percent',   
    MAX(avg_cpu_percent) AS 'Maximum CPU Utilization In Percent',   
    AVG(avg_data_io_percent) AS 'Average Data IO In Percent',   
    MAX(avg_data_io_percent) AS 'Maximum Data IO In Percent',   
    AVG(avg_log_write_percent) AS 'Average Log Write Utilization In Percent',   
    MAX(avg_log_write_percent) AS 'Maximum Log Write Utilization In Percent',   
    AVG(avg_memory_usage_percent) AS 'Average Memory Usage In Percent',   
    MAX(avg_memory_usage_percent) AS 'Maximum Memory Usage In Percent'   
FROM sys.dm_db_resource_stats;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. resource_stats &#40; Database SQL di Azure &#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Livelli di servizio](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Limiti e delle funzionalità di livello di servizio](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
