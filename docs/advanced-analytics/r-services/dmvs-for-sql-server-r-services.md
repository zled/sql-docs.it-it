---
title: "Viste a gestione dinamica per i servizi SQL Server R | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3643ea0-d9f3-463f-8ece-572127f32a24
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Viste a gestione dinamica per i servizi SQL Server R

L'argomento sono elencate le viste del catalogo di sistema e viste a gestione dinamica correlate a [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. 


Per informazioni sugli eventi estesi, vedere [eventi estesi per i servizi di SQL Server R](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md).

> [!TIP]
> Il team del prodotto ha fornito i report personalizzati che è possibile utilizzare per monitorare pacchetti e sessioni di servizi di R. Per ulteriori informazioni vedere [R monitorare i servizi tramite i report personalizzati in Management Studio](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md).
> 

## <a name="system-configuration-and-system-resources"></a>Configurazione del sistema e risorse di sistema

È possibile monitorare e analizzare le risorse utilizzate dagli script R di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] viste del catalogo di sistema e viste a gestione dinamica.


**Generale**
+ [ DM exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)

  Restituisce informazioni relative alle connessioni utente e le sessioni di sistema. È possibile identificare le sessioni di sistema esaminando il *session_id* colonna; i valori maggiori di o uguale a 51 sono connessioni utente e i valori inferiori 51 sono i processi di sistema. 



+ [DM os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)

  Restituisce una riga per ogni contatore delle prestazioni di sistema utilizzata dal server.  È possibile utilizzare queste informazioni per vedere quanti gli script eseguiti, sono stati eseguiti gli script che utilizza la modalità di autenticazione o il numero delle chiamate R sono stato rilasciato nell'istanza globale.

  Questo esempio si ottiene solo i contatori relativi a script R:

  ```SQL
  SELECT * from sys.dm_os_performance_counters WHERE object_name LIKE '%Extended Scripts%'
  ```

  I contatori seguenti vengono restituiti da questa DMV per gli script esterni per ogni istanza:

  + **Totale esecuzioni**: numero di processi R tramite chiamate locali o remote
  + **Esecuzioni in parallelo**: numero di volte in cui è incluso uno script di @parallel specifica e che [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] è stato in grado di generare e utilizzare un piano di query parallele
  + **Streaming esecuzioni**: numero di volte in cui la funzionalità di flusso è stata richiamata. 
  + **Esecuzioni CC SQL**: numero di R script eseguiti in cui la chiamata è stata creata un'istanza in modalità remota e SQL Server utilizzato come contesto di calcolo 
  + **Autenticazione implicita. Gli account di accesso**: numero di volte in cui è stata effettuata una chiamata di loopback ODBC tramite cui è inclusa l'autenticazione, vale a dire, la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] l'esecuzione della chiamata per conto dell'utente invia la richiesta di script
  + **Tempo totale di esecuzione (ms)**: tempo trascorso tra la chiamata e il completamento della chiamata.
  + **Gli errori di esecuzione**: numero di volte in cui gli script sono verificati errori. Questo conteggio include errori R.


+ [Sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)

  Questa DMV restituisce una riga per ogni account di lavoro attualmente in esecuzione uno script esterno. Si noti che questo account di lavoro diverso dalle credenziali dell'utente l'invio dello script. Se un singolo utente di Windows invia più richieste di script, vengono assegnati account solo un ruolo di lavoro per gestire tutte le richieste da tale utente. Se un utente Windows diverso accede a eseguire uno script esterno, la richiesta sarebbe gestita da un account di lavoro distinto. 
  Questa DMV non restituirà alcun risultato se gli script non sono attualmente in esecuzione; Pertanto, è particolarmente utile per gli script con esecuzione prolungata di monitoraggio. Restituisce valori sono i seguenti:
  + **external_script_request_id**: un GUID, che viene utilizzato anche come il nome temporaneo della directory di lavoro utilizzata per archiviare gli script e i risultati intermedi.  
  + **lingua**: un valore come `R` che indica la lingua dello script esterno.
  + **degree_of_parallelism**: intero che indica il numero di parallelo processi che sono stati utilizzati. 
  + **external_user_name**: un account di lavoro di avvio, ad esempio SQLRUser01. 
  

+ [Sys.dm_external_script_execution_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)

  Questa DMV viene fornita per il monitoraggio interno (dati di telemetria) tenere traccia di quante R chiamate vengono eseguite su un'istanza. Il servizio dati di telemetria inizia quando [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e viene incrementato un contatore basata su disco ogni volta che viene chiamata una funzione R specifica.

  Il contatore viene incrementato per ogni chiamata a una funzione. Ad esempio, se `rxLinMod` viene chiamato ed eseguito in parallelo, il contatore viene incrementato di 1.
  
  In generale, i contatori delle prestazioni sono validi solo se il processo che li ha generati è attivo. Quindi, una query su una DMV non può visualizzare i dati dettagliati per i servizi che non sono in esecuzione. Ad esempio, se la finestra di avvio consente di creare più processi R paralleli e ancora vengono eseguite molto rapidamente e pulizia per l'oggetto processo Windows, è possibile che una DMV non mostri tutti i dati.
 
  Tuttavia, i contatori rilevati da questa DMV sono mantenuti in esecuzione e stato per dm_external_script _execution contatore viene mantenuto utilizzando scritture su disco, anche se l'istanza è stato arrestato.
 
 Per ulteriori informazioni sui contatori delle prestazioni di sistema utilizzato da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], vedere [utilizzare oggetti di SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).

**Viste di Resource Governor**

+ [resource_governor_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)

  Restituisce le informazioni sullo stato del pool di risorse corrente, la configurazione del pool di risorse corrente e le statistiche del pool di risorse.

  > [!IMPORTANT]
  > 
  > È necessario modificare i pool di risorse che si applicano ad altri servizi server prima di allocare risorse aggiuntive per i servizi di R.


+ [Sys.resource_governor_external_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)

  Una nuova vista del catalogo che mostra i valori di configurazione correnti per i pool di risorse esterno.
  In Enterprise Edition, è possibile configurare i pool di risorse esterne aggiuntive: ad esempio, è possibile gestire le risorse per i processi in esecuzione in R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] separatamente da quelli che provengono da un client remoto. 

  > [!NOTE]
  > 
  > Nell'edizione Standard vengono eseguiti tutti i processi R nello stesso pool di risorse predefinito esterno.

+ [resource_governor_workload_groups](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)

  Restituisce statistiche del gruppo del carico di lavoro e la configurazione corrente del gruppo di carico di lavoro. Questa vista può essere unita a sys.dm_resource_governor_resource_pools per ottenere il nome del pool di risorse.
  Per gli script esterni, è stata aggiunta una nuova colonna che mostra l'id del pool di esterni associati al gruppo di carico di lavoro. 


+ [Sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)

  Una nuova vista di catalogo di sistema che consente di visualizzare i processori e risorse che vengono creata un'affinità per un pool di risorse specifico.

  Restituisce una riga per utilità di pianificazione in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], dove è stato eseguito il mapping di ogni utilità di pianificazione a un singolo processore. Utilizzare questa vista per eseguire il monitoraggio delle condizioni di un'utilità di pianificazione oppure per identificare eventuali attività sfuggite al controllo.

  Nella configurazione predefinita, i pool di carico di lavoro vengono assegnati automaticamente a processori e pertanto non sono presenti valori di affinità per restituire.

  La pianificazione di affinità associa il pool di risorse di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] pianificazioni identificate dagli ID specificati. Questi ID mapping ai valori nella colonna scheduler_id DM os_schedulers (Transact-SQL).


> [!NOTE] 
> 
> Sebbene la possibilità di configurare e personalizzare i pool di risorse è disponibile solo in Enterprise Edition e Developer Edition, pool predefiniti, nonché le DMV sono disponibili in tutte le edizioni. Pertanto, è possibile utilizzare queste DMV in Standard Edition per determinare i limiti di risorse per i processi R. 

Per informazioni generali sul monitoraggio [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanze, vedere [viste del catalogo](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) e [Resource Governor correlati viste a gestione dinamica](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="r-script-execution-and-monitoring"></a>Monitoraggio e l'esecuzione dello Script R

R script eseguiti in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] vengono avviati per la [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] interfaccia. Tuttavia, la finestra di avvio non è risorsa disciplinato o monitorata separatamente, come si presuppone che un servizio protetto fornito da Microsoft che gestisce le risorse in modo appropriato.

Singoli script R che eseguono il servizio di avvio vengono gestiti mediante il [oggetto processo Windows](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx). Un oggetto processo consente a gruppi di processi per essere gestiti come un'unità. Ogni oggetto processo gerarchica e controlla gli attributi di tutti i processi associati. Operazioni eseguite su un oggetto processo interessano tutti i processi associati all'oggetto processo. 

Pertanto, se è necessario terminare un processo associato all'oggetto, tenere presente che tutti i processi correlati inoltre verranno interrotte. Se si esegue uno script R che viene assegnato a un oggetto processo Windows e lo script esegue un processo ODBC correlato che deve essere terminato, nonché il processo di script R padre verrà terminato. 

Se si avvia uno script R che utilizza l'elaborazione parallela, un singolo oggetto processo Windows gestisce tutti i processi figlio paralleli.

Per determinare se un processo viene eseguito in un processo, utilizzare il `IsProcessInJob` (funzione).

## <a name="see-also"></a>Vedere anche
[La gestione e monitoraggio](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)

