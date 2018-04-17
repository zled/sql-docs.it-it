---
title: Le prestazioni per SQL Server R Services - risultati e le risorse | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ce5fb99b3808b9da0d32bee48ff31f6e0b2dae95
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="performance-for-r-services-results-and-resources"></a>Prestazioni per R Services: risultati e le risorse
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo è la quarta e finale in una serie che descrive ottimizzazione delle prestazioni per R Services. In questo articolo sono riepilogati i metodi, i risultati e conclusioni del case due study test diversi metodi di ottimizzazione.

I due case study ha obiettivi diversi:

+ Il primo case study, dal team di sviluppo di R Services, richiesta misurare l'impatto delle tecniche di ottimizzazione specifiche
+ Il secondo case study, da un team esperto di dati, sperimentato con più metodi per determinare le migliori ottimizzazioni per uno specifico scenario di assegnazione dei punteggi di volumi elevati.

Questo argomento elenca i risultati dettagliati del primo case study. Per il case study, secondo un riepilogo descrive le conclusioni generali. Alla fine di questo argomento vengono forniti collegamenti a tutti gli script e i dati di esempio e le risorse utilizzate dagli autori originali.

## <a name="performance-case-study-airline-dataset"></a>Case study di prestazioni: Airline set di dati

Questo case study dal team di sviluppo di SQL Server R Services testare gli effetti delle diverse ottimizzazioni. È stato creato un modello rxLogit singolo e assegnazione dei punteggi eseguite sul set di dati Airline. Le ottimizzazioni sono state applicate durante il training e assegnazione dei punteggi di processi per valutare l'impatto singoli.

- Github: [dati e gli script di esempio](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning) per Studio ottimizzazioni di SQL Server

### <a name="test-methods"></a>Metodi di test

1. Il set di dati Airline consiste in una singola tabella di M 10 righe. È stato scaricato e caricamento bulk in SQL Server.
2. Sono state apportate sei copie della tabella.
3. Varie modifiche sono state applicate alle copie della tabella, per testare le funzionalità di SQL Server, ad esempio la compressione di pagina, la compressione di riga, l'indicizzazione, l'archivio dati a colonne e così via.
4. Le prestazioni è stata misurata prima e dopo ogni ottimizzazione è stata applicata.

| Nome tabella| Description|
|------|------|
| *airline* | Dati convertiti dal file con estensione xdf originale tramite `rxDataStep`.|                          |
| *airlineWithIntCol*   | *DayOfWeek* convertito in un intero anziché in una stringa. Aggiunge anche una colonna *rowNum*.|
| *airlineWithIndex*    | Stessi dati della tabella *airlineWithIntCol*, ma con un singolo indice cluster basato sulla colonna *rowNum*.|
| *airlineWithPageComp* | Stessi dati della tabella *airlineWithIndex*, ma con la compressione di pagina abilitata. Aggiunge anche due colonne, *CRSDepHour* e *Late*, che vengono calcolate da *CRSDepTime* e *ArrDelay*. |
| *airlineWithRowComp*  | Stessi dati della tabella *airlineWithIndex*, ma con la compressione di riga abilitata. Aggiunge anche due colonne, *CRSDepHour* e *Late*, che vengono calcolate da *CRSDepTime* e *ArrDelay*. |
| *airlineColumnar*     | Archivio a colonne con un singolo indice cluster. Questa tabella viene popolata con i dati di un file pulito con estensione csv.|

Ogni test è costituito da questi passaggi:

1. Prima di ciascun test è stata generata la Garbage Collection R.
2. Un modello di regressione logistica è stato creato in base ai dati di tabella. Il valore di *rowsPerRead* per ogni test è stato impostato su 500000.
3. Punteggi generati usando il modello con training
4. Ogni test è stato eseguito sei volte. Il tempo di esecuzione del primo (il "Esegui freddo") è stato eliminato. Per consentire l'outlier occasionale, il **massimo** tempo tra le esecuzioni di cinque rimanenti anche è stato eliminato. La media delle quattro esecuzioni rimanenti è stata usata per calcolare il runtime trascorso medio di ogni test.
5. Sono stati eseguiti i test utilizzando il *reportProgress* parametro con il valore 3 (= intervalli di report e lo stato di avanzamento). Ogni file di output contiene informazioni riguardanti il tempo impiegato nelle operazioni i/o, tempo di transizione e tempo di calcolo. Questi tempi sono utili per la diagnosi e la risoluzione dei problemi.
6. L'output della console è stato inoltre indirizzato a un file nella directory di output.
7. Script di test elaborati gli orari in questi file per calcolare il tempo medio in esecuzioni.

Ad esempio, i risultati seguenti sono le ore da un singolo test. I principali intervalli di interesse sono quelli relativi al **tempo di lettura totale** (tempo di I/O) e al **tempo di transizione** (overhead nell'impostazione dei processi per il calcolo).

**Intervalli di esempio**

```
Running IntCol Test. Using airlineWithIntCol table.
run 1 took 3.66 seconds
run 2 took 3.44 seconds
run 3 took 3.44 seconds
run 4 took 3.44 seconds
run 5 took 3.45 seconds
run 6 took 3.75 seconds
  
Average Time: 3.4425
metric time pct
1 Total time 3.4425 100.00
2 Overall compute time 2.8512 82.82
3 Total read time 2.5378 73.72
4 Transition time 0.5913 17.18
5 Total non IO time 0.3134 9.10
```

Si consiglia di scaricare e modificare gli script di test per la risoluzione dei problemi con R Services o con le funzioni RevoScaleR.

### <a name="test-results-all"></a>Verificare i risultati (tutti)

Questa sezione vengono confrontate prima e dopo i risultati per ciascun test.

#### <a name="data-size-with-compression-and-a-columnar-table-store"></a>Dimensioni dei dati con la compressione e un archivio a colonne di tabella

Il primo test confrontati l'utilizzo di compressione e una tabella a colonne per ridurre le dimensioni dei dati.

| Nome tabella            | Righe     | Riservato   | data       | index_size | Non utilizzato  | % salvataggio (riservato) |
|-----------------------|----------|------------|------------|------------|---------|---------------------|
| *airlineWithIndex*    | 10000000 | 2978816 KB | 2972160 KB | 6128 KB    | 528 KB  | 0                   |
| *airlineWithPageComp* | 10000000 | 625784 KB  | 623744 KB  | 1352 KB    | 688 KB  | 79%                 |
| *airlineWithRowComp*  | 10000000 | 1262520 KB | 1258880 KB | 2552 KB    | 1088 KB | 58%                 |
| *airlineColumnar*     | 9999999  | 201992 KB  | 201624 KB  | n/d        | 368 KB  | 93%                 |

**Conclusioni**

La riduzione massima di dimensioni dei dati è stata ottenuta applicando un indice columnstore, aggiungendo la compressione di pagina.

#### <a name="effects-of-compression"></a>Effetti della compressione

Questo test confrontati i vantaggi della compressione di riga, la compressione di pagina e nessuna compressione. Un modello è stato eseguito il training usando `rxLinMod` sui dati di tre tabelle di dati diversi. Per tutte le tabelle sono state usate la stessa formula e la stessa query.

| Nome tabella            | Nome test       | numTasks | Durata media |
|-----------------------|-----------------|----------|--------------|
| *airlineWithIndex*    | NoCompression   | 1        | 5.6775       |
|                       | NoCompression - parallelo| 4        | 5.1775       |
| *airlineWithPageComp* | PageCompression | 1        | 6.7875       |
|                       | PageCompression - parallelo | 4        | 5.3225       |
| *airlineWithRowComp*  | RowCompression  | 1        | 6.1325       |
|                       | RowCompression - parallelo  | 4        | 5.2375       |

**Conclusioni**

Solo la compressione non sembra Guida in linea. In questo esempio, l'aumento della CPU per gestire la compressione compensa la diminuzione nel tempo i/o.

Tuttavia, quando il test viene eseguito in parallelo impostando *numTasks* su 4, il tempo medio diminuisce.

Per set di dati di dimensioni maggiori, l'effetto della compressione può essere più evidente. La compressione dipende dal set di dati e dai valori, pertanto potrebbe essere necessaria una sperimentazione per determinare l'effetto della compressione sul set di dati.

### <a name="effect-of-windows-power-plan-options"></a>Effetto di opzioni risparmio energia piano

In questo esperimento `rxLinMod` è stato usato con la tabella *airlineWithIntCol*. Il piano di risparmio energia di Windows è stato impostato su **bilanciato** o **ad alte prestazioni**. Per tutti i test, *numTasks* è stato impostato su 1. Il test è stato eseguito sei volte ed è stato eseguito due volte in entrambe le opzioni di risparmio energia per esaminare la variabilità dei risultati.

**Prestazioni elevate** power opzione:

| Nome test | Eseguire \# | Tempo trascorso | Durata media |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3,57 secondi |              |
|           | 2      | 3,45 secondi |              |
|           | 3      | 3,45 secondi |              |
|           | 4      | 3,55 secondi |              |
|           | 5      | 3,55 secondi |              |
|           | 6      | 3,45 secondi |              |
|           |        |              | 3.475        |
|           | 1      | 3,45 secondi |              |
|           | 2      | 3,53 secondi |              |
|           | 3      | 3,63 secondi |              |
|           | 4      | 3,49 secondi |              |
|           | 5      | 3,54 secondi |              |
|           | 6      | 3,47 secondi |              |
|           |        |              | 3.5075       |

Opzione per il risparmio di energia **Bilanciata**:

| Nome test | Eseguire \# | Tempo trascorso | Durata media |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3,89 secondi |              |
|           | 2      | 4,15 secondi |              |
|           | 3      | 3,77 secondi |              |
|           | 4      | 5 secondi    |              |
|           | 5      | 3,92 secondi |              |
|           | 6      | 3,8 secondi  |              |
|           |        |              | 3.91         |
|           | 1      | 3,82 secondi |              |
|           | 2      | 3,84 secondi |              |
|           | 3      | 3,86 secondi |              |
|           | 4      | 4,07 secondi |              |
|           | 5      | 4,86 secondi |              |
|           | 6      | 3,75 secondi |              |
|           |        |              | 3.88         |

**Conclusioni**

Il tempo di esecuzione è più veloce e coerente quando si utilizza Windows **ad alte prestazioni** risparmio di energia.

#### <a name="using-integer-vs-strings-in-formulas"></a>Utilizzo di tipo integer e stringhe nelle formule

Questo test valutata l'impatto della modifica del codice R per evitare un problema comune dei fattori di stringa. In particolare, un modello è stato eseguito il training usando `rxLinMod` usano due tabelle: nel primo, fattori vengono memorizzati come stringhe; nella seconda tabella, i fattori vengono archiviati come numeri interi.

+ Per il *airline* tabella la colonna [DayOfWeek] contiene le stringhe. Il _colInfo_ parametro viene utilizzato per specificare i livelli di fattore (lunedì, martedì,...)

+  Per il *airlineWithIndex* tabella [DayOfWeek] è un numero intero. Il _colInfo_ parametro non è stato specificato.

+ In entrambi i casi è stata usata la stessa formula: `ArrDelay ~ CRSDepTime + DayOfWeek`.

| Nome tabella          | Nome test   | Durata media |
|---------------------|-------------|--------------|
| *Airline*           | *FactorCol* | 10.72        |
| *airlineWithIntCol* | *IntCol*    | 3.4475       |

**Conclusioni**

Quando si utilizzano numeri interi anziché stringhe per fattori è un evidente vantaggio.

### <a name="avoiding-transformation-functions"></a>Evitare le funzioni di trasformazione

In questo test, un modello è stato eseguito il training usando `rxLinMod`, ma il codice è stato modificato tra le due esecuzioni:

+ La prima esecuzione, una funzione di trasformazione è stata applicata come parte della compilazione del modello. 
+ Nella seconda esecuzione, i valori delle funzionalità sono rese pre-calcolate e disponibili, in modo che nessuna funzione di trasformazione è stato richiesta.

| Nome test             | Durata media |
|-----------------------|--------------|
| WithTransformation    | 5.1675       |
| WithoutTransformation | 4.7          |

**Conclusioni**

I tempi di training sono più breve quando **non** utilizzando una funzione di trasformazione. In altre parole, il training del modello è stato eseguito più velocemente quando si utilizzano le colonne che sono pre-calcolate e mantenute nella tabella.

Il risparmio di spazio deve essere maggiore se sono presenti molti più trasformazioni e il set di dati sono molto grandi (\> M 100).

### <a name="using-columnar-store"></a>Uso di archivio colonne

Questo test valutata i vantaggi delle prestazioni dell'utilizzo di un archivio dati a colonne e un indice. Lo stesso modello è stato eseguito il training utilizzando `rxLinMod` e non le trasformazioni dei dati.

+ La prima esecuzione, la tabella di dati utilizzato un archivio di riga standard.
+ Nella seconda esecuzione, è stato usato un archivio colonne.

| Nome tabella         | Nome test | Durata media |
|--------------------|-----------|--------------|
| *airlineWithIndex* | RowStore  | 4.67         |
| *airlineColumnar*  | ColStore  | 4.555        |

**Conclusioni**

Le prestazioni sono migliori con l'archivio colonne rispetto a con l'archiviazione su righe standard. È possibile prevedere una differenza significativa delle prestazioni in set di dati più grande (\> M 100).

### <a name="effect-of-using-the-cube-parameter"></a>Effetto dell'uso del parametro del cubo

Lo scopo di questo test è stato per determinare se l'opzione in RevoScaleR per l'utilizzo di pre-calcolate **cubo** parametro può migliorare le prestazioni. Un modello è stato eseguito il training usando `rxLinMod`, utilizzando la formula:

```R
ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime
```

Nella tabella, i fattori *DayOfWeek* viene archiviato sotto forma di stringa.

| Nome test     | Parametro cube | numTasks | Durata media | Singola riga stima (ArrDelay_Pred) |
|---------------|----------------|----------|--------------|---------------------------------|
| CubeArgEffect | `cube = F`     | 1        | 91.0725      | 9.959204                        |
|               |                | 4        | 44.09        | 9.959204                        |
|               | `cube = T`     | 1        | 21.1125      | 9.959204                        |
|               |                | 4        | 8.08         | 9.959204                        |

**Conclusioni**

L'utilizzo dell'argomento di parametro del cubo chiaramente migliora le prestazioni.

### <a name="effect-of-changing-maxdepth-for-rxdtree-models"></a>Effetto della modifica maxDepth per i modelli rxDTree

In questo esercizio, il `rxDTree` algoritmo utilizzato per creare un modello nel *airlineColumnar* tabella. Per questo test *numTasks* è stato impostato su 4. Valori diversi per *maxDepth* utilizzati per illustrare la modifica di profondità dell'albero impatto della fase di esecuzione.

| Nome test       | maxDepth | Durata media |
|-----------------|----------|--------------|
| TreeDepthEffect | 1        | 10.1975      |
|                 | 2        | 13.2575      |
|                 | 4        | 19.27        |
|                 | 8        | 45.5775      |
|                 | 16       | 339.54       |

**Conclusioni**

Man mano che aumenta la profondità dell'albero, il numero totale di nodi aumenta in misura esponenziale. Il tempo trascorso per la creazione del modello anche aumentate in modo significativo.

### <a name="prediction-on-a-stored-model"></a>Stima su un modello archiviato

Lo scopo di questo test è stato per determinare l'impatto sulle prestazioni sul punteggio quando il modello con Training viene salvato in una tabella di SQL Server anziché generato come parte del codice attualmente in esecuzione. Per il punteggio, il modello archiviato viene caricato dal database e le stime vengono create utilizzando un frame di dati di una riga in memoria (contesto di calcolo locale).

I risultati del test mostrano il tempo necessario per salvare il modello e il tempo impiegato per caricare il modello e di stima.

| Nome tabella | Nome test | Tempo medio (per il training del modello) | Tempo di salvataggio/caricamento del modello|
|------------|------------|------------|------------|
| airline    | SaveModel| 21.59| 2.08|
| airline    | LoadModelAndPredict | | 2,09 (include il tempo per la stima) |

**Conclusioni**

Il caricamento di un modello con Training da una tabella è chiaramente un modo più veloce per eseguire stime. Si consiglia di evitare la creazione del modello e l'esecuzione di punteggio tutti nello stesso script.

## <a name="case-study-optimization-for-the-resume-matching-task"></a>Case study: ottimizzazione dell'attività di corrispondenza resume

È stato sviluppato il modello di corrispondenza resume esperto di dati Microsoft Ke Huang per testare le prestazioni del codice R in SQL Server e in questo modo pertanto i dati della Guida creare scalabili, gli esperti di soluzioni aziendali.

### <a name="methods"></a>Metodi

RevoScaleR sia MicrosoftML pacchetti sono stati utilizzati per il training di un modello predittivo in una soluzione di R complessa che coinvolgono grandi set di dati. Le query SQL e codice R sono identici in tutti i test. Test sono stati condotti su una singola macchina virtuale di Azure con SQL Server installato. L'autore quindi confrontata punteggio volte con e senza le ottimizzazioni seguenti fornite da SQL Server:

- Tabelle in memoria
- Soft-NUMA
- Resource Governor

Per valutare l'effetto di soft-NUMA nell'esecuzione dello script R, il team di analisi scientifica dei dati sottoposti a test la soluzione in una macchina virtuale Azure con 20 core fisici. In questi core fisici e quattro nodi soft-NUMA sono stati creati automaticamente, in modo che ogni nodo di contenuto in cinque Core.

Affinità della CPU è stata applicata per valutare l'impatto sui processi R lo scenario corrispondente resume. Quattro **pool di risorse SQL** e quattro **pool di risorse esterne** sono stati creati, e l'affinità della CPU è stato specificato per assicurarsi che lo stesso set di CPU potrebbe essere utilizzato in ogni nodo.

Ognuno dei pool di risorse è stato assegnato a un gruppo di carico di lavoro diversi, per ottimizzare l'utilizzo dell'hardware. Il motivo è che Soft-NUMA e affinità di CPU non è possibile dividere la memoria fisica in nodi NUMA fisici. Pertanto, per definizione tutti i nodi NUMA soft basati sullo stesso nodo NUMA fisico devono utilizzare memoria nello stesso blocco di memoria del sistema operativo. In altre parole, non è senza affinità del processore della memoria.

Per creare questa configurazione è stata usata la seguente procedura:

1. Ridurre la quantità di memoria allocata per impostazione predefinita di SQL Server.

2. Creare quattro nuovi pool per l'esecuzione di processi di R in parallelo.

3. Creare quattro gruppi di carico di lavoro in modo che ogni gruppo di carico di lavoro è associato a un pool di risorse.

4. Riavviare Resource Governor con i nuovi gruppi di carico di lavoro e le assegnazioni.

5. Creare una funzione di classificazione definita dall'utente (UDF) per assegnare varie attività sui gruppi del carico di lavoro diverso.

6. Aggiornare la configurazione di Resource Governor per utilizzare la funzione per i gruppi di carico di lavoro appropriato.

### <a name="results"></a>Risultati

La configurazione con prestazioni ottimali in corrispondenza resume studiare è indicato di seguito:

-   Quattro pool di risorse interno (per SQL Server)

-   Quattro pool di risorse esterne (per i processi di script esterni)

-   Ogni pool di risorse è associato a un gruppo di carico di lavoro specifico

-   Ogni pool di risorse viene assegnato a diverse CPU

-   Utilizzo massimo memoria interna (per SQL Server) = 30%

-   Quantità massima di memoria utilizzata dalle sessioni R = 70%

Per il modello di corrispondenza resume utilizzo dello script esterno è stato elevato e si sono verificati nessun altro database servizi motore di esecuzione. Di conseguenza, le risorse allocate per gli script esterni sono state portate a 70%, che ha dimostrato la migliore configurazione per le prestazioni di script.

Questa configurazione è stata arrivata tramite sperimentazioni con valori diversi. Se si utilizza hardware diverso o una soluzione diversa, è possibile che la configurazione ottimale potrebbe essere diversa. Sempre riuscire a individuare la migliore configurazione per il case!

Nella soluzione ottimizzata, classificate in meno di 8,5 secondi in un computer di 20 core 1.1 milioni di righe di dati (con 100 funzionalità). Le ottimizzazioni migliorate in modo significativo le prestazioni in termini di tempo di punteggio.

I risultati suggerisce che il **numero di funzionalità** aveva un impatto significativo sul tempo di assegnazione dei punteggi. Il miglioramento è stata ancora più importante quando altre funzionalità sono state utilizzate nel modello di stima.

È consigliabile leggere l'esercitazione di accompagnamento per una descrizione dettagliata e l'articolo di blog.

-   [Ottimizzazione suggerimenti e trucchi per machine learning in SQL Server](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

Molti utenti hanno indicato che vi sia una pausa di piccole dimensioni come il runtime di R (o Python) viene caricato per la prima volta. Per questo motivo, come descritto in questi test, il tempo per la prima esecuzione è spesso misurato ma eliminato in un secondo momento. Conseguente memorizzazione nella cache potrebbe comportare differenze rilevanti delle prestazioni tra il primo e secondo viene eseguito. È inoltre disponibile un overhead quando i dati vengono spostati tra SQL Server e runtime esterno, in particolare se i dati vengono passati tramite la rete, invece di essere caricato direttamente da SQL Server.

Per questi motivi, non è disponibile alcuna soluzione per ridurre il tempo di caricamento iniziale, come l'impatto sulle prestazioni varia notevolmente a seconda dell'attività. Ad esempio, vengono memorizzati nella cache per l'assegnazione dei punteggi in batch; a riga singola di conseguenza, le operazioni successive di punteggio sono molto più veloci e il modello né il runtime di R viene ricaricato al momento. È inoltre possibile utilizzare [punteggio native](../sql-native-scoring.md) per evitare il caricamento del runtime di R completamente.

Per il training di modelli di grandi dimensioni, o punteggio in batch di grandi dimensioni, l'overhead potrebbe essere minima rispetto i guadagni da evitare lo spostamento dei dati o dal flusso e l'elaborazione parallela. Vedere i blog recenti ed esempi per linee guida aggiuntive sulle prestazioni:

+ [Classificazione di prestito con SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/)
+ [Esperienze del cliente anticipata con R Services](https://blogs.msdn.microsoft.com/sqlcat/2016/06/16/early-customer-experiences-with-sql-server-r-services/)
+ [Uso di R per rilevare una frode pari a 1 milione di transazioni al secondo](http://blog.revolutionanalytics.com/2016/09/fraud-detection.html/)

## <a name="resources"></a>Risorse

Di seguito vengono forniti collegamenti a informazioni e strumenti di script utilizzati per lo sviluppo di questi test.

+ Test degli script e i collegamenti ai dati delle prestazioni: [campionare i dati e gli script per uno studio di ottimizzazioni di SQL Server](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)

+ Articolo che descrive la soluzione corrispondente resume: [suggerimento di ottimizzazione e consigli per SQL Server R Services](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

+ Script utilizzati nell'ottimizzazione di SQL per la soluzione corrispondente resume: [repository GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips)

### <a name="learn-about-windows-server-management"></a>Informazioni sulla gestione dei server Windows

+ [How to determine the appropriate page file size for 64-bit versions of Windows](https://support.microsoft.com/kb/2860880) (Come determinare le dimensioni appropriate del file di paging per le versioni a 64 bit di Windows)

+ [Informazioni sui NUMA](https://technet.microsoft.com/library/ms178144.aspx)

+ [Modo in cui SQL Server supporta NUMA](https://technet.microsoft.com/library/ms180954.aspx)

+ [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)

### <a name="learn-about-sql-server-optimizations"></a>Informazioni sull'ottimizzazione di SQL Server

+ [Riorganizzare e ricompilare gli indici](../../relational-databases\indexes\reorganize-and-rebuild-indexes.md)

+ [Introduzione alle tabelle con ottimizzazione per la memoria](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)

+ [Dimostrazione: Miglioramento delle prestazioni di OLTP in memoria](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp)

+ [Compressione dei dati](../../relational-databases/data-compression/data-compression.md)

+ [Abilitare la compressione in una tabella o un indice](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Disabilitare la compressione in una tabella o un indice](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

### <a name="learn-about-managing-sql-server"></a>Informazioni sulla gestione di SQL Server

+ [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)

+ [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)

+ [Introduzione a Resource Governor](https://technet.microsoft.com/library/bb895232.aspx)

+ [Governance delle risorse per R Services](resource-governance-for-r-services.md)

+ [Come creare un pool di risorse per R](how-to-create-a-resource-pool-for-r.md)

+ [Un esempio di configurazione di Resource Governor](https://blog.sqlauthority.com/2012/06/04/sql-server-simple-example-to-configure-resource-governor-introduction-to-resource-governor/)

### <a name="tools"></a>Strumenti

+ [Strumento di generazione del carico di archiviazione e di test delle prestazioni DISKSPD](https://github.com/microsoft/diskspd)

+ [Informazioni di riferimento sull'utilità FSUtil](https://technet.microsoft.com/library/cc753059.aspx)


## <a name="other-articles-in-this-series"></a>Altri articoli di questa serie

[Prestazioni di ottimizzazione per R: introduzione](sql-server-r-services-performance-tuning.md)

[Ottimizzazione delle prestazioni per R - configurazione SQL Server](sql-server-configuration-r-services.md)

[Ottimizzazione delle prestazioni per R - R ottimizzazione di codice e i dati](r-and-data-optimization-r-services.md)

[Ottimizzazione delle prestazioni - case study sulla risultati](performance-case-study-r-services.md)
