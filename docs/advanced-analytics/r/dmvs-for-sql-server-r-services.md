---
title: Viste a gestione dati (DMV) per SQL Server di Machine Learning servizi | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e2180794ca96fc6387105745e346802725afe1dd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dmvs-for-sql-server-machine-learning-services"></a>Viste a gestione dinamica per servizi SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'articolo elenca le viste del catalogo di sistema e viste a gestione dinamica correlate a apprendimento in SQL Server.

Per informazioni sugli eventi estesi, vedere [eventi per machine learning estesi](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md).

> [!TIP]
> Utilizzare i report predefiniti per le sessioni di apprendimento di monitoraggio e l'utilizzo di pacchetto. Per ulteriori informazioni, vedere [monitorare machine learning che usano report personalizzati in Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="system-configuration-and-system-resources"></a>Configurazione di sistema e le risorse di sistema

È possibile monitorare e analizzare le risorse usate da script esterno utilizzando [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] DMV e viste del catalogo di sistema.

+ [ sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)

  Restituisce informazioni relative alle connessioni utente e alle sessioni di sistema. È possibile identificare le sessioni di sistema esaminando la colonna *session_id*. I valori superiori o uguali a 51 corrispondono a connessioni utente e i valori inferiori a 51 a processi di sistema.

+ [sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)

  Restituisce una riga per ogni contatore delle prestazioni di sistema usato dal server.  È possibile usare queste informazioni per visualizzare quanti script sono stati eseguiti, quali script sono stati eseguiti usando una determinata modalità di autenticazione o quante chiamate R sono state effettuate nell'istanza complessivamente.

  Questo esempio ottiene solo i contatori relativi a uno script R:

  ```SQL
  SELECT * from sys.dm_os_performance_counters WHERE object_name LIKE '%External Scripts%'
  ```

  I contatori seguenti vengono segnalati da questa vista DMV per gli script esterni per ogni istanza:

  + **Totale di esecuzioni**: numero di processi esterni avviate dalle chiamate locali o remote
  + **Le esecuzioni parallele**: numero di volte in cui è incluso uno script la _@parallel_ specifica e che [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] è stato in grado di generare e utilizzare un piano di query parallele
  + **Streaming esecuzioni**: numero di volte in cui è stata richiamata la funzionalità di flusso
  + **SQL CC esecuzioni**: numero di external script fase in cui la chiamata è stata creata un'istanza in modalità remota e SQL Server è stato usato come contesto di calcolo
  + **Accessi tramite autenticazione implicita**: numero di volte in cui è stata effettuata una chiamata di loopback ODBC usando l'autenticazione implicita, vale a dire che [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ha eseguito la chiamata per conto dell'utente inviando la richiesta di script.
  + **Tempo totale di esecuzione (ms)**: tempo trascorso tra la chiamata e il completamento della chiamata
  + **Errori di esecuzione**: numero di volte in cui gli script hanno segnalato errori. Questo conteggio non include gli errori R.


+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)

  Questa vista DMV segnala una sola riga per ogni account di lavoro che esegue attualmente uno script esterno. Si noti che questo account di lavoro è diverso dalle credenziali della persona che invia lo script. Se un solo utente di Windows invia più richieste di script, verrà assegnato un solo account di lavoro per gestire tutte le richieste di tale utente. Se un utente di Windows diverso accede per eseguire uno script esterno, la richiesta verrà gestita da un account di lavoro separato.

  Questa vista DMV non restituisce risultati se nessuno script è attualmente in esecuzione, quindi è molto utile per monitorare gli script con esecuzione prolungata. Restituisce questi valori:

  + **external_script_request_id**: un GUID, che viene usato anche come il nome temporaneo della directory di lavoro utilizzato per archiviare gli script e i risultati intermedi
  + **linguaggio**: un valore, ad esempio `R` che denota la lingua dello script esterno
  + **degree_of_parallelism**: un numero intero che indica il numero di parallelo processi che sono stati utilizzati
  + **external_user_name**: finestra di avvio di un ruolo di lavoro dell'account, ad esempio **SQLRUser01**

+ [sys.dm_external_script_execution_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)

  Questa DMV viene fornita per il monitoraggio interno (telemetria) tenere traccia delle chiamate di script esterni quanti vengono eseguite su un'istanza. Il servizio telemetria ha inizio quando [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e incrementa un contatore basate su disco ogni volta che viene chiamato una specifica funzione di machine learning.

  Il contatore viene incrementato per ogni chiamata a una funzione di rilevamento specifica. Ad esempio, se `rxLinMod` viene chiamato ed eseguito in parallelo, il contatore viene incrementato di 1.
  
  In generale, i contatori delle prestazioni sono validi solo se il processo che li ha generati è attivo. Quindi, una query su una DMV non può visualizzare i dati dettagliati per i servizi che non sono in esecuzione. Se ad esempio Launchpad crea più processi R paralleli che vengono eseguiti molto velocemente e quindi puliti dall'oggetto processo di Windows, è possibile che una vista DMV non visualizzi alcun dato.
 
  I contatori rilevati da questa DMV restano tuttavia in esecuzione e lo stato del contatore dm_external_script_execution viene mantenuto usando le scritture su disco, anche se l'istanza è arrestata.
 
 Per altre informazioni sui contatori delle prestazioni di sistema usati da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], vedere [Usare oggetti di SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).

## <a name="resource-governor-views"></a>Viste di Resource Governor

Nelle edizioni che supportano Resource Governor, creazione di pool di risorse esterne per carichi di lavoro R o Python può essere efficace en per tenere traccia e gestire le risorse.

+ [sys.resource_governor_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)

  Restituisce le informazioni sullo stato del pool di risorse corrente, la configurazione del pool di risorse corrente e le statistiche del pool di risorse.

  > [!IMPORTANT]
  > 
  > È necessario modificare i pool di risorse che si applicano ad altri servizi del server prima di poter allocare risorse aggiuntive a R Services.

+ [sys.resource_governor_external_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)

  Una nuova vista del catalogo che visualizza i valori di configurazione correnti per i pool di risorse esterni.
  In Enterprise Edition è possibile configurare pool di risorse esterni aggiuntivi: si potrebbe decidere, ad esempio, di gestire le risorse per i processi R in esecuzione in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] separatamente da quelle originate da un client remoto.

  > [!NOTE]
  > 
  > Nell'edizione Standard, tutti i processi di script esterni eseguire nel pool di risorse esterno predefinito stesso.

+ [sys.resource_governor_workload_groups](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)

  Restituisce le statistiche del gruppo del carico di lavoro e la configurazione corrente del gruppo del carico di lavoro. Questa vista può essere unita a `sys.dm_resource_governor_resource_pools` per ottenere il nome del pool di risorse.
  Per gli script esterni, è stata aggiunta una nuova colonna in cui è visualizzato l'ID del pool esterno associato al gruppo di carico di lavoro.

+ [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)

  Una nuova vista del catalogo di sistema che consente di visualizzare i processori e le risorse per i quali è impostata l'affinità con un determinato pool di risorse.

  Restituisce una riga per utilità di pianificazione in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], dove è stato eseguito il mapping di ogni utilità di pianificazione a un singolo processore. Utilizzare questa vista per eseguire il monitoraggio delle condizioni di un'utilità di pianificazione oppure per identificare eventuali attività sfuggite al controllo.

  Con la configurazione predefinita, i pool di carichi di lavoro vengono automaticamente assegnati ai processori e quindi non sono presenti valori di affinità da restituire.

  La pianificazione dell'affinità esegue il mapping del pool di risorse alle pianificazioni di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] identificate dagli ID specificati. Questi ID eseguire il mapping ai valori di `scheduler_id` colonna `sys.dm_os_schedulers`.


> [!NOTE] 
> 
> Anche se è possibile configurare e personalizzare pool di risorse solo nelle edizioni Enterprise e Developer, i pool predefiniti e le viste DMV sono disponibili in tutte le edizioni. Pertanto, è possibile utilizzare queste DMV in Standard Edition per determinare l'estremità di risorse per i processi di script esterni.

Per informazioni generali sul monitoraggio delle istanze di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], vedere [Viste del catalogo di sistema](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) e [Resource Governor Related Dynamic Management Views](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md) (Viste a gestione dinamica (DMV) correlate a Resource Governor).

## <a name="monitoring-script-execution"></a>L'esecuzione dello script di monitoraggio

Script R e Python da eseguire nel [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] vengono avviati mediante il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] interfaccia. Launchpad non viene tuttavia gestito a livello di risorse né monitorato separatamente, perché si presuppone che sia un servizio sicuro fornito da Microsoft che gestisce le risorse correttamente.

Singoli script eseguiti con il servizio Launchpad vengono gestiti mediante il [oggetto processo di Windows](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx). Un oggetto processo consente di gestire gruppi di processi come unità. Ogni oggetto processo è gerarchico e controlla gli attributi di tutti i processi associati a esso. Le operazioni eseguite su un oggetto processo interessano tutti i processi associati all'oggetto processo.

Se quindi è necessario terminare un processo associato a un oggetto, tenere presente che verranno terminati anche tutti i processi correlati. Se si esegue uno script R assegnato a un oggetto processo di Windows e tale script esegue un processo ODBC correlato che deve essere terminato, verrà terminato anche il processo di script R padre.

Se si avvia uno script esterno che utilizza l'elaborazione parallela, un singolo oggetto processo Windows gestisce tutti i processi figlio parallelo.

Per determinare se un processo è in esecuzione in un processo, usare la funzione `IsProcessInJob`.

## <a name="next-steps"></a>Passaggi successivi

[Gestione e monitoraggio delle soluzioni di apprendimento automatico](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
