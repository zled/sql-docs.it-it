---
title: "Monitoraggio delle prestazioni con Archivio query | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/28/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archivio query"
  - "Archivio query, descrizione"
ms.assetid: e06344a4-22a5-4c67-b6c6-a7060deb5de6
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Monitoraggio delle prestazioni con Archivio query
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  La funzionalità Archivio query di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mostra informazioni dettagliate sulle prestazioni e sulla scelta del piano di query. Semplifica la risoluzione dei problemi di prestazioni in quanto consente di individuare rapidamente le variazioni delle prestazioni causate da modifiche nei piani di query. Archivio query acquisisce automaticamente una cronologia delle query, dei piani e delle statistiche di runtime e li conserva per la consultazione. I dati vengono separati in base a intervalli di tempo, consentendo di visualizzare i modelli di utilizzo del database e capire quando sono state apportate modifiche al piano di query nel server. Per configurare l'archivio query, è possibile usare l'opzione [ALTER DATABASE SET](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md) . 
  
 Per informazioni sul funzionamento dell'archivio query nel database SQL di Azure, vedere [Uso dell'archivio query nel database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-operate-query-store/).  
  
##  <a name="a-nameenablinga-enabling-the-query-store"></a><a name="Enabling"></a> Abilitazione di Archivio query  
 Per impostazione predefinita, la funzionalità Archivio query non è attiva per i nuovi database.  
  
#### <a name="use-the-query-store-page-in-management-studio"></a>Usare la pagina Archivio query in Management Studio  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un database e quindi scegliere **Proprietà**.  
  
    > [!NOTE]  
    >  È necessaria almeno la versione [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Nella finestra di dialogo **Proprietà database** selezionare la pagina **Archivio query** .  
  
3.  Nella casella **Modalità operativa (richiesta)** selezionare **Attivato**.  
  
#### <a name="use-transact-sql-statements"></a>Usare istruzioni Transact-SQL  
  
1.  Per abilitare l'archivio query, usare l'istruzione **ALTER DATABASE** . Esempio:  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET QUERY_STORE = ON;  
    ```  
  
     Per altre opzioni della sintassi correlate all'archivio query, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
> [!NOTE]  
>  Non è possibile abilitare l'archivio query per il database **master** o **tempdb** .  
 
  
##  <a name="a-nameabouta-information-in-the-query-store"></a><a name="About"></a> Informazioni presenti in Archivio query  
 I piani di esecuzione per query specifiche in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in genere cambiano nel tempo per motivi diversi, quali modifiche delle statistiche, modifiche dello schema, creazione/eliminazione di indici e così via. Nella cache delle procedure, dove sono archiviati i piani di query memorizzati nella cache, viene archiviato solo il piano di esecuzione più recente. La rimozione dei piani dalla cache dei piani può dipendere anche da problemi di memoria. Di conseguenza, le regressioni delle prestazioni di esecuzione delle query causate da modifiche del piano di esecuzione possono essere rilevanti e richiedere tempo per la risoluzione.  
  
 Dal momento che nell'archivio query vengono mantenuti più piani di esecuzione per ogni query, è possibile applicare i criteri in modo che il processore di query usi un piano di esecuzione specifico per una query. Questo processo viene chiamato utilizzo forzato del piano. Per applicare l'utilizzo forzato del piano in Archivio query, viene usato un meccanismo simile all'hint per la query [USE PLAN](../Topic/Query%20Hints%20\(Transact-SQL\).md) , che però non richiede modifiche nelle applicazioni utente. Grazie all'utilizzo forzato del piano è possibile risolvere molto rapidamente una regressione delle prestazioni di esecuzione delle query causata da una modifica del piano.  
  
 La funzionalità Archivio query viene usata in genere negli scenari seguenti:  
  
-   Individuare e correggere rapidamente una regressione delle prestazioni di esecuzione delle query forzando un piano di query precedente. Correggere le query in cui si è verificata di recente una regressione delle prestazioni a causa di modifiche del piano di esecuzione.  
  
-   Determinare il numero di volte in cui una query è stata eseguita in un determinato intervallo di tempo, in modo da assistere un amministratore di database nella risoluzione dei problemi relativi alle prestazioni delle risorse.  
  
-   Identificare le prime *n* query (in base al tempo di esecuzione, al consumo della memoria e così via) nelle ultime *x* ore.  
  
-   Controllare la cronologia dei piani di query per una determinata query.  
  
-   Analizzare i modelli di utilizzo delle risorse (CPU, I/O e memoria) per un determinato database.  
  
 L'archivio query contiene due archivi: un **archivio piani** per salvare in modo permanente le informazioni sul piano di esecuzione e un **archivio delle statistiche di runtime** per salvare in modo permanente le informazioni sulle statistiche di esecuzione. Il numero di piani univoci che è possibile archiviare per una query nell'archivio piani è limitato dall'opzione di configurazione **max_plans_per_query** . Per migliorare le prestazioni, le informazioni vengono scritte nei due archivi in modo asincrono. Per ridurre al minimo l'utilizzo dello spazio, le statistiche di esecuzione di runtime nell'archivio delle statistiche di runtime vengono aggregate in un intervallo di tempo fisso. Per visualizzare le informazioni contenute in questi archivi, è possibile eseguire una query sulle viste del catalogo dell'archivio query.  
  
 La query seguente restituisce le informazioni sulle query e sui piani inclusi nell'archivio query.  
  
```  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
 
  
##  <a name="a-nameregresseda-use-the-regressed-queries-feature"></a><a name="Regressed"></a> Usare la funzionalità Query regredite  
 Dopo aver abilitato Archivio query, aggiornare la parte del database del riquadro Esplora oggetti per aggiungere la sezione **Archivio query** .  
  
 ![Query store tree in Object Explorer](../../relational-databases/performance/media/objectexplorerquerystore.PNG "Query store tree in Object Explorer")  
  
 Selezionare **Query regredite** per aprire il riquadro **Query regredite** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Nel riquadro Query regredite sono visualizzati i piani e le query presenti nell'archivio query. Usare le caselle a discesa nella parte superiore per selezionare le query in base a diversi criteri. Selezionare un piano per visualizzare il piano di query con interfaccia grafica. Sono disponibili pulsanti per visualizzare la query di origine, forzare e annullar e la forzatura di un piano di query e aggiornare la visualizzazione.  
  
 ![Regressed queries in object explorer](../../relational-databases/performance/media/objectexplorerregressedqueries.PNG "Regressed queries in object explorer")  
  
 Per forzare un piano, selezionare una query e un piano, quindi fare clic su **Forza piano**. È possibile forzare solo piani che sono stati salvati dalla funzionalità del piano di query e che sono ancora presenti nella relativa cache.  
 
  
##  <a name="a-nameoptionsa-configuration-options"></a><a name="Options"></a> Opzioni di configurazione  
 OPERATION_MODE  
 Può essere READ_WRITE (impostazione predefinita) o READ_ONLY.  
  
 CLEANUP_POLICY (STALE_QUERY_THRESHOLD_DAYS)  
 Configurare l'argomento STALE_QUERY_THRESHOLD_DAYS per specificare il numero di giorni per la conservazione dei dati nell'archivio query. Il valore predefinito è 30. Per l'edizione [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic, l'impostazione predefinita è 7 giorni.
  
 DATA_FLUSH_INTERVAL_SECONDS  
 Determina la frequenza con cui i dati scritti nell'archivio query vengono mantenuti su disco. Per ottimizzare le prestazioni, i dati raccolti dall'archivio query vengono scritti in modo asincrono sul disco. La frequenza con cui si verifica questo trasferimento asincrono viene configurata tramite DATA_FLUSH_INTERVAL_SECONDS. Il valore predefinito 900 (15 min).  
  
 MAX_STORAGE_SIZE_MB  
 Consente di configurare le dimensioni massime dell'archivio query. Se i dati nell'archivio query raggiungono il limite impostato in MAX_STORAGE_SIZE_MB, lo stato cambia da lettura/scrittura a sola lettura e la raccolta di nuovi dati viene interrotta.  Il valore predefinito è 100Mb. Per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition il valore predefinito è 1Gb, mentre per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition il valore predefinito è 10Mb.
  
 INTERVAL_LENGTH_MINUTES  
 Determina l'intervallo di tempo in cui vengono aggregati i dati delle statistiche di esecuzione di runtime nell'archivio query. Per ottimizzare l'utilizzo dello spazio, le statistiche di esecuzione di runtime nell'archivio delle statistiche di runtime vengono aggregate in un intervallo di tempo fisso. L'intervallo di tempo predefinito viene configurato tramite INTERVAL_LENGTH_MINUTES. Il valore predefinito è 60. 
  
 SIZE_BASED_CLEANUP_MODE  
 Determina se il processo di pulizia viene attivato automaticamente quando la quantità totale di dati sta per raggiungere le dimensioni massime. Può essere AUTO (impostazione predefinita) o OFF.  
  
 QUERY_CAPTURE_MODE  
 Determina se Archivio dati acquisisce tutte le query oppure le query pertinenti in base a conteggio esecuzioni e consumo delle risorse oppure se interrompe l'aggiunta delle nuove query e tiene semplicemente traccia delle query correnti. Può essere ALL (acquisire tutte le query), SUTO (ignorare le query poco frequenti e quelle con una durata di compilazione e di esecuzione non significativa) o NONE (arrestare l'acquisizione di nuove query). Il valore predefinito in SQL Server 2016 è ALL, mentre nel database SQL di Azure è AUTO.
  
 max_plans_per_query  
 Intero che rappresenta il numero massimo di piani mantenuti per ogni query. Il valore predefinito è 200.  
  
 Per determinare le opzioni correnti dell'archivio query, eseguire una query sulla vista **sys.database_query_store_options** . Per altre informazioni sui valori, vedere [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md).  
  
 Per altre informazioni sull'impostazione di opzioni con istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] , vedere [Gestione delle opzioni](#OptionMgmt).  
 
  
##  <a name="a-namerelateda-related-views-functions-and-procedures"></a><a name="Related"></a> Viste, funzioni e procedure correlate  
 È possibile visualizzare e gestire Archivio query con [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oppure usando le viste e le procedure seguenti.  
  
-   [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
### <a name="query-store-catalog-views"></a>Viste del catalogo di Archivio query  
 Le informazioni su Archivio query vengono presentate in sette viste del catalogo.  
  
-   [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)  
  
-   [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)  
  
-   [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)  
  
-   [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)  
  
-   [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)  
  
-   [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)  
  
-   [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)  
  
### <a name="query-store-stored-procedures"></a>Stored procedure di Archivio query  
 Per configurare Archivio query, vengono invece usate sei stored procedure.  
  
-   [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)  
  
-   [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)  
  
-   [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)  
  
-   [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)  
  
-   [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)  
  
-   [sp_query_store_remove_query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)  
 
  
##  <a name="a-namescenariosa-key-usage-scenarios"></a><a name="Scenarios"></a> Principali scenari di utilizzo  
  
###  <a name="a-nameoptionmgmta-option-management"></a><a name="OptionMgmt"></a> Gestione delle opzioni  
 Questa sezione fornisce alcune linee guida per la gestione della funzionalità Archivio query.  
  
 **Come sapere se la funzionalità Archivio query è attualmente attiva**  
  
 I dati della funzionalità Archivio query vengono archiviati nel database utente e per questo motivo è previsto un limite per le dimensioni che viene configurato con **MAX_STORAGE_SIZE_MB**. Se i dati in Archivio query raggiungono tale limite, lo stato cambia automaticamente da lettura/scrittura a sola lettura e la raccolta di nuovi dati viene interrotta.  
  
 Eseguire una query in [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md) per determinare se la funzionalità Archivio query è attualmente attiva e se la raccolta delle statistiche di runtime viene eseguita o meno.  
  
```  
SELECT actual_state, actual_state_desc, readonly_reason,   
    current_storage_size_mb, max_storage_size_mb  
FROM sys.database_query_store_options;  
```  
  
 Lo stato di Archivio query è determinato dalla colonna actual_state. Se è diverso dallo stato desiderato, la colonna readonly_reason può fornire ulteriori informazioni.   
Quando le dimensioni di Archivio query superano la quota, la funzionalità passa alla modalità readon_only.  
  
 **Ottenere le opzioni di Archivio query**  
  
 Per informazioni dettagliate sullo stato di Archivio query, eseguire l'istruzione seguente in un database utente.  
  
```  
SELECT * FROM sys.database_query_store_options;  
```  
  
 **Impostazione dell'intervallo di Archivio query**  
  
 È possibile ignorare l'intervallo per l'aggregazione delle statistiche di runtime delle query (impostazione predefinita: 60 minuti).  
  
```  
ALTER DATABASE <database_name>   
SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 15);  
```  
  
 Si noti che non sono consentiti valori arbitrari. È necessario usare uno dei valori seguenti: 1, 5, 10, 15, 30, 60 e 1440 minuti.  
  
 Il nuovo valore per l'intervallo viene esposto mediante la visualizzazione **sys.database_query_store_options** .  
  
 **Utilizzo dello spazio di Archivio query**  
  
 Per controllare le dimensioni e i limiti correnti di Archivio query, eseguire l'istruzione seguente nel database utente.  
  
```  
SELECT current_storage_size_mb, max_storage_size_mb   
FROM sys.database_query_store_options;  
```  
  
 Se lo spazio di archiviazione di Archivio query è esaurito, usare l'istruzione seguente per estenderlo.  
  
```  
ALTER DATABASE <database_name>   
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <new_size>);  
```  
  
 **Impostare tutte le opzioni di Archivio query**  
  
 È possibile impostare più opzioni di Archivio query contemporaneamente con un'unica istruzione ALTER DATABASE.  
  
```  
ALTER DATABASE <database name>   
SET QUERY_STORE (  
    OPERATION_MODE = READ_WRITE,  
    CLEANUP_POLICY =   
    (STALE_QUERY_THRESHOLD_DAYS = 30),  
    DATA_FLUSH_INTERVAL_SECONDS = 3000,  
    MAX_STORAGE_SIZE_MB = 500,  
    INTERVAL_LENGTH_MINUTES = 15,  
    SIZE_BASED_CLEANUP_MODE = AUTO,  
    QUERY_CAPTURE_MODE = AUTO,  
    MAX_PLANS_PER_QUERY = 1000  
);  
```  
  
 **Pulizia dello spazio**  
  
 Le tabelle interne di Archivio query vengono create nel filegroup PRIMARY durante la creazione del database e tale configurazione non è modificabile in un secondo momento. Se si esaurisce lo spazio, è possibile cancellare dati di Archivio query meno recenti usando l'istruzione seguente.  
  
```  
ALTER DATABASE <db_name> SET QUERY_STORE CLEAR;  
```  
  
 In alternativa, è possibile cancellare solo dati di query ad hoc perché sono meno rilevanti per le ottimizzazioni query e l'analisi del piano, ma occupano molto spazio.  
  
 **Eliminare query ad-hoc** È possibile eliminare le query che sono state eseguite solo una volta e che risalgono a più di 24 ore prima.  
  
```  
DECLARE @id int  
DECLARE adhoc_queries_cursor CURSOR   
FOR   
SELECT q.query_id  
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q   
    ON q.query_text_id = qt.query_text_id  
JOIN sys.query_store_plan AS p   
    ON p.query_id = q.query_id  
JOIN sys.query_store_runtime_stats AS rs   
    ON rs.plan_id = p.plan_id  
GROUP BY q.query_id  
HAVING SUM(rs.count_executions) < 2   
AND MAX(rs.last_execution_time) < DATEADD (hour, -24, GETUTCDATE())  
ORDER BY q.query_id ;  
  
OPEN adhoc_queries_cursor ;  
FETCH NEXT FROM adhoc_queries_cursor INTO @id;  
WHILE @@fetch_status = 0  
    BEGIN   
        PRINT @id  
        EXEC sp_query_store_remove_query @id  
        FETCH NEXT FROM adhoc_queries_cursor INTO @id  
    END   
CLOSE adhoc_queries_cursor ;  
DEALLOCATE adhoc_queries_cursor;  
```  
  
 Per la cancellazione dei dati non più necessari, è possibile definire procedure personalizzate con logiche diverse.  
  
 Per rimuovere i dati non necessari, nell'esempio precedente viene usata la stored procedure estesa **sp_query_store_remove_query** . È anche possibile usare:  
  
-   **sp_query_store_reset_exec_stats** : consente di cancellare le statistiche di runtime per un piano specifico.  
  
-   **sp_query_store_remove_plan** : consente di rimuovere un singolo piano.  
 
  
###  <a name="a-namepeformancea-performance-auditing-and-troubleshooting"></a><a name="Peformance"></a> Controllo delle prestazioni e risoluzione dei problemi  
 Archivio query conserva la cronologia delle metriche relative a compilazione e runtime per tutte le esecuzioni delle query e questo consente di ottenere facilmente informazioni sul carico di lavoro.  
  
 **Ultime *n* query eseguite sul database?**  
  
```  
SELECT TOP 10 qt.query_sql_text, q.query_id,   
    qt.query_text_id, p.plan_id, rs.last_execution_time  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
ORDER BY rs.last_execution_time DESC;  
```  
  
 **Numero di esecuzioni per ogni query.**  
  
```  
SELECT q.query_id, qt.query_text_id, qt.query_sql_text,   
    SUM(rs.count_executions) AS total_execution_count  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
GROUP BY q.query_id, qt.query_text_id, qt.query_sql_text  
ORDER BY total_execution_count DESC;  
```  
  
 **Numero di query con il tempo medio di esecuzione maggiore nell'ultima ora.**  
  
```  
SELECT TOP 10 rs.avg_duration, qt.query_sql_text, q.query_id,  
    qt.query_text_id, p.plan_id, GETUTCDATE() AS CurrentUTCTime,   
    rs.last_execution_time   
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
WHERE rs.last_execution_time > DATEADD(hour, -1, GETUTCDATE())  
ORDER BY rs.avg_duration DESC;  
```  
  
 **Numero di query con il maggior numero medio di letture I/O fisiche nelle ultime 24 ore, con il numero medio di righe e di esecuzioni corrispondente.**  
  
```  
SELECT TOP 10 rs.avg_physical_io_reads, qt.query_sql_text,   
    q.query_id, qt.query_text_id, p.plan_id, rs.runtime_stats_id,   
    rsi.start_time, rsi.end_time, rs.avg_rowcount, rs.count_executions  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi   
    ON rsi.runtime_stats_interval_id = rs.runtime_stats_interval_id  
WHERE rsi.start_time >= DATEADD(hour, -24, GETUTCDATE())   
ORDER BY rs.avg_physical_io_reads DESC;  
```  
  
 **Query con più piani.** Queste query sono particolarmente interessanti perché sono candidati a regressioni in seguito alla modifica del piano selezionato. La query seguente consente di identificare queste query unitamente a tutti i piani:  
  
```  
WITH Query_MultPlans  
AS  
(  
SELECT COUNT(*) AS cnt, q.query_id   
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q  
    ON qt.query_text_id = q.query_text_id  
JOIN sys.query_store_plan AS p  
    ON p.query_id = q.query_id  
GROUP BY q.query_id  
HAVING COUNT(distinct plan_id) > 1  
)  
  
SELECT q.query_id, object_name(object_id) AS ContainingObject,   
    query_sql_text, plan_id, p.query_plan AS plan_xml,  
    p.last_compile_start_time, p.last_execution_time  
FROM Query_MultPlans AS qm  
JOIN sys.query_store_query AS q  
    ON qm.query_id = q.query_id  
JOIN sys.query_store_plan AS p  
    ON q.query_id = p.query_id  
JOIN sys.query_store_query_text qt   
    ON qt.query_text_id = q.query_text_id  
ORDER BY query_id, plan_id;  
```  
  
 **Query in cui si è verificata di recente una regressione delle prestazioni (confrontando momenti diversi).** L'esempio di query seguente restituisce tutte le query in cui il tempo di esecuzione è raddoppiato nelle ultime 48 ore in seguito alla modifica del piano selezionato. La query confronta tutti gli intervalli delle statistiche di runtime affiancandoli.  
  
```  
SELECT   
    qt.query_sql_text,   
    q.query_id,   
    qt.query_text_id,   
    rs1.runtime_stats_id AS runtime_stats_id_1,  
    rsi1.start_time AS interval_1,   
    p1.plan_id AS plan_1,   
    rs1.avg_duration AS avg_duration_1,   
    rs2.avg_duration AS avg_duration_2,  
    p2.plan_id AS plan_2,   
    rsi2.start_time AS interval_2,   
    rs2.runtime_stats_id AS runtime_stats_id_2  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p1   
    ON q.query_id = p1.query_id   
JOIN sys.query_store_runtime_stats AS rs1   
    ON p1.plan_id = rs1.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi1   
    ON rsi1.runtime_stats_interval_id = rs1.runtime_stats_interval_id   
JOIN sys.query_store_plan AS p2   
    ON q.query_id = p2.query_id   
JOIN sys.query_store_runtime_stats AS rs2   
    ON p2.plan_id = rs2.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi2   
    ON rsi2.runtime_stats_interval_id = rs2.runtime_stats_interval_id  
WHERE rsi1.start_time > DATEADD(hour, -48, GETUTCDATE())   
    AND rsi2.start_time > rsi1.start_time   
    AND p1.plan_id <> p2.plan_id  
    AND rs2.avg_duration > 2*rs1.avg_duration  
ORDER BY q.query_id, rsi1.start_time, rsi2.start_time;  
```  
  
 Per visualizzare tutte le regressioni delle prestazioni, non solo quelle correlate alla modifica del piano selezionato, è sufficiente rimuovere la condizione `AND p1.plan_id <> p2.plan_id` dalla query precedente.  
  
 **Query in cui si è verificata di recente una regressione delle prestazioni (confrontando esecuzioni recenti e della cronologia).** La query successiva confronta le esecuzioni di query in base ai periodi di esecuzione. In questo specifico esempio la query confronta le esecuzioni nel periodo recente (1 ora) con il periodo della cronologia (ultimo giorno) e identifica quelle che hanno introdotto `additional_duration_workload`. Questa metrica viene ottenuta moltiplicando la differenza tra l'esecuzione media recente e quella media della cronologia e il numero delle esecuzioni recenti. Rappresenta in effetti la quantità di esecuzioni recenti con durata aggiuntiva introdotte rispetto alla cronologia:  
  
```  
--- "Recent" workload - last 1 hour  
DECLARE @recent_start_time datetimeoffset;  
DECLARE @recent_end_time datetimeoffset;  
SET @recent_start_time = DATEADD(hour, -1, SYSUTCDATETIME());  
SET @recent_end_time = SYSUTCDATETIME();  
  
--- "History" workload  
DECLARE @history_start_time datetimeoffset;  
DECLARE @history_end_time datetimeoffset;  
SET @history_start_time = DATEADD(hour, -24, SYSUTCDATETIME());  
SET @history_end_time = SYSUTCDATETIME();  
  
WITH  
hist AS  
(  
    SELECT   
        p.query_id query_id,   
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration,   
        SUM(rs.count_executions) count_executions,  
        COUNT(distinct p.plan_id) num_plans   
     FROM sys.query_store_runtime_stats AS rs  
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id  
    WHERE  (rs.first_execution_time >= @history_start_time   
               AND rs.last_execution_time < @history_end_time)  
        OR (rs.first_execution_time <= @history_start_time   
               AND rs.last_execution_time > @history_start_time)  
        OR (rs.first_execution_time <= @history_end_time   
               AND rs.last_execution_time > @history_end_time)  
    GROUP BY p.query_id  
),  
recent AS  
(  
    SELECT   
        p.query_id query_id,   
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration,   
        SUM(rs.count_executions) count_executions,  
        COUNT(distinct p.plan_id) num_plans   
    FROM sys.query_store_runtime_stats AS rs  
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id  
    WHERE  (rs.first_execution_time >= @recent_start_time   
               AND rs.last_execution_time < @recent_end_time)  
        OR (rs.first_execution_time <= @recent_start_time   
               AND rs.last_execution_time > @recent_start_time)  
        OR (rs.first_execution_time <= @recent_end_time   
               AND rs.last_execution_time > @recent_end_time)  
    GROUP BY p.query_id  
)  
SELECT   
    results.query_id query_id,  
    results.query_text query_text,  
    results.additional_duration_workload additional_duration_workload,  
    results.total_duration_recent total_duration_recent,  
    results.total_duration_hist total_duration_hist,  
    ISNULL(results.count_executions_recent, 0) count_executions_recent,  
    ISNULL(results.count_executions_hist, 0) count_executions_hist   
FROM  
(  
    SELECT  
        hist.query_id query_id,  
        qt.query_sql_text query_text,  
        ROUND(CONVERT(float, recent.total_duration/  
                   recent.count_executions-hist.total_duration/hist.count_executions)  
               *(recent.count_executions), 2) AS additional_duration_workload,  
        ROUND(recent.total_duration, 2) total_duration_recent,   
        ROUND(hist.total_duration, 2) total_duration_hist,  
        recent.count_executions count_executions_recent,  
        hist.count_executions count_executions_hist     
    FROM hist   
        JOIN recent   
            ON hist.query_id = recent.query_id   
        JOIN sys.query_store_query AS q   
            ON q.query_id = hist.query_id  
        JOIN sys.query_store_query_text AS qt   
            ON q.query_text_id = qt.query_text_id      
) AS results  
WHERE additional_duration_workload > 0  
ORDER BY additional_duration_workload DESC  
OPTION (MERGE JOIN);  
```  
 
  
###  <a name="a-namestabilitya-maintaining-query-performance-stability"></a><a name="Stability"></a> Misure per garantire la stabilità delle prestazioni di esecuzione delle query  
 Per le query eseguite più volte è possibile notare che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa piani diversi che comportano durate e utilizzi diversi delle risorse. Archivio query consente di rilevare il momento in cui si verifica una regressione delle prestazioni di esecuzione delle query e di determinare il piano ottimale in un periodo di interesse. È quindi possibile forzare il piano ottimale per le future esecuzioni delle query.  
  
 È anche possibile identificare incoerenze nelle prestazioni di una query con parametri (impostati sia automaticamente che manualmente). Tra i diversi piani è possibile identificare quello più rapido e adatto per tutti o per la maggior parte dei valori di parametro e forzarne l'uso in modo da garantire prestazioni prevedibili per un ampio numero di scenari utente.  
  
 **Forzare un piano per una query (applicando criteri di utilizzo forzato).** Quando si forza un piano per una determinata query, la query viene sempre eseguita con il piano di cui è stato forzato l'utilizzo.  
  
```  
EXEC sp_query_store_force_plan @query_id = 48, @plan_id = 49;  
```  
  
 Se si usa **sp_query_store_force_plan** , è possibile forzare solo piani che sono stati registrati da Archivio query come piani per tale query. In altre parole, gli unici piani disponibili per una query sono quelli già usati per eseguire tale query mentre Archivio query era attivo.  
  
 **Rimuovere l'utilizzo forzato del piano per una query.** Per impiegare di nuovo Query Optimizer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per calcolare il piano di query ottimale, usare **sp_query_store_unforce_plan** per annullare l'utilizzo forzato del piano selezionato per la query.  
  
```  
EXEC sp_query_store_unforce_plan @query_id = 48, @plan_id = 49;  
```  
 
  
## <a name="see-also"></a>Vedere anche  
 [Procedure consigliate per l'archivio query](../../relational-databases/performance/best-practice-with-the-query-store.md)   
 [Uso di Archivio query con OLTP in-memoria](../../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md)   
 [Scenari di utilizzo dell'Archivio query](../../relational-databases/performance/query-store-usage-scenarios.md)   
 [Come Archivio query raccoglie i dati](../../relational-databases/performance/how-query-store-collects-data.md)   
 [Stored procedure di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [Viste del catalogo di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [Strumenti per il monitoraggio e l'ottimizzazione delle prestazioni](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)   
 [Aprire Monitoraggio attività &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)   
 [Statistiche sulle query dinamiche](../../relational-databases/performance/live-query-statistics.md)   
 [Monitoraggio attività](../../relational-databases/performance-monitor/activity-monitor.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)  
 [Uso dell'archivio query nel database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-operate-query-store/) 
  