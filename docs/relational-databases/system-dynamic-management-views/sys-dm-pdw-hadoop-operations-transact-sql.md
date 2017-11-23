---
title: Sys.dm_pdw_hadoop_operations (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
caps.latest.revision: "5"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9b735d4759d3164ae61da717ec18d54ab8661441
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwhadoopoperations-transact-sql"></a>Sys.dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene una riga per ogni processo MapReduce propagato ad Hadoop come parte dell'esecuzione un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] query su una tabella esterna di Hadoop. Ogni processo MapReduce rappresenta uno dei predicati della query. Viene utilizzato solo quando la distribuzione del predicato è abilitata per le query su tabelle esterne di Hadoop.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|ID per questa operazione esterna di Hadoop.|Stesso ID in [sys.dm_pdw_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Indice del passaggio di query che fa riferimento a questa operazione Hadoop.|Uguale a step_index in [sys.dm_pdw_request_steps &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Descrive il tipo di operazione esterna.|'Operazione esterna di Hadoop'|  
|operation_name|**nvarchar(4000)**|L'ID di processo per un processo MapReduce. Valore restituito da Hadoop dopo [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] invia il processo.||  
|map_progress|**float**|La percentuale di dati di input che sono stati utilizzati finora dal processo di mapping.|Numero a virgola mobile tra e tra 0 e 100.|  
|reduce_progress|**int**|La percentuale del processo di riduzione che è stata completata...|Numero a virgola mobile tra e tra 0 e 100.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
