---
title: "Scenari di utilizzo dell&#39;Archivio query | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "04/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-query-tuning"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archivio query, scenari di utilizzo"
ms.assetid: f5309285-ce93-472c-944b-9014dc8f001d
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Scenari di utilizzo dell&#39;Archivio query
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Archivio query può essere usato in diversi scenari in cui è fondamentale rilevare e garantire prestazioni prevedibili del carico di lavoro. Di seguito sono riportati alcuni esempi:  
  
-   Individuare e risolvere le query con regressioni nella scelta del piano  
  
-   Identificare e ottimizzare le prime query per consumo di risorse  
  
-   Test A/B  
  
-   Mantenere la stabilità delle prestazioni durante l'aggiornamento a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   Identificare e migliorare i carichi di lavoro ad hoc  
  
## Individuare e risolvere le query con regressioni nella scelta del piano  
 Durante l'esecuzione di query normali, Query Optimizer può selezionare un piano diverso se alcuni input importanti vengono modificati, ad esempio se viene modificata la cardinalità dei dati, se vengono creati, modificati o eliminati indici, se vengono aggiornate le statistiche e così via.  In generale, il nuovo piano selezionato è migliore o uguale a quello usato in precedenza. Tuttavia, a volte il nuovo piano risulta decisamente peggiore. In questi casi si parla di regressione nella scelta del piano. Prima di Archivio query, identificare e risolvere questo problema risultava molto difficile perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non forniva un archivio dati predefinito che gli utenti potessero esaminare per i piani di esecuzione usati nel corso del tempo.  
  
 Ora, con Archivio query, è possibile eseguire rapidamente queste operazioni:  
  
-   Identificare tutte le query le cui metriche di esecuzione siano peggiorate nel periodo di tempo di interesse (ultima ora, giorno, settimana e così via). Usare **Query regredite** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per velocizzare l'analisi.  
  
-   Tra le query regredite è molto semplice individuare quelle con più piani e che hanno subito un peggioramento a causa di una scelta errata di un piano. Usare il riquadro **Riepilogo piano** in **Query regredite** per visualizzare tutti i piani per una query regredita e le relative prestazioni della query nel tempo.  
  
-   Forzare il piano precedente dalla cronologia se ha dimostrato di essere più efficace. Usare il pulsante **Forza piano** in **Query regredite** per forzare un piano selezionato per la query.  
  
 ![query-store-usage-1](../../relational-databases/performance/media/query-store-usage-1.png "query-store-usage-1")  
  
 Per una descrizione dettagliata dello scenario, vedere il blog sull' [Archivio query: un'utilità di traccia eventi dei dati per il database](https://azure.microsoft.com/blog/query-store-a-flight-data-recorder-for-your-database/) .  
  
## Identificare e ottimizzare le prime query per consumo di risorse  
 Anche se il carico di lavoro può generare migliaia di query, nella pratica la gran parte delle risorse di sistema viene usata solo da poche query che, di conseguenza, richiedono attenzione. Tra le prime query per consumo di risorse si rilevano in genere quelle regredite o quelle che possono essere migliorate con un'ottimizzazione aggiuntiva.  
  
 Il modo più facile per iniziare l'esplorazione consiste nell'aprire **Prime query per consumo di risorse** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  L'interfaccia utente è suddivisa in tre riquadri: un istogramma che rappresenta le prime query per consumo di risorse (sinistra), un riepilogo del piano per la query selezionata (destra) e un piano di query visivo per il piano selezionato (in basso). Fare clic sul pulsante **Configura** per controllare il numero di query da analizzare e l'intervallo di tempo di interesse. È anche possibile scegliere tra diverse dimensioni di consumo delle risorse (durata, CPU, memoria, operazioni I/O, numero di esecuzione) e valori di base (Media, Min, Max, Totale, Deviazione standard).  
  
 ![query-store-usage-2](../../relational-databases/performance/media/query-store-usage-2.png "query-store-usage-2")  
  
 Esaminare il riepilogo del piano a destra per analizzare la cronologia di esecuzione e avere informazioni sui diversi piani e sulle statistiche di runtime. Usare il riquadro inferiore per esaminare i diversi piani o per eseguire un confronto visivo con il rendering in modalità affiancata (usare il pulsante Confronta).  
  
 Quando si rileva una query con prestazioni non ottimali, l'azione correttiva dipende dalla natura del problema:  
  
1.  Se la query è stata eseguita con più piani e l'ultimo piano è significativamente peggiore del piano precedente, è possibile usare il meccanismo di utilizzo forzato del piano per essere certi che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] userà il piano ottimale per le esecuzioni successive  
  
2.  Verificare se Query Optimizer rileva indici mancanti nel piano XML. In caso affermativo, creare l'indice mancante e usare Archivio query per valutare le prestazioni delle query dopo la creazione dell'indice  
  
3.  Verificare che le statistiche siano aggiornate per le tabelle sottostanti usate dalla query.  
  
4.  Verificare che gli indici usati dalla query siano deframmentati.  
  
5.  Valutare l'opportunità di riscrivere la query con costo elevato. Ad esempio, sfruttare i vantaggi associati alla parametrizzazione della query e ridurre l'utilizzo di SQL dinamico. Implementare la logica ottimale durante la lettura dei dati (applicare il filtro dei dati sul lato database, non sul lato applicazione).  
  
## Test A/B  
 Usare Archivio query per confrontare le prestazioni del carico di lavoro prima e dopo la modifica dell'applicazione che si intende introdurre.  L'elenco seguente contiene alcuni esempi in cui è possibile usare Archivio query per valutare l'impatto della modifica dell'ambiente o dell'applicazione sulle prestazioni del carico di lavoro:  
  
-   Implementazione della nuova versione dell'applicazione.  
  
-   Aggiunta di nuovo hardware al server.  
  
-   Creazione degli indici mancanti nelle tabelle a cui fanno riferimento le query con costo elevato.  
  
-   Applicazione di un criterio di filtro per la sicurezza a livello di riga. Per altre informazioni, vedere il blog sull' [ottimizzazione della sicurezza a livello di riga con Archivio query](http://blogs.msdn.com/b/sqlsecurity/archive/2015/07/21/optimizing-rls-performance-with-the-query-store.aspx).  
  
-   Aggiunta del controllo temporale delle versioni di sistema alle tabelle che vengono modificate di frequente dalle applicazioni OLTP.  
  
 In qualsiasi scenario, applicare il flusso di lavoro seguente:  
  
1.  Eseguire il carico di lavoro con Archivio query prima della modifica pianificata per generare dati di base delle prestazioni.  
  
2.  Applicare la modifica dell'applicazione in un determinato momento controllato.  
  
3.  Continuare l'esecuzione del carico di lavoro per il tempo necessario a generare un'immagine delle prestazioni del sistema dopo la modifica  
  
4.  Confrontare i risultati di 1 e 3.  
  
    1.  Aprire **Consumo complessivo risorse** per determinare l'impatto dell'intero database  
  
    2.  Aprire **Prime query per consumo di risorse** (o eseguire un'analisi con [!INCLUDE[tsql](../../includes/tsql-md.md)]) per analizzare l'impatto della modifica nelle query più importanti.  
  
5.  Decidere se mantenere la modifica o eseguire operazioni di rollback se le nuove prestazioni sono inaccettabili.  
  
 La figura seguente mostra l'analisi di Archivio query (passaggio 4) in caso di creazione dell'indice mancante. Aprire il riquadro **Prime query per consumo di risorse**/Riepilogo piano per ottenere la visualizzazione per la query che dovrebbe essere interessata dalla creazione dell'indice:  
  
 ![query-store-usage-3](../../relational-databases/performance/media/query-store-usage-3.png "query-store-usage-3")  
  
 È anche possibile confrontare i piani prima e dopo la creazione dell'indice con il rendering in modalità affiancata, usando l'opzione della barra degli strumenti Confronta i piani per la query selezionata in una finestra separata, contrassegnata con un quadrato rosso nella barra degli strumenti.  
  
 ![query-store-usage-4](../../relational-databases/performance/media/query-store-usage-4.png "query-store-usage-4")  
  
 Nel piano prima della creazione dell'indice (plan_id = 1, sopra) manca l'hint per l'indice e si può vedere che Clustered Index Scan è l'operatore con il costo più elevato nella query (rettangolo rosso).  
  
 Nel piano dopo la creazione dell'indice mancante (plan_id = 15, sotto) ora è presente Index Seek (Nonclustered) che consente di ridurre il costo complessivo della query e di migliorare le prestazioni (rettangolo verde).  
  
 In base all'analisi è consigliabile mantenere l'indice visto che le prestazioni delle query sono state migliorate.  
  
## Mantenere la stabilità delle prestazioni durante l'aggiornamento a SQL Server 2016  
 Prima di [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], gli utenti erano esposti al rischio di regressione delle prestazioni durante l'aggiornamento alla versione più recente della piattaforma. Il motivo era che la versione più recente di Query Optimizer si attivava subito dopo l'installazione dei nuovi bit.  
  
 A partire da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tutte le modifiche di Query Optimizer sono legate all'ultimo `COMPATIBILITY_LEVEL`, quindi i piani non vengono modificati al punto di aggiornamento, ma quando un utente modifica `COMPATIBILITY_LEVEL` alla versione più recente. Questa funzionalità, in combinazione con Archivio query, offre un alto livello di controllo sulle prestazioni delle query nel processo di aggiornamento. Il flusso di lavoro di aggiornamento consigliato è illustrato nella figura seguente:  
  
 ![query-store-usage-5](../../relational-databases/performance/media/query-store-usage-5.png "query-store-usage-5")  
  
1.  Aggiornare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza modificare `COMPATIBILITY_LEVEL`. Non esegue l'aggiornamento alla versione più recente di Query Optimizer, ma fornisce le funzionalità di [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tra cui Archivio query.  
  
2.  Abilitare Archivio query: acquisire le query e i piani e stabilire i valori di base delle prestazioni con il valore `COMPATIBILITY_LEVEL`precedente. Rimanere in questo passaggio per il tempo necessario ad acquisire tutti i piani e a ottenere valori di base stabili.  
  
3.  Passare al livello di compatibilità più recente: espone il carico di lavoro alla versione di Query Optimizer più recente e consente, in teoria, di creare nuovi piani.  
  
4.  Usare l'Archivio query per le correzioni di analisi e regressioni: nella maggior parte dei casi, il nuovo Query Optimizer dovrebbe produrre piani migliori. Tuttavia, Archivio query fornisce un modo semplice per identificare le regressioni nella scelta del piano e risolverle usando un meccanismo di utilizzo forzato del piano.  
  
## Identificare e migliorare i carichi di lavoro ad hoc  
 Alcuni carichi di lavoro non includono query dominanti che è possibile ottimizzare per migliorare le prestazioni complessive dell'applicazione. In genere, questi carichi di lavoro sono caratterizzati da un numero relativamente elevato di query diverse, ciascuna delle quali utilizza una parte delle risorse di sistema. Essendo univoche, queste query vengono eseguite raramente, (di solito una sola volta, quindi si consiglia di assegnare un nome ad hoc), di conseguenza il consumo di runtime non è critico. D'altra parte, dato che l'applicazione genera continuamente nuove query, una parte significativa delle risorse di sistema viene impiegata per la compilazione di query, il che non rappresenta uno scenario ottimale. Questa situazione non è ideale per Archivio query perché un numero elevato di query e piani ne occupa lo spazio riservato e causa probabilmente il passaggio in tempi molto rapidi alla modalità di sola lettura di Archivio query. Se è attivato **Modalità di pulizia basata sulle dimensioni**, un'opzione [fortemente consigliata](https://msdn.microsoft.com/library/mt604821.aspx) per mantenere Archivio query sempre attivo e in esecuzione, il processo in background esegue costantemente la pulizia delle strutture di Archivio query assorbendo molto spesso notevoli risorse di sistema.  
  
 La visualizzazione **Prime query per consumo di risorse** fornisce la prima indicazione relativa alla natura ad hoc del carico di lavoro:  
  
 ![query-store-usage-6](../../relational-databases/performance/media/query-store-usage-6.png "query-store-usage-6")  
  
 Usare la metrica **Conteggio esecuzioni** per verificare se le prime query sono ad hoc (questa operazione richiede l'esecuzione di Archivio query con `QUERY_CAPTURE_MODE = ALL`). Dal diagramma precedente è possibile vedere che il 90% delle **Prime query per consumo di risorse** viene eseguito una sola volta.  
  
 In alternativa, è possibile eseguire script [!INCLUDE[tsql](../../includes/tsql-md.md)] per ottenere il numero totale di testi della query, query e piani nel sistema e determinarne le differenze confrontando query_hash e plan_hash:  
  
```  
/*Do cardinality analysis when suspect on ad-hoc workloads*/  
SELECT COUNT(*) AS CountQueryTextRows FROM sys.query_store_query_text;  
SELECT COUNT(*) AS CountQueryRows FROM sys.query_store_query;  
SELECT COUNT(DISTINCT query_hash) AS CountDifferentQueryRows FROM  sys.query_store_query;  
SELECT COUNT(*) AS CountPlanRows FROM sys.query_store_plan;  
SELECT COUNT(DISTINCT query_plan_hash) AS  CountDifferentPlanRows FROM  sys.query_store_plan;  
```  
  
 Si tratta di un potenziale risultato che può essere prodotto nel caso di carichi di lavoro con query ad hoc:  
  
 ![query-store-usage-7](../../relational-databases/performance/media/query-store-usage-7.png "query-store-usage-7")  
  
 Il risultato della query mostra che, nonostante il numero elevato di query e piani in Archivio query, query_hash e plan_hash in realtà non sono diversi. Un rapporto molto maggiore di 1 tra i testi della query univoci e il valore query_hash univoco indica che il carico di lavoro è un buon candidato per la parametrizzazione perché l'unica differenza tra le query è la costante letterale (parametro) fornita come parte del testo della query.  
  
 In genere, questa situazione si verifica quando l'applicazione genera query, invece di richiamare stored procedure o query con parametri, oppure quando si basa su framework di mapping relazionale a oggetti che generano query per impostazione predefinita.  
  
 Se si ha il controllo del codice dell'applicazione è possibile valutare l'opportunità di riscrivere il livello di accesso ai dati per usare stored procedure o query con parametri. Tuttavia, questa situazione può essere notevolmente migliorata anche senza modificare l'applicazione, forzando la parametrizzazione delle query per l'intero database, ovvero per tutte le query, oppure per i singoli modelli di query con lo stesso valore query_hash.  
  
 L'approccio che prevede l'uso di singoli modelli di query richiede la creazione di guide di piano:  
  
```  
  
/*Apply plan guide for the selected query template*/  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'<your query text goes here>',  
    @stmt OUTPUT,   
    @params OUTPUT;  
  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION (PARAMETERIZATION FORCED)';  
```  
  
 La soluzione che include le guide di piano è più precisa, ma richiede più lavoro.  
  
 Se tutte o la maggior parte delle query sono idonee alla parametrizzazione automatica, valutare la modifica di `FORCED PARAMETERIZATION` per l'intero database:  
  
```  
  
/*Apply forced parameterization for entire database*/  
ALTER DATABASE <database name> SET PARAMETERIZATION  FORCED;  
```  
  
 Dopo aver applicato uno di questi passaggi, in **Prime query per consumo di risorse** viene visualizzata un'altra immagine del carico di lavoro.  
  
 ![query-store-usage-8](../../relational-databases/performance/media/query-store-usage-8.png "query-store-usage-8")  
  
 In alcuni casi l'applicazione può generare un numero elevato di query diverse, che non sono adatte alla parametrizzazione automatica. In questo caso viene visualizzato un numero elevato di query nel sistema ma il rapporto tra le query univoche e il valore query_hash univoco è probabilmente prossimo a 1.  
  
 In questo caso è opportuno impostare Ottimizza per carichi di lavoro ad hoc per evitare di sprecare memoria cache per query che probabilmente non verranno più eseguite. Per impedire l'acquisizione di tali query in Archivio query, impostare `QUERY_CAPTURE_MODE` su `AUTO`.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
  
sp_configure 'optimize for ad hoc workloads', 1;  
GO  
RECONFIGURE;  
GO  
  
ALTER DATABASE  [QueryStoreTest] SET QUERY_STORE CLEAR;  
ALTER DATABASE  [QueryStoreTest] SET QUERY_STORE = ON   
    (OPERATION_MODE = READ_WRITE, QUERY_CAPTURE_MODE = AUTO);  
```  
  
## Vedere anche  
 [Monitoraggio delle prestazioni con Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Procedure consigliate per l'archivio query](../../relational-databases/performance/best-practice-with-the-query-store.md)  
  
  