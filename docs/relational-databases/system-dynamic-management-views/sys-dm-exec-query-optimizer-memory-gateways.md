---
title: Sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL) | Documenti Microsoft
description: Restituisce lo stato corrente della risorsa semafori utilizzato per l'ottimizzazione delle query simultanee. limitazione totale
ms.custom: ''
ms.date: 04/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_memory_gateways_TSQL
- dm_exec_query_optimizer_memory_gateways
- sys.dm_exec_query_optimizer_memory_gateways_TSQL
- sys.dm_exec_query_optimizer_memory_gateways
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_memory_gateways dynamic management view
author: josack
ms.author: josack
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 90645c4d2d0bff9716926c0260853a76d39941d5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecqueryoptimizermemorygateways-transact-sql"></a>sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Restituisce lo stato corrente della risorsa semafori utilizzato per l'ottimizzazione delle query simultanee. limitazione totale.

|Colonna|Tipo|Description|  
|----------|---------------|-----------------|  
|**pool_id**|**int**|ID pool di risorse in Resource Governor|  
|**name**|**sysname**|Compilare il nome di controllo (Gateway Small, Medium Gateway, Gateway di grandi dimensioni)|
|**max_count**|**int**|Il numero massimo configurato di compilazioni simultanee|
|**active_count**|**int**|Il numero attualmente attivo di compilazioni in questo controllo|
|**waiter_count**|**int**|Il numero di oggetti waiter in questo controllo|
|**threshold_factor**|**bigint**|Fattore di soglia che definisce la parte di memoria massima utilizzata da ottimizzazione delle query.  Per il gateway di piccole dimensioni, threshold_factor indica l'utilizzo della memoria query optimizer massima in byte per una query prima che sia necessario per ottenere un accesso nel gateway di piccole dimensioni.  Per il gateway di medie e grandi dimensioni, threshold_factor illustra la parte della memoria totale del server disponibile per questo controllo. Quando si calcola la soglia di utilizzo della memoria per il controllo e viene utilizzato come divisore.|
|**Soglia**|**bigint**|Memoria successiva di soglia in byte.  La query è necessario per ottenere l'accesso a questo gateway, se l'utilizzo della memoria raggiunge questa soglia.  "-1" se la query non è necessario ottenere un accesso a questo gateway.|
|**is_active**|**bit**|Se la query è necessario passare il controllo corrente o non.|


## <a name="permissions"></a>Autorizzazioni  
SQL Server richiede l'autorizzazione VIEW SERVER STATE nel server.

Database SQL di Azure richiede l'autorizzazione VIEW DATABASE STATE nel database.


## <a name="remarks"></a>Osservazioni  
SQL Server utilizza un approccio a più livelli di gateway per limitare il numero di compilazioni simultanee consentite.  Tre gateway vengono utilizzati, tra cui piccole, medie e grandi. I gateway per evitare l'esaurimento delle risorse di memoria complessiva dai consumer che richiedono memoria più grande di compilazione.

È in attesa su un risultato gateway nella compilazione posticipata. Oltre ai ritardi nella compilazione, le richieste limitate avrà un RESOURCE_SEMAPHORE_QUERY_COMPILE associato accumulo di tipo di attesa. Il tipo di attesa RESOURCE_SEMAPHORE_QUERY_COMPILE potrebbe indicare che le query utilizzano una grande quantità di memoria per la compilazione e che la memoria è esaurita, o in alternativa è disponibile memoria sufficiente disponibile in generale, tuttavia disponibile unità in uno specifico gateway sono stati esauriti. L'output di **sys.dm_exec_query_optimizer_memory_gateways** può essere utilizzato per risolvere i problemi relativi a scenari in cui era presente memoria insufficiente per compilare un piano di esecuzione di query.  

## <a name="examples"></a>Esempi  

### <a name="a-viewing-statistics-on-resource-semaphores"></a>A. Visualizzazione delle statistiche durante i semafori di risorse  
Quali sono le statistiche di ottimizzazione memoria gateway corrente per questa istanza di SQL Server?

```  
SELECT [pool_id], [name], [max_count], [active_count],
       [waiter_count], [threshold_factor], [threshold],
       [is_active]
FROM sys.dm_exec_query_optimizer_memory_gateways;   

```  

## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](./system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](./execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[Come utilizzare il comando DBCC MEMORYSTATUS per monitorare l'utilizzo di memoria in SQL Server 2005](https://support.microsoft.com/help/907877/how-to-use-the-dbcc-memorystatus-command-to-monitor-memory-usage-on-sql-server-2005)
[la compilazione di query di grandi dimensioni è in attesa in RESOURCE_SEMAPHORE_QUERY_COMPILE in SQL Server 2014](https://support.microsoft.com/help/3024815/large-query-compilation-waits-on-resource-semaphore-query-compile-in-sql-server-2014)
