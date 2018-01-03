---
title: Gestione del carico di lavoro (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/12/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69063b1a-a8f3-453a-83ab-afbe7eb4f463
caps.latest.revision: "11"
ms.openlocfilehash: 738818a49491fbf8f8df491cac2f10ebdeedf3bf
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="workload-management"></a>Gestione del carico di lavoro
Funzionalità di gestione del SQL Server PDW carico di lavoro consentono agli utenti e agli amministratori di assegnare le richieste di pre-impostare le configurazioni di memoria e concorrenza. Gestione del carico di lavoro per migliorare le prestazioni del carico di lavoro, coerenza o mista, consentendo le richieste senza un'insufficienza delle risorse per tutte le richieste per le risorse appropriate.  
  
Ad esempio, con le tecniche di gestione del carico di lavoro in SQL Server PDW, è possibile:  
  
-   Allocare un numero elevato di risorse per un processo di caricamento.  
  
-   Specificare più risorse per la creazione di un indice columnstore.  
  
-   Risolvere i problemi relativi a un hash join esecuzione eccessivamente lento per verificare se è necessario maggiore quantità di memoria e quindi assegnare maggiore quantità di memoria.  
  
## <a name="Basics"></a>Nozioni fondamentali sulla gestione del carico di lavoro  
  
### <a name="key-terms"></a>Termini chiave  
Gestione del carico di lavoro  
*Gestione del carico di lavoro* è la possibilità di comprendere e regolare l'utilizzo delle risorse di sistema per ottenere prestazioni ottimali per le richieste simultanee.  
  
Classe di risorse  
In SQL Server PDW, un *classe di risorse* è un ruolo predefinito del server che dispone di limiti di pre-assegnati per la memoria e concorrenza. SQL Server PDW alloca le risorse per le richieste in base l'appartenenza al ruolo di risorsa classe server dell'account di accesso che invia le richieste.  
  
Nei nodi di calcolo, l'implementazione di classi di risorse utilizza la funzionalità Resource Governor in SQL Server. Per ulteriori informazioni su Resource Governor, vedere [Resource Governor](http://msdn.microsoft.com/en-us/library/bb933866(v=sql.11).aspx) su MSDN.  
  
### <a name="understand-current-resource-utilization"></a>Comprendere l'utilizzo delle risorse correnti  
Per comprendere l'utilizzo delle risorse di sistema per le richieste attualmente in esecuzione, utilizzare le DMV di SQL Server PDW. Ad esempio, è possibile utilizzare viste a gestione dinamica per comprendere se un join hash di grandi dimensioni con esecuzione prolungata può trarre vantaggio dalla presenza di più memoria.  
  
<!-- MISSING LINKS
For examples, see [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md).  
-->
  
### <a name="adjust-resource-allocations"></a>Modificare le allocazioni di risorse  
Per modificare l'utilizzo delle risorse, modificare l'appartenenza di classe di risorse dell'account di accesso che invia la richiesta. I ruoli del server di classe di risorse sono denominati **mediumrc**, **largerc**, e **xlargerc**. Rappresentano rispettivamente allocazioni Media, grande e molto grande.  
  
Ad esempio, per allocare una grande quantità di risorse di sistema per una richiesta, aggiungere l'account di accesso è l'invio della richiesta per il **largerc** ruolo del server. L'istruzione ALTER SERVER ROLE seguente aggiunge l'account di accesso Anna al ruolo del server largerc.  
  
```sql  
ALTER SERVER ROLE largerc ADD MEMBER Anna;  
```  
  
## <a name="RC"></a>Delle descrizioni classe di risorse  
Nella tabella seguente descrive le classi di risorse e le assegnazioni di risorse di sistema.  
  
|Classe di risorse|Priorità richiesta|Utilizzo della memoria massima *|Gli slot di concorrenza (massimo = 32)|Description|  
|------------------|----------------------|--------------------------|---------------------------------------|---------------|  
|predefiniti|Media|400 MB|1|Per impostazione predefinita, ogni account di accesso è consentita una piccola quantità di memoria e risorse di concorrenza per le richieste.<br /><br />Quando un account di accesso viene aggiunto a una classe di risorse, la nuova classe ha la precedenza. Quando un account di accesso viene eliminato da tutte le classi di risorse, l'account di accesso, vengono ripristinate l'allocazione di risorse predefinito.|  
|MediumRC|Media|1200 MB|3|Esempi di richieste che potrebbero essere la classe di risorse di supporto:<br /><br />Le operazioni di un'istruzione CTAS che dispongono di grandi dimensioni hash join.<br /><br />Selezionare le operazioni che richiedono più memoria per evitare la memorizzazione nella cache su disco.<br /><br />Il caricamento dei dati negli indici columnstore cluster.<br /><br />Compilazione, ricompilazione e la riorganizzazione degli indici columnstore cluster per le tabelle di dimensioni minori che hanno 10-15 colonne.|  
|largerc|Alto|2.8 GB|7|Esempi di richieste che potrebbero essere la classe di risorse di grandi dimensioni:<br /><br />Operazioni di un'istruzione CTAS grandi enorme hash join, o contengono aggregazioni di grandi dimensioni, ad esempio di grandi dimensioni clausole ORDER BY o GROUP BY.<br /><br />Selezionare le operazioni che richiedono grandi quantità di memoria per operazioni quali hash join o aggregazioni, ad esempio le clausole ORDER BY o GROUP BY<br /><br />Il caricamento dei dati negli indici columnstore cluster.<br /><br />Compilazione, ricompilazione e la riorganizzazione degli indici columnstore cluster per le tabelle di dimensioni minori che hanno 10-15 colonne.|  
|xlargerc|Alto|8.4 GB|22|La classe di risorse molto grande è per le richieste che potrebbero richiedere l'utilizzo di risorse molto grandi in fase di esecuzione.|  
  
<sup>*</sup>Utilizzo massimo della memoria è un'approssimazione.  
  
### <a name="request-importance"></a>Priorità richiesta  
Esegue il mapping alla quantità di tempo della CPU che consenta alle richieste di SQL Server, in esecuzione nei nodi di calcolo, l'importanza della richiesta.  Le richieste con priorità più alta ricevono più tempo della CPU.  
  
### <a name="maximum-memory-usage"></a>Utilizzo massimo della memoria  
Utilizzo massimo della memoria è la quantità massima di memoria disponibile che può essere utilizzata una richiesta all'interno di ogni spazio di elaborazione. Ad esempio una richiesta di mediumrc può utilizzare fino a 1200 MB per l'elaborazione all'interno di ogni distribuzione. È comunque importante garantire dati non è appropriati per evitare che alcune distribuzioni eseguendo la maggior parte del lavoro.  
  
### <a name="concurrency-slots"></a>Slot di concorrenza  
L'obiettivo di allocazione a 1, 3, 7 e slot concorrenza 22 è consentire di eseguire contemporaneamente, senza bloccare il processo di piccole dimensioni quando è in esecuzione un processo di grandi dimensioni i processi di piccoli e grandi dimensioni.  Ad esempio, SQL Server PDW può allocare massimo di 32 slot di concorrenza per l'esecuzione 1 richiesta di dimensioni molto grande (22 slot), 1 richiesta di grandi dimensioni (7 slot) e 1 medio richiesta (3 slot) nello stesso momento.  
  
Esempi di allocare un massimo di 32 slot di concorrenza di richieste simultanee:  
  
-   gli 28 slot = 4 di grandi dimensioni  
  
-   gli 30 slot = 10 medium  
  
-   gli 32 slot = 32 predefinito  
  
-   gli 32 slot = molto grandi di 1 + 1-medio di grandi dimensioni + 1  
  
-   gli 32 slot = 2-medio di grandi dimensioni + 4 + 6 predefinito  
  
Si supponga che le richieste di grandi dimensioni 6 vengono inviate a SQL Server PDW, e quindi non vengono inviate richieste predefinito 10. SQL Server PDW elaborerà le richieste in ordine di priorità come indicato di seguito:  
  
-   Allocare gli slot di concorrenza 28 per avviare l'elaborazione delle richieste di grandi dimensioni 4 come memoria diventa disponibile e mantenere 2 richieste di grandi dimensioni nella coda.  
  
-   Allocare 4 slot di concorrenza per avviare l'elaborazione delle richieste predefinito 4 e mantenere le richieste predefinito 6 nella coda di attesa.  
  
Come completare le richieste e diventano disponibili slot di concorrenza, pwd di SQL Server allocherà le richieste rimanenti in base alla priorità e le risorse disponibili. Ad esempio, quando sono presenti concorrenza 7 aprire slot, in attesa di richieste di grandi dimensioni verrà avranno la priorità per gli 7 slot più in attesa di richieste di medie dimensioni.  Se si apre 6 slot, SQL Server PDW allocherà 6 dimensioni predefinite più richieste. Tuttavia, gli slot di memoria e concorrenza devono essere tutti disponibili prima di SQL Server PDW consente a una richiesta per l'esecuzione.  
  
All'interno di ogni classe di risorse, le richieste di esecuzione in first-in first-out (FIFO) ordine.  
  
## <a name="GeneralRemarks"></a>Osservazioni generali  
Se un account di accesso è un membro di più di una classe di risorse, la classe con la maggior parte delle risorse ha la precedenza.  
  
Quando un account di accesso viene aggiunto o eliminato da una classe di risorse, la modifica diventa effettiva immediatamente per tutte le richieste successive; richieste correnti che sono in esecuzione o in attesa non sono interessate. L'account di accesso non è necessario disconnettersi e riconnettersi affinché avvenga la modifica.  
  
Per ogni account di accesso, le impostazioni di classe di risorse vengono applicate alle operazioni e le singole istruzioni e non alla sessione.  
  
Prima di SQL Server PDW esegue un'istruzione, tenta di acquisire gli slot di concorrenza necessari per la richiesta. Se Impossibile acquisire sufficiente slot di concorrenza, SQL Server PDW Sposta la richiesta in uno stato di attesa di esecuzione. Tutte le risorse di sistema che sono stati già allocato alla richiesta vengono restituiti al sistema.  
  
La maggior parte delle istruzioni SQL è necessario sempre le allocazioni di risorse predefinito e pertanto non sono controllata da classi di risorse. Ad esempio, CREATE LOGIN solo una piccola quantità di risorse è necessario e viene allocato le risorse predefinite, anche se la chiamata di creazione di account di accesso dell'account di accesso è un membro di una classe di risorse.  Se, ad esempio, Anna è un membro della classe di risorse largerc e invia un'istruzione CREATE LOGIN, l'istruzione CREATE LOGIN eseguirà con il numero di risorse predefinito.  
  
Istruzioni SQL e operazioni di classi di risorse:  
  
-   ALTER INDEX REBUILD  
  
-   ALTER INDEX REORGANIZE  
  
-   MODIFICA TABELLA RICOMPILAZIONE  
  
-   CREARE UN INDICE CLUSTER  
  
-   CREATE CLUSTERED COLUMNSTORE INDEX  
  
-   CREATE TABLE AS SELECT  
  
-   CREATE REMOTE TABLE AS SELECT  
  
-   Il caricamento dei dati con **dwloader**.  
  
-   COMANDI INSERT SELECT  
  
-   UPDATE  
  
-   Elimina  
  
-   RESTORE DATABASE durante il ripristino in un dispositivo con più nodi di calcolo.  
  
-   Selezionare, escluse le query DMV sola  
  
## <a name="Limits"></a>Limitazioni e restrizioni  
Le classi di risorse determinano le allocazioni di memoria e concorrenza.  Non controllano le operazioni di input/output.  
  
## <a name="Metadata"></a>Metadati  
Viste a gestione dinamica che contengono informazioni sulle classi di risorse e i membri di classe di risorse.  
  
-   [sys.server_role_members](../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
-   [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
Viste a gestione dinamica che contengono informazioni sullo stato delle richieste e le risorse che richiedono:  
  
-   [sys.dm_pdw_lock_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
-   [sys.dm_pdw_resource_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
Viste di sistema correlate esposte dalle DMV SQL Server nei nodi di calcolo. Vedere [viste a gestione dinamica SQL Server](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) per collegamenti a queste DMV su MSDN.  
  
-   Sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   Sys.dm_pdw_nodes_resource_governor_workload_groups  
  
-   Sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   Sys.dm_pdw_nodws_resource_governor_workload_groups  
  
-   Sys.dm_pdw_nodes_exec_sessions  
  
-   Sys.dm_pdw_nodes_exec_requests  
  
-   Sys.dm_pdw_nodes_exec_query_memory_grants  
  
-   Sys.dm_pdw_nodes_exec_query_resource_semaphores  
  
-   Sys.dm_pdw_nodes_os_memory_brokers  
  
-   Sys.dm_pdw_nodes_os_memory_cache_entries  
  
-   Sys.dm_pdw_nodes_exec_cached_plans  
  
## <a name="RelatedTasks"></a>Attività correlate  
[Attività di gestione del carico di lavoro](workload-management-tasks.md)  
  
<!-- MISSING LINKS
See the Workload Management section of [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md) for the following tasks:  
  
1.  Find the number of active requests for each resource group.  
  
2.  Determine if my requests need more memory  
  
3.  Determine if there are a high number of query optimizations or suboptimal plan generations.  
  
4.  Determine Average CPU time per request in each resource pool to date  
  
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
