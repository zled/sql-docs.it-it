---
title: Sys.dm_os_job_object (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 04/17/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1924f6c606d2d07d816409278cf9af56ecd868f8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmosjobobject-azure-sql-database"></a>Sys.dm_os_job_object (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Restituisce una riga singola che descrive la configurazione dell'oggetto processo che gestisce il processo di SQL Server, nonché alcune statistiche sui consumi di risorse a livello di oggetto processo. Restituisce un set vuoto se SQL Server non è in esecuzione in un oggetto processo. 

Un oggetto processo è un costrutto di Windows che implementa la governance delle risorse di CPU, memoria e i/o a livello di sistema operativo. Per ulteriori informazioni sugli oggetti di processo, vedere [gli oggetti processo](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx). 

> [!NOTE]
> Il sys.dm_os_job_object DMV può attualmente vengono visualizzati come sys.dm_job_object. Si tratta temporaneo: `sys.dm_os_job_object` sarà il nome di questa DMV permanente. 
  
|Colonne|Tipo di dati|Description|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|Specifica la parte di cicli del processore utilizzabili durante ogni intervallo di pianificazione thread di SQL Server. Il valore viene restituito come una percentuale di cicli disponibili entro un intervallo di pianificazione del ciclo di 10000. Ad esempio, i valore 100 indica che utilizzano thread core CPU sono alla capacità massima.|
|cpu_affinity_mask|**bigint**|Una maschera di bit che descrive quale processori logici il processo di SQL Server può utilizzare all'interno del gruppo di processore. Ad esempio, cpu_affinity_mask 255 (1111 1111 in formato binario) significa che i primi otto processori logici sono utilizzabile.|
|cpu_affinity_group|**int**|Il numero del gruppo di processore utilizzato da SQL Server.|
|memory_limit_mb|**bigint**|Quantità massima di memoria riservata, in MB, che tutti i processi nell'oggetto processo, incluso SQL Server, è possono utilizzare in modo cumulativo.| 
|process_memory_limit_mb |**bigint**|Quantità massima di memoria riservata, in MB, che è possibile utilizzare un singolo processo dell'oggetto processo, ad esempio SQL Server.|
|workingset_limit_mb |**bigint**|Quantità massima di memoria, in MB, che è possibile usare il set di lavoro di SQL Server.|
|non_sos_mem_gap_mb|**bigint**|La quantità di memoria, espressa in MB, riservare per gli stack di thread, le DLL e altre allocazioni di memoria non SOS. Memoria di destinazione SOS è la differenza tra `process_memory_limit_mb` e `non_sos_mem_gap_mb`.| 
|low_mem_signal_threshold_mb|**bigint**|Soglia di memoria, in MB. Quando la quantità di memoria disponibile per l'oggetto processo è di sotto questa soglia, viene inviato un segnale di notifica di memoria insufficiente per il processo di SQL Server. |
|total_user_time|**bigint**|Numero totale di 100 segni di graduazione ns impiegate dal thread all'interno dell'oggetto processo sono in modalità utente, poiché è stato creato l'oggetto processo. |
|total_kernel_time |**bigint**|Numero totale di 100 segni di graduazione ns impiegate dal thread all'interno dell'oggetto processo sono in modalità kernel, poiché è stato creato l'oggetto processo. |
|write_operation_count |**bigint**|Il numero totale di operazioni dei / o su dischi locali emessi da SQL Server perché è stato creato l'oggetto processo di scrittura. |
|read_operation_count |**bigint**|Numero totale di operazioni dei / o lettura su dischi locali emessi da SQL Server perché è stato creato l'oggetto processo. |
|peak_process_memory_used_mb|**bigint**|La quantità massima di memoria, in MB, di un singolo processo dell'oggetto processo, ad esempio SQL Server utilizzata dall'oggetto processo è stato creato.| 
|peak_job_memory_used_mb|**bigint**|La quantità massima di memoria, in MB, che tutti i processi dell'oggetto processo hanno utilizzato App ha complessivamente poiché l'oggetto processo è stata creata.|
  
## <a name="permissions"></a>Autorizzazioni  
Nell'istanza gestita di Database SQL, è necessario `VIEW SERVER STATE` l'autorizzazione. Nel Database SQL, è necessario il `VIEW DATABASE STATE` l'autorizzazione per il database.  
 
## <a name="see-also"></a>Vedere anche  

Per informazioni su istanze gestite, vedere [istanza gestita di SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
