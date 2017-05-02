---
title: Procedure consigliate per l&quot;archivio query | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 11/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query Store, best practices
ms.assetid: 5b13b5ac-1e4c-45e7-bda7-ebebe2784551
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f00c5db3574f21010e682f964d06f3c2b61a1d09
ms.openlocfilehash: 9cd813b72eda096f780ed7140b6691f528251a30
ms.lasthandoff: 04/29/2017

---
# <a name="best-practice-with-the-query-store"></a>Procedure consigliate per l'archivio query
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Questo argomento descrive le procedure consigliate per l'uso dell'archivio query con il carico di lavoro.  
  
##  <a name="SSMS"></a> Use the Latest SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ha un set di interfacce utente progettate per la configurazione dell'archivio query nonché per l'utilizzo dei dati raccolti relativi al carico di lavoro.  
Scaricare la versione più recente di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] da: [https://msdn.microsoft.com/library/mt238290.aspx](https://msdn.microsoft.com/library/mt238290.aspx)  
  
 Per una descrizione rapida dell'uso dell'archivio query in scenari di risoluzione dei problemi, vedere il [post relativo all'archivio query nei blog di @Azure](https://azure.microsoft.com/en-us/blog/query-store-a-flight-data-recorder-for-your-database/).  
  
##  <a name="Insight"></a> Usare Informazioni dettagliate prestazioni query nel database SQL di Azure  
 Se si esegue l'archivio query in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è possibile usare **Informazioni dettagliate prestazioni query** per analizzare il consumo di DTU nel tempo.  
Anche se è possibile usare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per ottenere il consumo dettagliato delle risorse per tutte le query, in termini di CPU, memoria, I/O e così via, Informazioni dettagliate prestazioni query offre un metodo rapido ed efficace per determinare l'impatto delle query sul consumo di DTU complessivo per il database.  
Per altre informazioni, vedere l'articolo relativo a [Informazioni dettagliate prestazioni query del database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-query-performance/).    

##  <a name="using-query-store-with-elastic-pool-databases"></a>Usare l'archivio query con pool di database elastici
È possibile usare Archivio query in tutti i database, anche in pool molto compressi. Tutti i problemi correlati all'utilizzo eccessivo delle risorse, che possono essersi verificati quando Archivio query era abilitato per un numero elevato di database in pool elastici, sono stati risolti.
##  <a name="Configure"></a> Keep Query Store Adjusted to your Workload  
 Configurare l'archivio query in base al carico di lavoro e ai requisiti di risoluzione dei problemi di prestazioni.   
I parametri predefiniti offrono un modo rapido per iniziare, ma è opportuno monitorare il comportamento dell'archivio query nel tempo e regolare la configurazione di conseguenza:  
  
 ![query-store-properties](../../relational-databases/performance/media/query-store-properties.png "query-store-properties")  
  
 Di seguito sono riportate alcune linee guida per l'impostazione dei valori dei parametri:  
  
 **Dimensioni massime (MB):** specifica il limite per lo spazio dati che l'archivio query può occupare all'interno del database.  Si tratta dell'impostazione più importante, che influisce direttamente sulla modalità di funzionamento dell'archivio query.  
  
 Mentre l'archivio query raccoglie query, piani di esecuzione e statistiche, le sue dimensioni nel database aumentano fino a quando non viene raggiunto questo limite. A quel punto, l'archivio query passa automaticamente alla modalità operativa di sola lettura e smette di raccogliere nuovi dati. Questo si riflette negativamente sull'accuratezza dell'analisi delle prestazioni.  
  
 Il valore predefinito (100 MB) potrebbe non essere sufficiente se il carico di lavoro genera un numero elevato di query e piani diversi o se si vuole conservare la cronologia delle query per un periodo di tempo più lungo. Tenere traccia dell'utilizzo dello spazio e aumentare le Dimensioni massime (MB) per impedire che l'archivio query passi alla modalità di sola lettura.  Usare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] o eseguire lo script seguente per ottenere informazioni aggiornate sulle dimensioni dell'archivio query:  
  
```  
USE [QueryStoreDB];  
GO  
  
SELECT actual_state_desc, desired_state_desc, current_storage_size_mb,   
    max_storage_size_mb, readonly_reason  
FROM sys.database_query_store_options;  
```  
  
 Lo script seguente imposta un nuovo valore di Dimensioni massime (MB):  
  
```  
ALTER DATABASE [QueryStoreDB]  
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = 1024);  
```  
  
 **Intervallo di raccolta statistiche:** definisce il livello di granularità delle statistiche di runtime raccolte. Il valore predefinito è 1 ora. È possibile usare un valore inferiore se è necessaria una maggiore granularità o maggiore rapidità nel rilevare e limitare i problemi, ma questo influisce direttamente sulle dimensioni dei dati dell'archivio query. Usare SSMS o Transact-SQL per impostare un valore diverso per Intervallo di raccolta statistiche:  
  
```  
ALTER DATABASE [QueryStoreDB] SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 30);  
```  
  
 **Soglia per query non aggiornate (giorni):** criteri di pulizia basati sul tempo che controllano il periodo di conservazione di statistiche di runtime persistenti e query inattive.  
Per impostazione predefinita, l'archivio query è configurato in modo da conservare i dati per 30 giorni, che per alcuni scenari potrebbe essere un periodo eccessivamente lungo.  
  
 Evitare di conservare i dati cronologici che non si intende usare. In questo modo è possibile ridurre il ricorso allo stato di sola lettura. Le dimensioni dei dati dell'archivio query e il tempo necessario per rilevare e limitare il problema saranno più prevedibili. Usare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oppure lo script seguente per configurare i criteri di pulizia basati sul tempo:  
  
```  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 14));  
```  
  
 **Modalità di pulizia basata sulle dimensioni:** specifica se viene eseguita la pulizia automatica dei dati quando le dimensioni dei dati dell'archivio query si avvicinano al limite.  
  
 È consigliabile attivare la pulizia basata sulle dimensioni per assicurarsi che l'archivio query venga sempre eseguito in modalità lettura/scrittura e possa raccoglie i dati più recenti.  
  
```  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (SIZE_BASED_CLEANUP_MODE = AUTO);  
```  
  
 **Modalità di acquisizione archivio query:** specifica i criteri di acquisizione delle query per l'archivio query.  
  
-   **All** : vengono acquisite tutte le query. Si tratta dell'opzione predefinita.  
  
-   **Auto** : le query poco frequenti e le query con durata di compilazione ed esecuzione non significativa vengono ignorate. Le soglie per la durata della fase di esecuzione, la compilazione e il conteggio esecuzioni vengono determinate internamente.  
  
-   **None** l'archivio query smette di acquisire nuove query.  
  
 Lo script seguente imposta la modalità di acquisizione query su Auto:  
  
```  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (QUERY_CAPTURE_MODE = AUTO);  
```  
  
## <a name="how-to-start-with-query-performance-troubleshooting"></a>Iniziare a risolvere i problemi di prestazioni relativi alle query  
 Il flusso di lavoro di risoluzione dei problemi relativi all'archivio query è semplice, come illustra il diagramma seguente:  
  
 ![query-store-troubleshooting](../../relational-databases/performance/media/query-store-troubleshooting.png "query-store-troubleshooting")  
  
 Abilitare l'archivio query usando [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] come descritto nella sezione precedente o eseguire l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente:  
  
```  
ALTER DATABASE [DatabaseOne] SET QUERY_STORE = ON;  
```  
  
 La raccolta di un set di dati che rappresenti in modo accurato il carico di lavoro da parte dell'archivio query può richiedere del tempo. In genere, un giorno è sufficiente anche per carichi di lavoro molto complessi. Tuttavia, dopo aver abilitato la funzionalità è possibile iniziare a esplorare i dati e identificare le query che richiedono attenzione immediata.   
Passare alla sottocartella dell'archivio query nel nodo database in Esplora oggetti di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per aprire le viste di risoluzione dei problemi per scenari specifici.   
Le viste dell'archivio query di[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] possono essere usate con un set di metriche di esecuzione, espresse come una delle funzioni statistiche seguenti:  
  
|Metrica di esecuzione|Funzione statistica|  
|----------------------|------------------------|  
|Tempo CPU, Durata, Conteggio esecuzioni, Letture logiche, Scritture logiche, Utilizzo memoria e Letture fisiche|Media, Massimo, Minimo, Deviazione standard, Totale|  
  
 L'immagine seguente mostra come trovare le viste dell'archivio query:  
  
 ![query-store-views](../../relational-databases/performance/media/query-store-views.png "query-store-views")  
  
 La tabella seguente illustra quando usare ognuna delle viste dell'archivio query:  
  
|Vista di SSMS|Scenario|  
|---------------|--------------|  
|Query regredite|Trovare le query per cui le metriche di esecuzione sono recentemente peggiorate. <br />Usare questa vista per correlare i problemi di prestazioni osservati nell'applicazione con le query effettive da correggere o migliorare.|  
|Prime query per consumo risorse|Scegliere una metrica di esecuzione di interesse e trovare le query con i valori più estremi in un intervallo di tempo specificato. <br />Usare questa vista per concentrare l'attenzione sulle query più rilevanti che hanno l'impatto maggiore sul consumo delle risorse di database.|  
|Query rilevate|Tenere traccia dell'esecuzione delle query più importanti in tempo reale. In genere, questa vista viene usata in presenza di query con piani forzati per garantire la stabilità delle prestazioni delle query.|  
|Consumo complessivo risorse|Analizzare il consumo totale delle risorse per il database per una delle metriche di esecuzione.<br />Usare questa vista per identificare gli schemi di consumo delle risorse, ad esempio nei carichi di lavoro diurni e notturni, e ottimizzare il consumo complessivo per il database.|  
  
> [!TIP]  
>  Per informazioni dettagliate sull'uso di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per identificare le prime query per consumo risorse e correggere le query regredite a causa della modifica di una scelta del piano, vedere i [post relativi all'archivio query nei blog di @Azure](https://azure.microsoft.com/blog/query-store-a-flight-data-recorder-for-your-database/).  
  
 Quando si rileva una query con prestazioni non ottimali, l'azione correttiva dipende dalla natura del problema.  
  
-   Se la query è stata eseguita con più piani e l'ultimo piano è notevolmente peggiore rispetto al piano precedente, è possibile ricorrere al meccanismo di uso forzato del piano per fare in modo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usi sempre il piano ottimale per le esecuzioni future.  
  
     ![query-store-force-plan](../../relational-databases/performance/media/query-store-force-plan.png "query-store-force-plan")  
  
-   Si può concludere che la query sia priva di un indice per l'esecuzione ottimale. Queste informazioni vengono rese disponibili all'interno del piano di esecuzione query. Creare l'indice mancante e verificare le prestazioni della query usando l'archivio query.  
  
     ![query-store-show-plan](../../relational-databases/performance/media/query-store-show-plan.png "query-store-show-plan")  
  
     Se si esegue il carico di lavoro in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], iscriversi a Index Advisor per [!INCLUDE[ssSDS](../../includes/sssds-md.md)] per ricevere automaticamente indicazioni relative agli indici.  
  
-   In alcuni casi si può applicare la ricompilazione delle statistiche, se c'è una notevole differenza tra il numero stimato di righe nel piano di esecuzione e quello effettivo.  
  
-   Riscrivere le query problematiche. Ad esempio, per sfruttare i vantaggi della parametrizzazione delle query o per implementare la logica ottimale.  
  
##  <a name="Verify"></a> Verify Query Store is Collecting Query Data Continuously  
 L'archivio query può cambiare automaticamente la modalità operativa. È necessario monitorare regolarmente lo stato dell'archivio query per assicurarsi che sia in funzione e per prevenire errori dovuti a cause evitabili. Eseguire questa query per determinare la modalità operativa e visualizzare i parametri più importanti:  
  
```  
USE [QueryStoreDB];  
GO  
  
SELECT actual_state_desc, desired_state_desc, current_storage_size_mb,   
    max_storage_size_mb, readonly_reason, interval_length_minutes,   
    stale_query_threshold_days, size_based_cleanup_mode_desc,   
    query_capture_mode_desc  
FROM sys.database_query_store_options;  
```  
  
 La differenza tra `actual_state_desc` e `desired_state_desc` indica che si è verificata una modifica automatica della modalità operativa. La modifica più comune è il passaggio automatico dell'archivio query alla modalità di sola lettura. Eccezionalmente, l'archivio query può passare a uno stato di errore a causa di errori interni.  
  
 Quando lo stato effettivo è di sola lettura, usare la colonna **readonly_reason** per determinare la causa radice. In genere, l'archivio query passa alla modalità di sola lettura quando viene superato il limite delle dimensioni. In questo caso **readonly_reason** è impostato su 65536. Per altre situazioni, vedere [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md).  
  
 Per riportare l'archivio query in modalità lettura/scrittura e attivare la raccolta dei dati, prendere in considerazione i passaggi seguenti:  
  
-   Aumentare le dimensioni massime dello spazio di archiviazione usando l'opzione **MAX_STORAGE_SIZE_MB** di **ALTER DATABASE**.  
  
-   Eseguire la pulizia dei dati dell'archivio query usando l'istruzione seguente:  
  
    ```  
    ALTER DATABASE [QueryStoreDB] SET QUERY_STORE CLEAR;  
    ```  
  
 È possibile applicare uno o entrambi questi passaggi eseguendo questa istruzione, che ripristina in modo esplicito la modalità lettura/scrittura:  
  
```  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (OPERATION_MODE = READ_WRITE);  
```  
  
 Seguire questa procedura:  
  
-   È possibile prevenire le modifiche automatiche della modalità operativa applicando le procedure consigliate. Facendo in modo che le dimensioni dell'archivio query siano sempre inferiori al valore massimo consentito è possibile ridurre drasticamente il rischio di passaggio alla modalità di sola lettura. Attivare criteri basati sulle dimensioni, come descritto nella sezione [Adattare l'archivio query al carico di lavoro](#Configure) , in modo che l'archivio query esegua automaticamente la pulizia dei dati quando le dimensioni si avvicinano al limite.  
  
-   Per fare in modo che vengano conservati i dati più recenti, configurare criteri basati sul tempo per rimuovere regolarmente le informazioni non aggiornate.  
  
-   Infine, è consigliabile impostare la modalità di acquisizione query su Auto per escludere le query generalmente meno rilevanti per il carico di lavoro.  
  
### <a name="error-state"></a>Stato di errore  
 Per recuperare l'archivio query, provare a impostare in modo esplicito la modalità lettura/scrittura e ricontrollare lo stato effettivo.  
  
```  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (OPERATION_MODE = READ_WRITE);    
GO  
  
SELECT actual_state_desc, desired_state_desc, current_storage_size_mb,   
    max_storage_size_mb, readonly_reason, interval_length_minutes,   
    stale_query_threshold_days, size_based_cleanup_mode_desc,   
    query_capture_mode_desc  
FROM sys.database_query_store_options;  
```  
  
 Se il problema persiste, il danneggiamento dei dati dell'archivio query è persistente su disco. Prima di richiedere la modalità lettura/scrittura è necessario cancellare l'archivio query.  
  
```  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE CLEAR;  
GO  
  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (OPERATION_MODE = READ_WRITE);    
GO  
  
SELECT actual_state_desc, desired_state_desc, current_storage_size_mb,   
    max_storage_size_mb, readonly_reason, interval_length_minutes,   
    stale_query_threshold_days, size_based_cleanup_mode_desc,   
    query_capture_mode_desc  
FROM sys.database_query_store_options;  
```  
  
## <a name="set-the-optimal-query-capture-mode"></a>Impostare la modalità di acquisizione query ottimale  
 Mantenere i dati più rilevanti nell'archivio query. La tabella seguente descrive gli scenari tipici per ogni modalità di acquisizione query:  
  
|Modalità di acquisizione query|Scenario|  
|------------------------|--------------|  
|All|Analizzare accuratamente il carico di lavoro in termini di forme di query, frequenza di esecuzione e altre statistiche.<br /><br /> Identificare le nuove query nel carico di lavoro.<br /><br /> Rilevare l'eventuale uso di query ad hoc per identificare le possibilità di parametrizzazione automatica o dell'utente.|  
|Auto|Concentrare l'attenzione su query rilevanti e da correggere, ovvero le query eseguite regolarmente o che hanno un consumo di risorse elevato.|  
|None|Il set di query da monitorare è stato già acquisito in fase di esecuzione e si vuole eliminare qualsiasi distrazione introdotta da altre query.<br /><br /> È adatta ad ambienti di testing e di benchmarking.<br /><br /> È adatta ai fornitori di software che forniscono l'archivio query configurato per il monitoraggio del carico di lavoro della relativa applicazione.<br /><br /> Deve essere usata con cautela perché può precludere la possibilità di rilevare e ottimizzare nuove query importanti. Evitare di usare questa modalità a meno che non sia richiesta da uno scenario specifico.|  
  
## <a name="keep-the-most-relevant-data-in-query-store"></a>Mantenere i dati più rilevanti nell'archivio query  
 Configurare l'archivio query in modo che contenga solo i dati rilevanti per garantire l'esecuzione ininterrotta e la risoluzione ottimale dei problemi con un impatto minimo sul normale carico di lavoro.  
La tabella seguente riporta le procedure consigliate:  
  
|Procedura consigliata|Impostazione|  
|-------------------|-------------|  
|Limitare i dati cronologici conservati.|Configurare criteri basati sul tempo per attivare la pulizia automatica.|  
|Escludere le query non rilevanti.|Configurare la modalità di acquisizione query su Auto.|  
|Eliminare le query meno rilevanti quando vengono raggiunte le dimensioni massime.|Attivare criteri di pulizia basati sulle dimensioni.|  
  
##  <a name="Parameterize"></a> Avoid Using Non-Parameterized Queries  
 L'uso di query senza parametri quando non è assolutamente necessario, ad esempio nel caso di analisi ad hoc, non è consigliato.  Non è possibile riutilizzare i piani memorizzati nella cache e questo impone a Query Optimizer di compilare query per ogni testo query univoco.  
  L'archivio query può superare rapidamente il limite di dimensioni a causa del numero potenzialmente elevato di testi query diversi e del conseguente numero elevato di piani di esecuzione diversi con forma simile.  
Questo influisce negativamente sulle prestazioni del carico di lavoro e l'archivio query potrebbe passare alla modalità di sola lettura o potrebbe eliminare dati continuamente nel tentativo di gestire le query in ingresso.  
  
 Valutare le opzioni seguenti:  
  
-   Parametrizzare le query, se applicabile. Ad esempio, eseguire il wrapping delle query all'interno di una stored procedure.  
  
-   Usare l'opzione **Ottimizza per carichi di lavoro ad hoc** se il carico di lavoro contiene molti batch ad hoc monouso con piani di query diversi.  
  
    -   Confrontare il numero di valori query_hash distinti con il numero totale di voci in sys.query_store_query. Se il rapporto è vicino a 1, il carico di lavoro ad hoc genera query diverse.  
  
-   Applicare la parametrizzazione forzata per il database o per un subset di query, se il numero di piani di query diversi non è elevato.  
  
    -   Usare la guida di piano per forzare la parametrizzazione solo per la query selezionata.  
  
    -   Configurare la parametrizzazione forzata per il database, se nel carico di lavoro è presente un numero ridotto di piani di query diversi e se il rapporto tra il numero di valori query_hash distinti e il numero totale di voci in sys.query_store_query è molto inferiore a 1.  
  
-   Impostare la **Modalità di acquisizione query** su Auto per filtrare automaticamente le query ad hoc con un consumo di risorse ridotto.  
  
##  <a name="Drop"></a> Avoid a DROP and CREATE Pattern When Maintaining Containing Objects for the Queries  
 L'archivio query associa ogni voce query a un oggetto contenitore, ad esempio una stored procedure, una funzione o un trigger.  Quando si ricrea un oggetto contenitore, viene generata una nuova voce query per lo stesso testo query. Questo impedisce di monitorare le statistiche sulle prestazioni relative a tale query nel tempo e di ricorrere al meccanismo di uso forzato del piano. Per evitare questo problema, usare il processo `ALTER <object>` per modificare la definizione dell'oggetto contenitore, quando è possibile.  
  
##  <a name="CheckForced"></a> Check the Status of Forced Plans Regularly  
 L'uso forzato del piano è un meccanismo efficace per risolvere i problemi di prestazioni delle query critiche e renderle più prevedibili. Tuttavia, come accade con gli hint di piano e le guide di piano, forzare un piano non garantisce che poi venga usato nelle esecuzioni successive. In genere, quando lo schema del database viene modificato in modo che gli oggetti a cui fa riferimento il piano di esecuzione vengono modificati o eliminati, l'uso forzato del piano ha esito negativo. In questo caso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] opta per la ricompilazione delle query, mentre il motivo effettivo dell'errore viene esposto in [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md). La query seguente restituisce informazioni sui piani forzati:  
  
```  
USE [QueryStoreDB];  
GO  
  
SELECT p.plan_id, p.query_id, q.object_id as containing_object_id,  
    force_failure_count, last_force_failure_reason_desc  
FROM sys.query_store_plan AS p  
JOIN sys.query_store_query AS q on p.query_id = q.query_id  
WHERE is_forced_plan = 1;  
```  
  
 Per un elenco completo dei motivi, vedere [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md). È anche possibile usare l'oggetto XEvent **query_store_plan_forcing_failed** per tenere traccia degli errori di uso forzato del piano di risoluzione dei problemi.  
  
##  <a name="Renaming"></a> Avoid Renaming Databases if you have Queries with Forced Plans  
 I piani di esecuzione fanno riferimento agli oggetti con nomi in tre parti (`database.schema.object`).   
Se si rinomina un database, l'uso forzato del piano avrà esito negativo e questo provoca la ricompilazione in tutte le esecuzioni di query successive.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Stored procedure di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [Uso di Archivio query con OLTP in-memoria](../../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md)   
 [Monitoraggio delle prestazioni con Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  

