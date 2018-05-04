---
title: sys.dm_exec_query_statistics_xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
caps.latest.revision: 6
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: f52c0a1a39d3c8ab56241644e4c8e4d42c9d0af7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Restituisce il piano di esecuzione per le richieste in elaborazione di query. Utilizzare questa DMV per recuperare showplan XML con le statistiche temporanee. 

## <a name="syntax"></a>Sintassi

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>Argomenti 
*session_id*  
 L'id di sessione è in esecuzione il batch da ricercare. *session_id* viene **smallint**. *session_id* può essere ottenuto dagli oggetti a gestione dinamica seguenti:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Tabella restituita
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|ID della sessione. Non ammette i valori NULL.|
|request_id|**int**|ID della richiesta. Non ammette i valori NULL.|
|sql_handle|**varbinary(64)**|Mappa hash del testo SQL della richiesta. Ammette valori Null.|
|plan_handle|**varbinary(64)**|Mappa hash del piano di query. Ammette valori Null.|
|query_plan|**xml**|Showplan XML con parziale delle statistiche. Ammette valori Null.|

## <a name="remarks"></a>Osservazioni
Questa funzione di sistema è disponibile a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1.

Questa funzione di sistema funziona in entrambi **standard** e **lightweight** infrastruttura di analisi delle statistiche di esecuzione di query.  
  
**Standard** le statistiche di profiling infrastruttura possono essere abilitate utilizzando:
  -  [SET STATISTICS XML SU](../../t-sql/statements/set-statistics-xml-transact-sql.md)
  -  [SET STATISTICS PROFILE IN](../../t-sql/statements/set-statistics-profile-transact-sql.md)
  -  il `query_post_execution_showplan` eventi estesi.  
  
**Lightweight** statistiche infrastruttura di analisi sono disponibile in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e possono essere abilitati:
  -  A livello globale tramite traccia flag 7412.
  -  Utilizzo di [ *query_thread_profile* ](http://support.microsoft.com/kb/3170113) eventi estesi.
  
> [!NOTE]
> Dopo aver abilitato dal flag di traccia 7412, profilatura leggera verrà abilitata per qualsiasi consumer dell'infrastruttura anziché standard, ad esempio la DMV di analisi le statistiche di esecuzione query [Sys.dm exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md).
> Tuttavia, la profilatura standard viene ancora usato per SET STATISTICS XML, *Includi piano effettivo* azione in [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)], e `query_post_execution_showplan` xEvent.

> [!IMPORTANT]
> TPC-c come test di carico di lavoro, consentendo l'infrastruttura di analisi statistiche lightweight aggiunge un overhead di 1,5 o 2 percento. Al contrario, l'infrastruttura di analisi statistiche standard è possibile aggiungere fino al 90% di overhead per lo stesso scenario di carico di lavoro.

## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione `VIEW SERVER STATE` per il server.  

## <a name="examples"></a>Esempi  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. Esaminando le statistiche piano e l'esecuzione di query in tempo reale per un batch in esecuzione  
 Le seguenti query di esempio **Sys.dm exec_requests** per trovare la query specifica e copiare il relativo `session_id` dall'output.  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Per ottenere le statistiche di piano e l'esecuzione di query in tempo reale, utilizzare copiato `session_id` con funzione di sistema **sys.dm_exec_query_statistics_xml**.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 O la combinazione per tutte le richieste in esecuzione.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>Vedere anche
  [Flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

