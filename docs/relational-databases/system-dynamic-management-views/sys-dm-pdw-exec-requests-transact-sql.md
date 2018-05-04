---
title: sys.dm_pdw_exec_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f6ceea1c7a604b2bfd98a158b383814990644391
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutte le richieste di recente o attualmente attivi nel [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Contiene una riga per ogni richiesta o alla query.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Chiave per la visualizzazione. Id numerico univoco associato alla richiesta.|Valore univoco in tutte le richieste nel sistema.|  
|session_id|**nvarchar(32)**|Id numerico univoco associato alla sessione in cui è stata eseguita la query. Vedere [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Stato corrente della richiesta.|'In esecuzione', 'Sospeso', 'Completato', 'Annullata', "Non riuscito".|  
|submit_time|**datetime**|Ora in cui è stata inviata la richiesta per l'esecuzione.|Valido **datetime** minore o uguale alla start_time e all'ora corrente.|  
|start_time|**datetime**|Ora di inizio dell'esecuzione della richiesta.|NULL per le richieste in coda. in caso contrario, valido **datetime** minore o uguale all'ora corrente.|  
|end_compile_time|**datetime**|Ora in cui il motore, è stata completata la richiesta di compilazione.|NULL per le richieste che non sono stati compilati. in caso contrario valido **datetime** start_time minore e minore o uguale all'ora corrente.|
|end_time|**datetime**|Ora in cui l'esecuzione della richiesta completata, non è riuscita o è stata annullata.|Null per le richieste in coda o attive. in caso contrario, un valido **datetime** minore o uguale all'ora corrente.|  
|total_elapsed_time|**int**|Tempo trascorso nell'esecuzione, poiché la richiesta è stata avviata, in millisecondi.|Compreso tra 0 e la differenza tra start_time ed end_time.<br /><br /> Se total_elapsed_time supera il valore massimo per un numero intero, total_elapsed_time continuerà a essere il valore massimo. Questa condizione genera l'avviso "è stato superato il valore massimo."<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
|Etichetta|**nvarchar(255)**|Stringa di etichetta facoltativa associata alcune istruzioni di query di selezione.|Qualsiasi stringa contenente "a-z", 'A-Z','0-9', '_'.|  
|error_id|**nvarchar(36)**|Id univoco dell'errore associato alla richiesta, se presente.|Vedere [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); se si è verificato alcun errore impostato su NULL.|  
|database_id|**int**|Identificatore del database utilizzato dal contesto esplicita (ad esempio, utilizzare DB_X).|Vedere id nel [Sys. Databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|comando|**nvarchar(4000)**|Contiene il testo completo della richiesta come inviato dall'utente.|Qualsiasi testo di query o di richiesta valido. Le query da più di 4000 byte vengono troncate.|  
|resource_class|**nvarchar(20)**|Classe di risorse per questa richiesta. Vedere correlati **concurrency_slots_used** in [sys.dm_pdw_resource_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere "Minimo e massimo valori" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE.  
  
## <a name="security"></a>Sicurezza  
 Sys.dm_pdw_exec_requests non filtra i risultati della query in base alle autorizzazioni specifiche del database. Account di accesso con autorizzazione VIEW SERVER STATE possono ottenere risultati risultati della query per tutti i database  
  
> [!WARNING]  
>  Un utente malintenzionato può utilizzare sys.dm_pdw_exec_requests per recuperare informazioni sugli oggetti di database specifico configurando semplicemente l'autorizzazione VIEW SERVER STATE e dalla mancanza di un'autorizzazione specifico del database.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
