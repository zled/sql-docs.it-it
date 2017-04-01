---
title: "SQL Server, Oggetto Batch Resp Statistics | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQLServer:Batch Resp Statistics"
ms.assetid: a58e8733-6a8d-4b47-b5cb-042e813d808a
caps.latest.revision: 3
author: "dagiro"
ms.author: "v-dagir"
manager: "jhubbard"
caps.handback.revision: 3
---
# SQL Server, Oggetto Batch Resp Statistics
L'oggetto prestazioni **SQLServer:Batch Resp Statistics** fornisce i contatori per tenere traccia dei tempi di risposta dei batch di SQL Server.

La tabella seguente descrive gli oggetti prestazioni **Batch Resp Statistics** di SQL Server.


|**Contatori di SQL Server Batch Resp Statistics**|Description|  
|-------------|-----------------|  
|**Batch >= 000000 ms e \< 000001 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 0 ms ma minori di 1 ms|
|**Batch >= 000001 ms e \< 000002 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 1 ms ma minori di 2 ms|
|**Batch >= 000002 ms e \< 000005 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 2 ms ma minori di 5 ms|
|**Batch >= 000005 ms e \< 000010 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 5 ms ma minori di 10 ms|
|**Batch >= 000010 ms e \< 000020 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 10 ms ma minori di 20 ms|
|**Batch >= 000020 ms e \< 000050 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 20 ms ma minori di 50 ms|
|**Batch >= 000050 ms e \< 000100 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 50 ms ma minori di 100 ms|
|**Batch >= 000100 ms e \< 000200 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 100 ms ma minori di 200 ms|
|**Batch >= 000200 ms e \< 000500 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 200 ms ma minori di 500 ms|
|**Batch >= 000500 ms e \< 001000 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 500 ms ma minori di 1.000 ms|
|**Batch >= 001000 ms e \< 002000 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 1.000 ms ma minori di 2.000 ms|
|**Batch >= 002000 ms e \< 005000 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 2.000 ms ma minori di 5.000 ms|
|**Batch >= 005000 ms e \< 010000 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 5000 ms ma minori di 10.000 ms|
|**Batch >= 010000 ms e \< 020000 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 10.000 ms ma minori di 20.000 ms|
|**Batch >= 020000 ms e \< 050000 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 20.000 ms ma minori di 50.000 ms|
|**Batch >= 050000 ms e \< 100000 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 50.000 ms ma minori di 100.000 ms| 
|**Batch >= 100000 ms**|Numero di batch SQL con tempi di risposta maggiori o uguali a 100.000 ms| 

Per ogni contatore nell'oggetto sono disponibili le istanze seguenti:  
  
|Elemento|Description|  
|----------|-----------------|  
|**CPU Time:Requests**|Tempo CPU impiegato per la richiesta.|  
|**CPU Time:Total(ms)**|Tempo CPU totale impiegato per il batch.|  
|**Elapsed Time:Requests**|Tempo trascorso della richiesta.|  
|**Elapsed Time:Total(ms)**|Tempo trascorso del batch.|  

## Vedere anche
[Oggetto Plan Cache di SQL Server](../../relational-databases/performance-monitor/sql-server-plan-cache-object.md)  
[Monitoraggio dell'utilizzo delle risorse (Monitor di sistema)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  