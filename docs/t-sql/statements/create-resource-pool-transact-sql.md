---
title: CREARE il POOL di risorse (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE RESOURCE POOL
- RESOURCE POOL
- CREATE_RESOURCE_POOL_TSQL
- RESOURCE_POOL_TSQL
dev_langs: TSQL
helpviewer_keywords: CREATE RESOURCE POOL
ms.assetid: 82712505-c6f9-4a65-a469-f029b5a2d6cd
caps.latest.revision: "42"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6da47e346606170b29798b0301c10c5adeeed055
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="create-resource-pool-transact-sql"></a>CREATE RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un pool di risorse di Resource Governor in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un pool di risorse rappresenta un subset delle risorse fisiche (memoria, CPU e IO) di un'istanza del motore di database. Resource Governor consente a un amministratore di database di distribuire le risorse del server tra pool di risorse, fino a un massimo di 64 pool. Resource Governor non è disponibile in tutte le edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE RESOURCE POOL pool_name  
[ WITH  
    (  
        [ MIN_CPU_PERCENT = value ]  
        [ [ , ] MAX_CPU_PERCENT = value ]   
        [ [ , ] CAP_CPU_PERCENT = value ]   
        [ [ , ] AFFINITY {SCHEDULER =  
                  AUTO 
                | ( <scheduler_range_spec> )   
                | NUMANODE = ( <NUMA_node_range_spec> )
                } ]   
        [ [ , ] MIN_MEMORY_PERCENT = value ]  
        [ [ , ] MAX_MEMORY_PERCENT = value ]  
        [ [ , ] MIN_IOPS_PER_VOLUME = value ]  
        [ [ , ] MAX_IOPS_PER_VOLUME = value ]  
    )   
]  
[;]  
  
<scheduler_range_spec> ::=  
{ SCHED_ID | SCHED_ID TO SCHED_ID }[,…n]  
  
<NUMA_node_range_spec> ::=  
{ NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID }[,…n]  
```  
  
## <a name="arguments"></a>Argomenti  
 *pool_name*  
 Nome definito dall'utente per il pool di risorse. *pool_name* è un valore alfanumerico, può essere fino a 128 caratteri, deve essere univoco all'interno di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e deve essere conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 MIN_CPU_PERCENT =*valore*  
 Specifica la larghezza di banda media garantita della CPU concessa per tutte le richieste nel pool di risorse, in caso di contesa di CPU. *valore* è un intero con valore predefinito è 0. L'intervallo consentito per *valore* è compreso tra 0 e 100.  
  
 MAX_CPU_PERCENT =*value*  
 Specifica la larghezza di banda media massima della CPU concessa per tutte le richieste nel pool di risorse in caso di contesa di CPU. *valore* è un intero con valore predefinito è pari a 100. L'intervallo consentito per *valore* è compreso tra 1 e 100.  
  
 Valore di CAP_CPU_PERCENT =*valore*  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il limite di utilizzo massimo della larghezza di banda della CPU concesso per tutte le richieste nel pool di risorse. Limita il livello massimo della larghezza di banda della CPU al valore specificato. *valore* è un intero con valore predefinito è pari a 100. L'intervallo consentito per *valore* è compreso tra 1 e 100.  
  
 AFFINITÀ {DELL'UTILITÀ DI PIANIFICAZIONE = AUTO | ( \<scheduler_range_spec >) | NUMANODE = (\<NUMA_node_range_spec >)} **si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Associa il pool di risorse a utilità di pianificazione specifiche. Il valore predefinito è AUTO.  
  
 AFFINITY SCHEDULER = **(** \<scheduler_range_spec > **)** esegue il mapping del pool di risorse per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pianificazioni identificate dagli ID specificati. Questi ID mapping ai valori nella colonna scheduler_id [Sys.dm os_schedulers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md). 
  
 Quando si utilizza AFFINITY NUMANODE = **(** \<NUMA_node_range_spec > **)**, il pool di risorse viene creata un'affinità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le utilità di pianificazione che eseguono il mapping alle CPU fisiche corrispondenti a il nodo NUMA specifico o un intervallo di nodi. È possibile utilizzare la seguente query [!INCLUDE[tsql](../../includes/tsql-md.md)] per individuare il mapping tra la configurazione NUMA fisica e gli ID delle utilità di pianificazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
  
```  
SELECT osn.memory_node_id AS [numa_node_id], sc.cpu_id, sc.scheduler_id  
FROM sys.dm_os_nodes AS osn  
INNER JOIN sys.dm_os_schedulers AS sc   
    ON osn.node_id = sc.parent_node_id   
    AND sc.scheduler_id < 1048576;  
```  
  
 MIN_MEMORY_PERCENT =*valore*  
 Specifica la quantità minima di memoria riservata al pool di risorse non condivisibile con altri pool di risorse. *valore* è un intero con un valore predefinito 0 nell'intervallo consentito per *valore* è compreso tra 0 e 100.  
  
 MAX_MEMORY_PERCENT =*valore*  
 Specifica la memoria totale del server utilizzabile dalle richieste in questo pool di risorse. *valore* è un intero con valore predefinito è pari a 100. L'intervallo consentito per *valore* è compreso tra 1 e 100.  
  
 MIN_IOPS_PER_VOLUME =*value*  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il numero minimo di operazioni di I/O al secondo per volume di disco da riservare per il pool di risorse. L'intervallo consentito per *valore* è compreso tra 0 e 2 ^ 31-1 (2.147.483.647). Specificare 0 per indicare che non è impostata alcuna soglia minima per il pool. Il valore predefinito è 0.  
  
 MAX_IOPS_PER_VOLUME =*value*  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il numero massimo di operazioni di I/O al secondo per volume di disco da riservare per il pool di risorse. L'intervallo consentito per *valore* è compreso tra 0 e 2 ^ 31-1 (2.147.483.647). Specificare 0 per impostare una soglia illimitata per il pool. Il valore predefinito è 0.  
  
 Se il valore MAX_IOPS_PER_VOLUME per un pool è impostato su 0, il pool non è governato e può accettare tutti gli IOPS nel sistema anche se in altri pool è stato impostato il valore MIN_IOPS_PER_VOLUME. In questo caso, è consigliabile impostare il valore MAX_IOPS_PER_VOLUME per questo pool su un numero elevato, ad esempio il valore massimo 2^31-1, se si desidera che questo pool sia governato per l'I/O.  
  
## <a name="remarks"></a>Osservazioni  
 MIN_IOPS_PER_VOLUME e MAX_IOPS_PER_VOLUME specificano il numero minimo e massimo di letture o scritture al secondo. Queste letture o scritture possono essere di qualsiasi dimensione e non indicano una velocità effettiva minima e massima.  
  
 I valori di MAX_CPU_PERCENT e MAX_MEMORY_PERCENT devono essere maggiori o uguali ai valori di MIN_CPU_PERCENT e MIN_MEMORY_PERCENT, rispettivamente.  
  
 CAP_CPU_PERCENT è diverso da MAX_CPU_PERCENT per il fatto che i carichi di lavoro associati al pool possono utilizzare una capacità della CPU superiore rispetto al valore di MAX_CPU_PERCENT, se disponibile, ma non superiore rispetto al valore di CAP_CPU_PERCENT.  
  
 La percentuale totale di CPU per ogni componente per il quale è impostata l'affinità (utilità di pianificazione o nodi NUMA) non deve superare il 100%.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come creare un pool di risorse denominato `bigPool`. Il pool utilizza le impostazioni predefinite di Resource Governor.  
  
```  
CREATE RESOURCE POOL bigPool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
 Nell'esempio seguente per `CAP_CPU_PERCENT` viene impostato un limite di utilizzo massimo pari al 30%, mentre per `AFFINITY SCHEDULER` viene impostato un intervallo compreso tra 0 e 63 e tra 128 e 191. 
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE RESOURCE POOL PoolAdmin  
WITH (  
     MIN_CPU_PERCENT = 10,  
     MAX_CPU_PERCENT = 20,  
     CAP_CPU_PERCENT = 30,  
     AFFINITY SCHEDULER = (0 TO 63, 128 TO 191),  
     MIN_MEMORY_PERCENT = 5,  
     MAX_MEMORY_PERCENT = 15  
      );  
  
```  
  
 L'esempio seguente imposta `MIN_IOPS_PER_VOLUME` a \<un valore > e `MAX_IOPS_PER_VOLUME` per \<un valore >. Questi valori determinano le operazioni di lettura e scrittura di I/O fisico disponibili per il pool di risorse.  
  
**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE RESOURCE POOL PoolAdmin  
WITH (  
    MIN_IOPS_PER_VOLUME = 20,  
    MAX_IOPS_PER_VOLUME = 100  
      );  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Creare un pool di risorse](../../relational-databases/resource-governor/create-a-resource-pool.md)  
  
  

