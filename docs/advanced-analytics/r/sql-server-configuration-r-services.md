---
title: Configurazione di SQL Server (R Services) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 382b39a7209480f7f02b0cee5d91eb6cbd662cd9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-configuration-for-use-with-r"></a>Configurazione di SQL Server per l'uso con R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo è il secondo in una serie che descrive l'ottimizzazione delle prestazioni per R Services in base alle due case study.  In questo articolo vengono fornite indicazioni sulla configurazione hardware e di rete del computer in cui viene utilizzato per eseguire SQL Server R Services. Contiene inoltre informazioni su come configurare l'istanza di SQL Server, database o tabelle utilizzate in una soluzione. Poiché l'utilizzo di NUMA in SQL Server applica una sfocatura la riga tra le ottimizzazioni di hardware e del database, una terza sezione vengono illustrati CPU affinità e regolamentazione delle risorse in modo dettagliato.

> [!TIP]
> Se si ha familiarità con SQL Server, è consigliabile rivedere anche la Guida di ottimizzazione delle prestazioni di SQL Server: [monitoraggio e ottimizzazione delle prestazioni](https://docs.microsoft.com/sql/relational-databases/performance/monitor-and-tune-for-performance).

## <a name="hardware-optimization"></a>Ottimizzazione di hardware

Ottimizzazione del server è importante assicurarsi di disporre di risorse per l'esecuzione di script esterni. Quando le risorse sono limitate, potresti vedere sintomi come i seguenti:

- Esecuzione del processo è posticipata o annullata per stabilire le priorità delle altre operazioni di database
- Script R che provocano di errore "superato" per terminare senza termine
- Dati caricati in memoria di R troncata, per risultati incompleti

### <a name="memory"></a>Memoria

La quantità di memoria disponibile nel computer può avere un notevole impatto sulle prestazioni di algoritmi analitici avanzati. Memoria insufficiente potrebbe influire sul grado di parallelismo, utilizzando il contesto di calcolo SQL. Può anche influire sulle dimensioni del blocco (righe per operazione di lettura) che possono essere elaborate e sul numero di sessioni simultanee supportato.

È consigliabile un minimo di 32 GB. Se si dispone di più di 32 GB di spazio disponibile, è possibile configurare l'origine dati SQL per l'utilizzo di più righe in ogni operazione di lettura per migliorare le prestazioni.

È inoltre possibile gestire la memoria utilizzata dall'istanza. Per impostazione predefinita, SQL Server ha la priorità dei processi dello script esterno quando la memoria viene allocata. In un'installazione predefinita di R Services, solo il 20% di memoria allocato per R.

In genere questo non è sufficiente per le attività di analisi scientifica dei dati, ma non si desidera mancanza di risorse SQL server, di memoria. È consigliabile provare e ottimizzare l'allocazione della memoria tra il motore di database, i servizi correlati e gli script esterni, a condizione che la configurazione ottimale varia caso per caso.

Per il modello di corrispondenza resume utilizzo dello script esterno è stato elevato e si sono verificati nessun altro database servizi motore di esecuzione; Pertanto, le risorse allocate per gli script esterni sono stati aumentato fino al 70%, che è la migliore configurazione per le prestazioni di script.

### <a name="power-options"></a>Opzioni risparmio energia

Nel sistema operativo Windows, il **ad alte prestazioni** power opzione deve essere utilizzata. Utilizzando un'impostazione di alimentazione differenti risultati incoerenti o una riduzione delle prestazioni quando si utilizza SQL Server.

### <a name="disk-io"></a>I/O su disco

Training e la stima, i processi con R Services sono intrinsecamente IO associato e variano a seconda della velocità dei dischi che è archiviato il database in. Può essere utile unità più veloce, quali le unità SSD (unità SSD).

Sull'I/O su disco influiscono anche altre applicazioni che accedono al disco, ad esempio le operazioni di lettura su un database da parte di altri client. Le prestazioni di I/O su disco dipendono anche dalle impostazioni nel file system in uso, come le dimensioni dei blocchi usate dal file system.

Se sono disponibili più unità, i database in un'unità diversa da quella di SQL Server in modo che le richieste per il motore di database non raggiunge lo stesso disco come archivio richieste per i dati archiviati nel database.

L'I/O su disco può avere un notevole impatto sulle prestazioni durante l'esecuzione di funzioni analitiche RevoScaleR che usano più iterazioni durante il training. Ad esempio, `rxLogit`, `rxDTree`, `rxDForest`, e `rxBTrees` utilizzano più iterazioni. Quando l'origine dati è SQL Server, i file temporanei che sono ottimizzati per acquisire i dati di questi algoritmi. Questi file vengono automaticamente eliminati al termine della sessione. Con un disco ad alte prestazioni per le operazioni di lettura/scrittura può migliorare significativamente il tempo complessivo trascorso per questi algoritmi.

> [!NOTE]
> Nelle versioni precedenti di R Services necessari per il supporto di nome file 8.3 nei sistemi operativi Windows. Questa restrizione è stata eliminata dopo il Service Pack 1. Tuttavia, è possibile utilizzare fsutil.exe per determinare se un'unità supporta nomi di 8.3 file o per abilitare il supporto in caso contrario.

### <a name="paging-file"></a>File di paging

Il sistema operativo Windows usa un file di paging per gestire i dump di arresto anomalo e per archiviare pagine di memoria virtuale. Se si nota un paging eccessivo, provare ad aumentare la memoria fisica nel computer. Benché la disponibilità di più memoria fisica non elimina il paging, riduce la necessità di paging.

Anche la velocità del disco in cui è archiviato il file di paging può influire sulle prestazioni. L'archiviazione del file di paging in un'unità SSD o l'uso di più file di paging su più SSD può migliorare le prestazioni.

Per informazioni sulla definizione delle dimensioni del file di paging, vedere [come determinare le dimensioni del file di pagina appropriata per le versioni a 64 bit di Windows](https://support.microsoft.com/kb/2860880).

## <a name="optimizations-at-instance-or-database-level"></a>Ottimizzazioni a livello di istanza o del database

Ottimizzazione dell'istanza di SQL Server è la chiave per l'esecuzione efficiente di script esterni.

> [!NOTE]
> Le impostazioni ottimali variano a seconda della dimensione e tipo di dati, il numero di colonne utilizzato per l'assegnazione dei punteggi o training di un modello.
> 
> È possibile esaminare i risultati delle ottimizzazioni specifiche nell'articolo finale: [ottimizzazione delle prestazioni - case study sulla risultati](../../advanced-analytics/r/performance-case-study-r-services.md)
> 
> Per gli script di esempio, vedere le varie [repository GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning).

### <a name="table-compression"></a>Compressione di tabelle

Spesso possano migliorare le prestazioni dei / o utilizzando la compressione o un archivio dati a colonne. In genere, i dati sono spesso ripetuti in numerose colonne all'interno di una tabella, in modo da usare un columnstore consente di sfruttare questi valori di ripetizione quando si comprime i dati.

Un columnstore potrebbe non essere efficace se sono presenti numerose operazioni di inserimento nella tabella, ma è consigliabile se i dati statici o vengono modificati solo raramente. Se un archivio a colonne non è appropriato, è possibile abilitare la compressione in una tabella principale di righe per migliorare l'I/O.

Per altre informazioni, vedere i documenti seguenti:

+ [Compressione dei dati](../../relational-databases/data-compression/data-compression.md)

+ [Abilitare la compressione in una tabella o un indice](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Guida agli indici columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)

### <a name="memory-optimized-tables"></a>Tabelle con ottimizzazione per la memoria

Oggi memoria non è più un problema per il computer moderni. Come per le specifiche hardware continuano a migliorare, è relativamente semplice ottenere valori RAM. Tuttavia, allo stesso tempo, in corso di produzione più rapidamente che mai dati e i dati devono essere elaborati con una latenza bassa.

Le tabelle con ottimizzazione per la memoria rappresentano una soluzione, che utilizzano grandi quantità di memoria disponibile nei computer avanzate di affrontare il problema dei big data. Le tabelle con ottimizzazione per la memoria si trovano principalmente in memoria, in modo che i dati sono di lettura e scritti per la memoria. Per la durabilità, una seconda copia della tabella viene mantenuta su disco e i dati vengono letti dal disco solo durante il recupero del database.

Se è necessario leggere e scrivere frequentemente alle tabelle, le tabelle con ottimizzazione per la memoria agevola la scalabilità elevate e a bassa latenza.  Nello scenario di ripresa di corrispondenza, utilizzo di tabelle con ottimizzazione per la memoria consentito di leggere tutte le funzionalità di ripristino dal database e di archiviarli nella memoria principale per la corrispondenza con nuove offerte di lavoro. Questo riduce in modo significativo i/o disco.

Ulteriori miglioramenti delle prestazioni sono stati ottenuti utilizzando una tabella con ottimizzazione per la memoria nel processo di scrittura stime nuovamente al database da più batch simultanei. L'utilizzo delle tabelle con ottimizzazione per la memoria in SQL Server abilitato a bassa latenza in tabella lettura e scrittura.

L'esperienza è trasparente anche durante lo sviluppo. Le tabelle durevoli con ottimizzazione per la memoria sono state create nello stesso momento che il database è stato creato. Pertanto, lo sviluppo utilizzato stesso flusso di lavoro indipendentemente dalla posizione dei dati.

### <a name="processor"></a>Processore

SQL Server può eseguire attività in parallelo utilizzando i core disponibili nel computer; più core disponibili, ottenere le migliori prestazioni. Mentre per le operazioni dei / o bound potrebbe non consente ad aumentare il numero di core, associate alla CPU algoritmi vantaggio dalla CPU più veloci con molti Core.

Poiché il server viene normalmente utilizzato da più utenti contemporaneamente, l'amministratore del database deve determinare il numero ideale di core che sono necessarie per supportare i calcoli di picco del carico di lavoro.

### <a name="resource-governance"></a>Governance delle risorse

Nelle edizioni che supportano Resource Governor, è possibile utilizzare pool di risorse per specificare che alcuni carichi di lavoro vengono allocate a un certo numero di CPU. È inoltre possibile gestire la quantità di memoria allocata per i carichi di lavoro specifici.

Governance delle risorse di SQL Server consente di centralizzare il monitoraggio e controllo delle diverse risorse utilizzati da SQL Server e da R. Ad esempio, si potrebbe allocare metà della memoria disponibile per il motore di database, per garantire che core services consente di eseguire sempre nonostante carichi di lavoro più pesante.

Il valore predefinito per il consumo di memoria tramite gli script esterni è limitato al 20% della memoria totale disponibile per SQL Server. Questo limite viene applicato per impostazione predefinita per garantire che tutte le attività che si basano sul server di database non sono gravemente condizionate dai processi R esecuzione prolungata. Tuttavia, questi limiti possono essere modificati dall'amministratore del database. In molti casi, il limite di 20% non è sufficiente per supportare i carichi di lavoro di apprendimento automatico grave.

Le opzioni di configurazione supportate sono **MAX_CPU_PERCENT**, **MAX_MEMORY_PERCENT**, e **MAX_PROCESSES**. Per visualizzare le impostazioni correnti, utilizzare l'istruzione seguente: `SELECT * FROM sys.resource_governor_external_resource_pools`

-  Se il server viene utilizzato principalmente per R Services, potrebbe essere utile aumentare MAX_CPU_PERCENT fino al 40% o % di 60.

-  Se il numero di sessioni R deve utilizzare lo stesso server allo stesso tempo, è necessario aumentare tutte e tre le impostazioni.

Per modificare i valori delle risorse allocate, utilizzare le istruzioni T-SQL.

+ Questa istruzione imposta l'utilizzo della memoria a 40%: `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)`

+ Questa istruzione imposta tutti e tre i valori configurabili: `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`

+ Se si modifica una memoria, CPU o l'impostazione max di processo e quindi si desidera applicare immediatamente le impostazioni, eseguire l'istruzione seguente: `ALTER RESOURCE GOVERNOR RECONFIGURE`

## <a name="soft-numa-hardware-numa-and-cpu-affinity"></a>Affinità di CPU, l'hardware NUMA e soft-NUMA

Quando si utilizza SQL Server come contesto di calcolo, è talvolta possibile ottenere prestazioni migliori, ottimizzando le impostazioni relative all'affinità NUMA e del processore. 

Sistemi con _hardware NUMA_ dispone di più di un bus di sistema, ognuno utilizzato da un piccolo set di processori. Ogni CPU può accedere alla memoria associata ad altri gruppi in modo coerente. Ogni gruppo viene denominato nodo NUMA. Se si dispone di hardware NUMA, è possibile che questo sia configurato in modo da utilizzare memoria interleaved anziché la modalità NUMA. In tal caso, Windows e pertanto SQL Server, non lo riconosceranno come NUMA. 

È possibile eseguire la query seguente per trovare il numero di nodi di memoria disponibili per SQL Server:

```SQL
SELECT DISTINCT memory_node_id
FROM sys.dm_os_memory_clerks
```

Se la query restituisce un solo nodo di memoria (nodo 0), non si dispone dell'hardware NUMA o l'hardware è configurato come interleaved (non NUMA). SQL Server ignora inoltre hardware NUMA quando non esiste un numero inferiore o quattro CPU, o se almeno un nodo è solo una CPU.

Se il computer con più processori, ma non dispone di hardware NUMA, è inoltre possibile utilizzare [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) per suddividere le CPU in gruppi più piccoli.  In SQL Server 2016 e SQL Server 2017, la funzionalità di Soft-NUMA viene attivata automaticamente all'avvio del servizio SQL Server.

Quando Soft-NUMA è abilitato, SQL Server gestisce automaticamente i nodi. Tuttavia, per ottimizzare i carichi di lavoro specifici, è possibile disabilitare _affinità soft_ e configurare manualmente l'affinità della CPU per i nodi NUMA soft. Ciò consente di visualizzare un maggiore controllo su cui i carichi di lavoro assegnati a quali nodi, in particolare se si utilizza un'edizione di SQL Server che supporta la governance delle risorse. Specificando l'affinità di CPU e allineamento dei pool di risorse con i gruppi di CPU, è possibile ridurre la latenza e verificare che i processi correlati vengano eseguiti nello stesso nodo NUMA.

Il processo generale per la configurazione soft-NUMA e affinità di CPU per supportare i carichi di lavoro R è il seguente:

1. Abilita soft-NUMA, se disponibile
2. Definire l'affinità processori
3. Creare i pool di risorse per i processi esterni, utilizzando [Resource Governor](../r/resource-governance-for-r-services.md)
4. Assegnare il [gruppi del carico di lavoro](../../relational-databases/resource-governor/resource-governor-workload-group.md) a specifici gruppi di affinità

Per informazioni dettagliate, incluso il codice di esempio, vedere l'esercitazione: [SQL ottimizzazione suggerimenti e trucchi (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Altre risorse:**

+ [Architettura soft-NUMA in SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)
    
    Come eseguire il mapping di nodi soft-NUMA alle CPU

+ [Architettura soft-NUMA automatica: esegue semplicemente più veloce (Bob Ward)](https://blogs.msdn.microsoft.com/bobsql/2016/06/03/sql-2016-it-just-runs-faster-automatic-soft-numa/)

   Viene descritto cronologia nonché i dettagli di implementazione, le prestazioni nel server multi-core più recenti.

## <a name="task-specific-optimizations"></a>Ottimizzazioni di attività specifiche

Questa sezione vengono riepilogati i metodi adottati in questi casi in altri test, per l'ottimizzazione delle specifiche di machine learning i carichi di lavoro. Carichi di lavoro comuni includono training del modello, estrazione di funzioni e funzionalità progettazione e vari scenari per l'assegnazione dei punteggi: a riga singola, batch di piccole dimensioni e batch di grandi dimensioni.

### <a name="feature-engineering"></a>Progettazione delle funzionalità

Un punto debole di R è solitamente vengono elaborato in una singola CPU. Si tratta di un collo di bottiglia delle prestazioni principali per molte attività, funzionalità particolarmente engineering. Nella soluzione corrispondenti alla ripresa, l'attività di progettazione di funzionalità solo creato le funzionalità del prodotto incrociato 2.500 che dovevano essere combinati con le funzionalità di 100 originale. Questa operazione richiederebbe una quantità significativa di tempo se tutto ciò che è stata eseguita su una singola CPU.

Esistono diversi modi per migliorare le prestazioni di progettazione delle funzioni. È possibile ottimizzare il codice R e mantenere l'estrazione di funzioni all'interno del processo di modellazione o spostare il processo di progettazione di funzionalità in SQL.

- Con R. Definire una funzione e quindi passarlo come argomento a [rxTransform](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxtransform) durante il training. Se il modello supporta l'elaborazione parallela, è possibile elaborare l'attività di progettazione di funzionalità con più CPU. Questo approccio, il team di analisi scientifica dei dati osservati un miglioramento delle prestazioni di 16% in termini di tempo di punteggio. Questo approccio richiede tuttavia un modello che supporta la parallelizzazione e una query che può essere eseguita tramite un piano parallelo.

- Contesto di calcolo usano R con un database SQL. In un ambiente multiprocessore con isolate risorse disponibili per l'esecuzione di batch separati, è possibile ottenere maggiore efficienza isolando le query SQL utilizzate per ogni batch, per estrarre dati da tabelle e limitare i dati nello stesso gruppo di carico di lavoro. Metodi usati per isolare i batch includono il partizionamento e utilizzano di PowerShell per eseguire query separate in parallelo.

- L'esecuzione parallela ad hoc: contesto di calcolo In un SQL Server, è possibile basarsi su motore di database SQL per imporre l'esecuzione parallela se possibile, e se tale opzione risulta più efficiente.

- Utilizzare T-SQL in un processo separato featurization. Precomputing i dati della funzionalità tramite SQL è in genere più veloce.

### <a name="prediction-scoring-in-parallel"></a>Stima (assegnazione dei punteggi) in parallelo

Uno dei vantaggi di SQL Server è la possibilità di gestire un volume elevato di righe in parallelo. Non è questo vantaggio contrassegnato come punteggio. In genere il modello non è necessario l'accesso a tutti i dati per il punteggio, pertanto è possibile partizionare i dati di input, con ogni gruppo di carico di lavoro, l'elaborazione di un'attività.

È anche possibile inviare i dati di input come una singola query e SQL Server analizza la query. Se è possibile creare un piano di query parallele per i dati di input, automaticamente partizioni dati assegnati ai nodi ed esegue obbligatorio join e aggregazioni in parallelo anche.

Se si è interessati nei dettagli su come definire una stored procedure per l'utilizzo nell'assegnazione dei punteggi, vedere il progetto di esempio in [GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips/SQLR) e cercare il file "step5_score_for_matching.sql". L'esempio di script anche tiene traccia delle query inizio e ora di fine e scrive il tempo necessario per la console SQL in modo che sia possibile valutare le prestazioni.

### <a name="concurrent-scoring-using-resource-groups"></a>Gruppi di risorse di punteggio simultanee

Per aumentare il problema di assegnazione dei punteggi, una procedura consigliata è di adottare l'approccio MapReduce in cui milioni di elementi sono suddivisi in più batch. Quindi, più processi punteggio vengono eseguiti contemporaneamente. In questo framework, i batch vengono elaborati in diversi set di CPU e i risultati vengono raccolti e scritti nel database.

Si tratta dell'approccio utilizzato nello scenario di corrispondenza resume; Tuttavia, la governance delle risorse in SQL Server è essenziale per l'implementazione di questo approccio. Impostando i gruppi di carico di lavoro per i processi di script esterni, è possibile indirizzare R punteggio processi a diversi gruppi di processori e ottenere una velocità effettiva.

Governance delle risorse può anche essere utile assegnare dividere le risorse disponibili nel server (CPU e memoria) per ridurre al minimo la concorrenza del carico di lavoro. È possibile impostare funzioni di classificazione per distinguere tra diversi tipi di processi R: ad esempio, si potrebbe decidere che punteggio chiamato da un'applicazione sempre ha la priorità, mentre i processi hanno la priorità bassa. L'isolamento delle risorse può potenzialmente migliorare i tempi di esecuzione e offrono prestazioni più prevedibili.

### <a name="concurrent-scoring-using-powershell"></a>Punteggio simultanee tramite PowerShell

Se si decide di partizionare i dati manualmente, è possibile utilizzare gli script di PowerShell per eseguire più attività simultanee. A tale scopo, utilizzare il cmdlet Invoke-SqlCmd e avviare l'attività in parallelo.

Nello scenario di ripresa di corrispondenza, la concorrenza è stata progettata come indicato di seguito:

- 20 processori divise in quattro gruppi di cinque CPU. Ogni gruppo di CPU si trova nello stesso nodo NUMA.

- Numero massimo di batch simultanei è stata impostata su 8.

- Ogni gruppo di carico di lavoro deve gestire due attività di assegnazione dei punteggi. Non appena un'attività fine della lettura dei dati e avvia il punteggio, l'altra attività può avviare la lettura dei dati dal database.

Per visualizzare gli script di PowerShell per questo scenario, aprire il file experiment.ps1 nel [Github progetto](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips).

### <a name="storing-models-for-prediction"></a>L'archiviazione di modelli per la stima

Quando la formazione e al termine della valutazione e si seleziona un modello migliore, è consigliabile archiviare il modello nel database in modo che sia disponibile per le stime. Caricare il modello di pre-calcolato dal database per la stima è efficiente, perché l'apprendimento di SQL Server Usa algoritmi speciale di serializzazione per archiviare e caricare i modelli durante lo spostamento tra R e il database.

> [!TIP]
> In SQL Server 2017, è possibile utilizzare la funzione di stima per eseguire l'assegnazione dei punteggi anche se R non è installato nel server. Sono supportati i tipi di modelli limitato, dal pacchetto RevoScaleR.

Tuttavia, a seconda dell'algoritmo utilizzato, alcuni modelli possono essere notevole, specialmente quando è sottoposto a training su un set di dati di grandi dimensioni. Ad esempio gli algoritmi, ad esempio **lm** o **glm** generare un numero elevato di dati di riepilogo e le regole. Poiché non esistono limiti alle dimensioni di un modello che può essere archiviato in una colonna varbinary, è consigliabile consente di eliminare gli elementi non necessari dal modello prima di archiviare il modello nel database di produzione.

## <a name="articles-in-this-series"></a>Articoli di questa serie

[Prestazioni di ottimizzazione per R: introduzione](../r/sql-server-r-services-performance-tuning.md)

[Ottimizzazione delle prestazioni per R - configurazione SQL Server](../r/sql-server-configuration-r-services.md)

[Ottimizzazione delle prestazioni per R - R ottimizzazione di codice e i dati](../r/r-and-data-optimization-r-services.md)

[Ottimizzazione delle prestazioni - case study sulla risultati](../r/performance-case-study-r-services.md)
