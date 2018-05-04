---
title: L'ottimizzazione automatica | Documenti Microsoft
description: Informazioni sull'ottimizzazione automatica in SQL Server e Database SQL di Azure
ms.custom: ''
ms.date: 08/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: automatic-tuning
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- performance tuning [SQL Server]
ms.assetid: ''
caps.latest.revision: ''
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 5139bbadbc83b1046d6c03dd54b556173dd9ea6f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="automatic-tuning"></a>Ottimizzazione automatica
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  L'ottimizzazione automatica è una funzionalità di database che offre informazioni su potenziali problemi di prestazioni delle query, suggerisce soluzioni e corregge automaticamente i problemi rilevati.

L'ottimizzazione automatica [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] invia una notifica ogni volta che viene rilevato un potenziale problema di prestazioni e consente di applicare azioni correttive o consente il [!INCLUDE[ssde_md](../../includes/ssde_md.md)] risolvere automaticamente i problemi di prestazioni.
L'ottimizzazione automatica [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] consente di identificare e risolvere i problemi di prestazioni causati da **regressioni nella scelta del piano SQL**. L'ottimizzazione automatica [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] crea indici necessari e vengono eliminati gli indici inutilizzati.

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] Consente di monitorare le query che vengono eseguite sul database e automaticamente migliora le prestazioni del carico di lavoro. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] dispone di un meccanismo di intelligence predefinite che è possibile ottimizzare e migliorare le prestazioni delle query da adattare dinamicamente il database per il carico di lavoro automaticamente. Esistono due funzionalità di ottimizzazione automatica che sono disponibili:

 -  **Correzione automatica piano** (disponibile in [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] e [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]) che identifica i piani di esecuzione di query problematiche e correzioni SQL prevede i problemi di prestazioni.
 -  **La gestione automatica degli indici** (disponibile solo in [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]) che identifica gli indici che devono essere aggiunti al database e gli indici che devono essere rimossi.

## <a name="why-automatic-tuning"></a>Perché l'ottimizzazione automatica?

Una delle attività principali in Amministrazione classica di database esegue il monitoraggio del carico di lavoro, identificazione critico [!INCLUDE[tsql_md](../../includes/tsql_md.md)] esegue una query, gli indici devono essere aggiunti per migliorare le prestazioni di indici utilizzato di rado. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] fornisce informazioni dettagliate sulla query e gli indici che è necessario monitorare. Tuttavia, costantemente il monitoraggio del database è un'attività difficile e noiosa, soprattutto quando si gestiscono molti database. Gestisce un numero elevato di database potrebbero essere impossibili da eseguire in modo efficiente. Invece di monitoraggio e ottimizzazione del database manualmente, è possibile delegare alcuni del monitoraggio e ottimizzazione azioni [!INCLUDE[ssde_md](../../includes/ssde_md.md)] utilizzando le funzionalità di ottimizzazione automatica.

### <a name="how-does-automatic-tuning-works"></a>Qual è works ottimizzazione automatica?

L'ottimizzazione automatica è un monitoraggio continuo e il processo di analisi che rileva costantemente le caratteristiche del carico di lavoro e identificare potenziali problemi e miglioramenti.

![Processo di ottimizzazione automatica](./media/tuning-process.png)

Questo processo consente di adattare dinamicamente il carico di lavoro mediante la ricerca, quali indici e i piani potrebbero migliorare le prestazioni dei carichi di lavoro e gli indici di influire sui carichi di lavoro database. In base a questi risultati, l'ottimizzazione automatica applica le azioni di ottimizzazione che consentono di migliorare le prestazioni del carico di lavoro. Inoltre, i database monitora costantemente prestazioni dopo qualsiasi modifica apportata dall'ottimizzazione automatica per garantire che è possibile migliorare le prestazioni del carico di lavoro. Qualsiasi azione che non consentono di migliorare le prestazioni è automaticamente annullata. Il processo di verifica è una funzionalità chiave che assicura che qualsiasi modifica apportata dall'ottimizzazione automatica non diminuisca le prestazioni del carico di lavoro.

## <a name="automatic-plan-correction"></a>Correzione automatica di piano

Correzione automatica di piano è una funzionalità di ottimizzazione automatica che identifica **di regressione nella scelta di piani SQL** e risolvere automaticamente il problema, forzando l'ultimo piano valido noto.

### <a name="what-is-sql-plan-choice-regression"></a>Che cos'è regressione nella scelta del piano SQL?

[!INCLUDE[ssdenoversion_md](../../includes/ssdenoversion_md.md)] può utilizzare i diversi piani SQL per eseguire il [!INCLUDE[tsql_md](../../includes/tsql_md.md)] query. I piani di query dipendono da altri fattori, indici e le statistiche. Il piano ottimale che deve essere utilizzato per eseguire alcune [!INCLUDE[tsql_md](../../includes/tsql_md.md)] query potrebbero essere modificate nel corso del tempo. In alcuni casi, il nuovo piano potrebbe non essere migliore rispetto a quello precedente e il nuovo piano potrebbe causare una regressione delle prestazioni.

 ![Regressione nella scelta del piano SQL](media/plan-choice-regression.png "regressione nella scelta del piano SQL") 

Ogni volta che si nota che la regressione nella scelta del piano, è necessario trovare alcuni validi precedenti, piano e forza anziché corrente utilizzando uno `sp_query_store_force_plan` stored procedure.
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] in [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] fornisce informazioni sulle regredite piani e le azioni correttive consigliate.
Inoltre, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] consente di automatizzare il processo completamente e consentire [!INCLUDE[ssde_md](../../includes/ssde_md.md)] correggere gli eventuali problemi riscontrati correlati alle modifiche di piano.

### <a name="automatic-plan-choice-correction"></a>Correzione scelta del piano automatico

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] possono passare automaticamente per l'ultimo piano buona noto ogni volta che viene rilevata la regressione nella scelta del piano.

![Correzione scelta del piano SQL](media/force-last-good-plan.png "correzione scelta del piano SQL") 

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] rileva automaticamente qualsiasi potenziale regressione nella scelta del piano tra il piano che deve essere utilizzato anziché il piano non corretto.
Quando il [!INCLUDE[ssde_md](../../includes/ssde_md.md)] verrà applicata l'ultima noto del piano appropriato, automaticamente consente di monitorare le prestazioni del piano forzato. Se il piano forzato non è un vantaggio rispetto al piano regredito, il nuovo piano sarà unforced e [!INCLUDE[ssde_md](../../includes/ssde_md.md)] verrà compilato un nuovo piano. Se [!INCLUDE[ssde_md](../../includes/ssde_md.md)] verifica che il piano forzato è preferibile rispetto a quello regredita, il piano forzato verrà conservato fino a quando la ricompilazione (ad esempio, al prossimo cambio di statistiche o schema) se è preferibile rispetto al piano regredito.

Nota: Qualsiasi automaticamente piani forzato non si persit un riavvio dell'istanza di SQL Server.

### <a name="enabling-automatic-plan-choice-correction"></a>Abilitazione di correzione scelta del piano automatico

È possibile abilitare l'ottimizzazione automatica per ogni database e specificare che il miglior piano più recente deve essere forzato ogni volta in cui viene rilevata una regressione della modifica del piano. L'ottimizzazione automatica viene abilitata con il comando seguente:

```sql   
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON ); 
```
Una volta per attivare la questa opzione, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] verrà automaticamente forzare le raccomandazioni in cui il miglioramento della CPU stimato è superiore a 10 secondi o il numero di errori nel nuovo piano di è maggiore del numero di errori nel piano consigliato e verificare che il piano forzato è migliore di quella corrente.

### <a name="alternative---manual-plan-choice-correction"></a>Alternative: correzione di scelte di pianificazione manuale

Senza l'ottimizzazione automatica, gli utenti devono monitorare il sistema periodicamente e cercare le query regredite. Se qualsiasi piano regredite, utente dovrebbe trovare alcuni validi precedenti, piano e forza anziché corrente utilizzando uno `sp_query_store_force_plan` stored procedure. La procedura consigliata, è possibile forzare l'ultimo piano buona noto perché i piani precedenti potrebbero non essere validi a causa di modifiche di indice o statistica. L'utente che impone l'ultimo piano buona noto deve monitorare le prestazioni della query che viene eseguita utilizzando il piano forzato e verificare che tale piano forzato funziona come previsto. In base ai risultati dell'analisi e monitoraggio, è necessario forzare il piano o utente deve individuare un altro modo per ottimizzare la query.
I piani forzati manualmente è necessario non forzare sempre, poiché il [!INCLUDE[ssde_md](../../includes/ssde_md.md)] deve essere in grado di applicare piani ottimali. L'utente o amministratore di database deve infine annullar il piano utilizzando `sp_query_store_unforce_plan` procedura e lasciare il [!INCLUDE[ssde_md](../../includes/ssde_md.md)] trovare il piano ottimale.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce tutte le viste necessarie e le procedure necessarie per monitorare le prestazioni e risolvere i problemi nell'archivio Query.

In [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], è possibile trovare l'utilizzo delle viste di sistema di archivio Query regressioni nella scelta del piano. In [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)], il [!INCLUDE[ssde_md](../../includes/ssde_md.md)] rileva e vengono mostrati potenziali regressioni nella scelta del piano e le azioni consigliate che devono essere applicate nella [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) visualizzazione. La visualizzazione Mostra informazioni sul problema, l'importanza del problema e dettagli, ad esempio la query identificato, l'ID del piano di regredite, l'ID del piano a cui è stato utilizzato come linea di base per il confronto e [!INCLUDE[tsql_md](../../includes/tsql_md.md)] istruzione che può essere eseguito per correggere il esiste un problema.

| Tipo | description | datetime | score | dettagli | … |
| --- | --- | --- | --- | --- | --- |
| `FORCE_LAST_GOOD_PLAN` | Tempo di CPU, modificato da 4 ms a 14 ms | 3/17/2017 | 83 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |
| `FORCE_LAST_GOOD_PLAN` | Tempo di CPU, modificato da ms 37 a 84 ms | 3/16/2017 | 26 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |

Alcune colonne da questa visualizzazione sono descritti nell'elenco seguente:
 - Tipo di azione consigliata - `FORCE_LAST_GOOD_PLAN`.
 - Descrizione che contiene informazioni perché [!INCLUDE[ssde_md](../../includes/ssde_md.md)] ritiene che la modifica del piano è una regressione delle prestazioni potenziali.
 - Data e ora quando viene rilevata la regressione potenziali.
 - Assegnare un punteggio questa raccomandazione. 
 - Informazioni dettagliate sui problemi, ad esempio ID del piano rilevato, ID del piano regredito, ID del piano a cui deve essere forzato in modo per risolvere il problema, [!INCLUDE[tsql_md](../../includes/tsql_md.md)]
 script che potrebbe essere applicato per risolvere il problema e così via. I dettagli sono archiviati in [formato JSON](../../relational-databases/json/index.md).

Utilizzare la query seguente per ottenere uno script che corregge il problema e informazioni aggiuntive sulle stimato è possibile ottenere:

```sql   
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount+recommendedPlanExecutionCount)
                  *(regressedPlanCpuTimeAverage-recommendedPlanCpuTimeAverage)/1000000,
      error_prone = IIF(regressedPlanErrorCount>recommendedPlanErrorCount, 'YES','NO')
FROM sys.dm_db_tuning_recommendations
  CROSS APPLY OPENJSON (Details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            [current plan_id] int '$.regressedPlanId',
            [recommended plan_id] int '$.recommendedPlanId',

            regressedPlanErrorCount int,
            recommendedPlanErrorCount int,

            regressedPlanExecutionCount int,
            regressedPlanCpuTimeAverage float,
            recommendedPlanExecutionCount int,
            recommendedPlanCpuTimeAverage float

          ) as planForceDetails;
```

[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]     

| reason | score | script | query\_id | piano corrente\_id | piano consigliato\_id | stimato\_ottenere | errore\_soggetto
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Tempo di CPU, modificato da ms 3 a 46 ms | 36 | EXEC sp\_query\_archiviare\_forzare\_piano di 12, 17; | 12 | 28 | 17 | 11.59 | 0

`estimated_gain` rappresenta il numero stimato di secondi che verrebbero salvate se verrà eseguito il piano consigliato anziché il piano corrente. Se il miglioramento è maggiore di 10 secondi, è necessario forzare il piano consigliato anziché il piano corrente. Se sono presenti più errori (ad esempio, i timeout o interrotte esecuzioni) nel piano corrente di in consigliata prevede, la colonna `error_prone` verrebbe impostato sul valore `YES`. Piano soggetta a errore è motivo di un altro motivo per cui è necessario forzare il piano consigliato anziché quello corrente.

Sebbene [!INCLUDE[ssde_md](../../includes/ssde_md.md)] fornisce tutte le informazioni necessarie per identificare le regressioni nella scelta del piano; continua il monitoraggio e risoluzione dei problemi di prestazioni potrebbero essere un'operazione laboriosa. L'ottimizzazione automatica semplifica questo processo.

Nota: I dati in questa DMV non vengono mantenute dopo il riavvio dell'istanza di SQL Server.

## <a name="automatic-index-management"></a>Gestione automatica degli indici

In [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)], la gestione degli indici è semplice perché [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] riceve informazioni relative al carico di lavoro e assicura che i dati vengono indicizzati sempre in modo ottimale. Struttura di indice appropriato è fondamentale per ottenere prestazioni ottimali del carico di lavoro e la gestione automatica degli indici per ottimizzare gli indici. La gestione automatica degli indici possibile correggere i problemi di prestazioni nel database in modo non corretto indicizzati, o gestire e migliorare gli indici lo schema del database esistente. L'ottimizzazione automatica [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] esegue le azioni seguenti:

 - Identifica gli indici che potrebbe migliorare le prestazioni delle query T-SQL che leggono i dati dalle tabelle.
 - Identifica la ridondanza indici o che non sono stati utilizzati nel periodo di tempo che è possibile rimuovere. Rimozione di indici non necessari migliora le prestazioni delle query che aggiornano i dati nelle tabelle.

### <a name="why-do-you-need-index-management"></a>Motivo per cui occorre la gestione degli indici

Indici velocizzare alcune delle query che recuperano i dati dalle tabelle; Tuttavia, può rallentare le query di aggiornamento dei dati. È necessario analizzare attentamente quando creare un indice e le colonne che si desidera includere nell'indice. Alcuni indici potrebbero non essere necessario qualche minuto. Pertanto, è necessario periodicamente identificare ed eliminare gli indici che non portare i vantaggi. Se si ignorano gli indici inutilizzati, le prestazioni delle query di aggiornamento di dati sarebbero ridotto senza alcun vantaggio sulle query che recuperano i dati. Gli indici inutilizzati influire sulle prestazioni complessive del sistema perché altri aggiornamenti necessaria la registrazione non necessaria.

Ricerca del set ottimale di indici che consentono di migliorare le prestazioni delle query che può leggere i dati delle tabelle e hanno un impatto minimo per gli aggiornamenti, potrebbe essere necessario analysis continua e complessi.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] Usa intelligenti e regole avanzate che consentono di analizzare le query, identificare gli indici che sarebbero ottimali per i carichi di lavoro corrente e gli indici potrebbero essere rimossa. Database SQL di Azure consente di disporre di un set minimo necessario di indici che ottimizza le query che recuperano i dati, con un impatto ridotto a icona sul altre query.

### <a name="automatic-index-management"></a>Gestione automatica degli indici

Oltre a rilevamento, [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] possono applicare automaticamente i suggerimenti identificati. Se si ritiene che le regole predefinite di migliorare le prestazioni del database, è possibile consentire [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] gestire automaticamente gli indici.

Per abilitare l'ottimizzazione automatica nel Database di SQL Azure e gestire le funzionalità di ottimizzazione automatica completamente il carico di lavoro, vedere [abilitare la regolazione automatica nel Database di SQL Azure tramite il portale di Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-automatic-tuning-enable).

Quando il [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] si applica una raccomandazione CREATE INDEX o DROP INDEX, automaticamente consente di monitorare le prestazioni delle query che sono interessati dall'indice. Nuovo indice verrà mantenute solo se vengono migliorate le prestazioni delle query interessata. L'indice rimosso verrà ricreato automaticamente se sono presenti alcune query eseguite più lentamente a causa della mancanza di corrispondenza dell'indice.

### <a name="automatic-index-management-considerations"></a>Considerazioni sulla gestione automatica dell'indice

Le azioni necessarie per creare gli indici necessari [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] potrebbe utilizzare risorse e temporaneamente le prestazioni del carico di lavoro. Per ridurre al minimo l'impatto della creazione dell'indice sulle prestazioni del carico di lavoro, Database SQL di Azure consente di trovare l'intervallo di tempo appropriato per qualsiasi operazione di gestione dell'indice. Ottimizzazione di azione è posticipata se il database deve risorse per l'esecuzione del carico di lavoro e avviato durante il database disponga di sufficiente risorse inutilizzate che possono essere utilizzate per l'attività di manutenzione. Una funzionalità importante nella gestione automatica dell'indice è una verifica delle azioni. Quando il Database SQL di Azure crea o Elimina indice, un processo di monitoraggio consente di analizzare le prestazioni del carico di lavoro per verificare che l'azione migliorate le prestazioni. Se non introducono miglioramenti significativi: l'azione viene immediatamente ripristinato. In questo modo, il Database di SQL Azure garantisce che le azioni automatiche non influire negativamente sulle prestazioni del carico di lavoro. Gli indici creati tramite l'ottimizzazione automatica sono trasparenti per l'operazione di manutenzione per lo schema sottostante. Le modifiche dello schema, ad esempio l'eliminazione o ridenominazione delle colonne non sono bloccate dalla presenza di indici creati automaticamente. Gli indici che vengono creati automaticamente dal Database di SQL Azure vengono immediatamente eliminati quando correlate a colonne o una tabella viene eliminata.

### <a name="alternative---manual-index-management"></a>In alternativa, la gestione manuale degli indici

Senza la gestione automatica degli indici, sarebbe necessario eseguire manualmente una query utente [DM db_missing_index_details &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) vista per individuare gli indici che potrebbero migliorare le prestazioni, creare indici utilizzando i dettagli disponibili in questa vista e manualmente monitorare le prestazioni della query. Per trovare gli indici che devono essere eliminati, gli utenti devono monitorare le statistiche di utilizzo operativo degli indici per gli indici di ricerca utilizzato raramente.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] semplifica questo processo. [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] Analizza il carico di lavoro, identifica le query che è stato possibile eseguire più rapidamente con un nuovo indice e identifica gli indici inutilizzati o duplicati. Ulteriori informazioni sull'identificazione degli indici che devono essere modificati in [trovare indicazioni relative agli indici nel portale di Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-advisor-portal).

## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)  
 [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)     
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)           
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Funzioni JSON](../../relational-databases/json/index.md)
