---
title: Sys.dm_exec_distributed_requests (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_REQUESTS
- DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- sys.dm_exec_distributed_sql_requests management view
- PolyBase
- dm_exec_distributed_sql_requests management view
ms.assetid: c041d416-d8c6-435e-a563-6a310abd33e3
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b60432de0dda1417bcb350ccf4337edd09375a26
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmexecdistributedrequests-transact-sql"></a>sys.dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutte le richieste attualmente o recentemente active nelle query di PolyBase. Contiene una riga per ogni richiesta o alla query.  
  
 In base a una sessione e un utente può, ID richiesta quindi recuperare le richieste distribuite effettive generate per l'esecuzione: tramite sys.dm_exec_distributed_requests. Ad esempio, una query che includono SQL regolari e le tabelle esterne SQL verrà scomposte in varie istruzioni/richieste eseguite in tutti i nodi di calcolo diversi. Per registrare i passaggi distribuiti in tutti i nodi di calcolo, si introduce un ID esecuzione 'global' può essere usato per tenere traccia di tutte le operazioni sui nodi di calcolo associati con una particolare richiesta e l'operatore, rispettivamente.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Chiave per la visualizzazione. Id numerico univoco associato alla richiesta.|Valore univoco in tutte le richieste nel sistema.|  
|execution_id|**nvarchar(32**|Id numerico univoco associato alla sessione in cui è stata eseguita la query.||  
|status|**nvarchar(32**|Stato corrente della richiesta.|'Pending', 'Authorizing', 'AcquireSystemResources', 'Initializing', 'Plan', 'Parsing', 'AquireResources', 'Running', 'Cancelling', 'Complete', 'Failed', 'Cancelled'.|  
|error_id|**nvarchar(36)**|Id univoco dell'errore associato alla richiesta, se presente.|Se si è verificato alcun errore, impostato su NULL.|  
|start_time|**datetime**|Ora di inizio dell'esecuzione della richiesta.|0 per le richieste in coda. in caso contrario, valido datetime minore o uguale all'ora corrente.|  
|end_time|**datetime**|Ora in cui il motore, è stata completata la richiesta di compilazione.|Null per le richieste in coda o attive. in caso contrario, un valore datetime valido minore o uguale all'ora corrente.|  
|total_elapsed_time|**int**|Tempo trascorso nell'esecuzione, poiché la richiesta è stata avviata, in millisecondi.|Compreso tra 0 e la differenza tra start_time ed end_time. Se total_elapsed_time supera il valore massimo per un numero intero, total_elapsed_time continuerà a essere il valore massimo. Questa condizione genera l'avviso "è stato superato il valore massimo." Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
  
## <a name="see-also"></a>Vedere anche  
 [PolyBase, risoluzione dei problemi con viste a gestione dinamica](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
