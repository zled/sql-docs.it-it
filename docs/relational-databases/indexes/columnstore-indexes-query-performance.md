---
title: Indici columnstore - Prestazioni delle query | Microsoft Docs
ms.custom: 
ms.date: 01/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: indexes
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83acbcc4-c51e-439e-ac48-6d4048eba189
caps.latest.revision: "23"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: abf0e72140ff724671d5864461ad5f82ce9aed76
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="columnstore-indexes---query-performance"></a>Indici columnstore - Prestazioni delle query
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Indicazioni per ottenere prestazioni delle query elevate che è possibile raggiungere con la progettazione degli indici columnstore.    
    
 Gli indici columnstore possono raggiungere un miglioramento fino a 100 volte in termini di prestazioni per le analisi e i carichi di lavoro di data warehouse e fino a 10 volte in termini di compressione dei dati rispetto agli indici rowstore tradizionali.   Queste indicazioni di ottenere prestazioni delle query elevate che è possibile raggiungere con la progettazione degli indici columnstore.  Alla fine dell'articolo vengono fornite ulteriori spiegazioni sulle prestazioni di columnstore.    
    
## <a name="recommendations-for-improving-query-performance"></a>Indicazioni per migliorare le prestazioni delle query    
 Di seguito sono fornite alcune indicazioni per ottenere le prestazioni elevate che è possibile raggiungere con la progettazione degli indici columnstore.    
    
### <a name="1-organize-data-to-eliminate-more-rowgroups-from-a-full-table-scan"></a>1. Organizzare i dati per eliminare più rowgroup da una scansione di tabella completa    
    
-   **Usare l'ordine di inserimento.** In genere, in un data warehouse tradizionale i dati vengono inseriti in ordine temporale e le analisi vengono eseguite in una dimensione temporale, come nel caso delle analisi delle vendite per trimestre. Per questo tipo di carico di lavoro, l'eliminazione del rowgroup viene eseguita automaticamente. In SQL Server 2016 diversi rowgroup vengono ignorati durante l'elaborazione della query.    
    
-   **Usare l'indice rowstore cluster.** Se il predicato della query comune è in una colonna (ad esempio C1) che non è correlata all'ordine di inserimento della riga, è possibile creare un indice rowstore cluster nelle colonne C1 e quindi creare l'indice columstore cluster eliminando l'indice rowstore cluster. Se si crea l'indice columnstore cluster in modo esplicito usando DOP (grado di parallelismo) = 1, l'indice columnstore cluster risultante verrà ordinato perfettamente nella colonna C1. Se si specifica DOP=8, viene visualizzata una sovrapposizione di valori in 8 rowgroup.  Un caso comune di applicazione di questa strategia riguarda l'indice columnstore creato inizialmente con un set di dati di grandi dimensioni. Per un indice columnstore non cluster (NCCI), se la tabella rowstore di base include un indice cluster, le righe risultano già ordinate. In questo caso, l'indice columnstore non cluster risultante sarà ordinato automaticamente. È importante notare che l'indice columnstore non mantiene automaticamente l'ordine delle righe. Quando vengono inserite nuove righe o vengono aggiornate righe meno recenti, potrebbe essere necessario ripetere il processo a causa di un possibile deterioramento delle prestazioni delle query di analisi.    
    
-   **Usare il partizionamento delle tabelle.** È possibile partizionare l'indice columnstore e usare l'eliminazione delle partizioni per ridurre il numero di rowgroup da analizzare. Ad esempio, se si ha una tabella dei fatti in cui vengono archiviati gli acquisti eseguiti dai clienti e si usa un modello di query comune per cercare gli acquisti eseguiti trimestralmente da un determinato cliente, è possibile combinare l'ordine di inserimento con il partizionamento nella colonna del cliente. Ogni partizione contiene righe in ordine temporale per un determinato cliente.    
    
### <a name="2-plan-for-enough-memory-to-create-columnstore-indexes-in-parallel"></a>2. Pianificare una quantità di memoria sufficiente per creare indici columnstore in parallelo    
 Per impostazione predefinita, la creazione di un indice columnstore è un'operazione parallela, a meno che la memoria non sia vincolata. La creazione dell'indice in parallelo richiede più memoria rispetto alla creazione dell'indice in modo seriale. Se si dispone di un'ampia quantità di memoria, la creazione di un indice columnstore richiede un tempo di circa 1,5 volte superiore rispetto alla compilazione di un albero B nelle stesse colonne.    
    
 La memoria richiesta per la creazione di un indice columnstore dipende dal numero di colonne, dal numero di colonne stringa, dal grado di parallelismo e dalle caratteristiche dei dati. Ad esempio, se la tabella contiene meno di un milione di righe, SQL Server utilizzerà un solo thread per creare l'indice columnstore.    
    
 Se la tabella dispone di più di un milione di righe, ma SQL Server non ha a disposizione memoria sufficiente per creare l'indice utilizzando MAXDOP, SQL Server ridurrà automaticamente MAXDOP secondo le esigenze per adattarsi alla memoria disponibile.  In alcuni casi, è necessario ridurre il grado di parallelismo a uno per compilare l'indice nella memoria vincolata.    
    
 A partire da SQL Server 2016, la query viene eseguita sempre in modalità batch. Nelle versioni precedenti l'esecuzione batch viene usata solo quando DOP è maggiore di uno.    
    
## <a name="columnstore-performance-explained"></a>Spiegazione delle prestazioni columnstore    
 Gli indici columnstore raggiungono prestazioni delle query ottimali combinando l'elaborazione in modalità batch in memoria ad alta velocità con tecniche che riducono significativamente i requisiti per le operazioni I/O.  Poiché le query di analisi analizzano un numero elevato di righe, in genere sono associate alle operazioni I/O, quindi la riduzione di tali operazioni durante l'esecuzione delle query è fondamentale per la progettazione di indici columnstore.  Dopo la lettura dei dati in memoria, è molto importante ridurre il numero di operazioni in memoria.    
    
 Gli indici columnstore riducono le operazioni I/O e ottimizzano le operazioni in memoria grazie a un'elevata compressione dei dati, l'eliminazione di columnstore, l'eliminazione di rowgroup e l'elaborazione batch.    
    
### <a name="data-compression"></a>Compressione dati    
 Gli indici columnstore raggiungono una compressione dei dati 10 volte superiore a quella degli indici rowstore.  Ciò riduce significativamente le operazioni I/O richieste per eseguire query di analisi e, di conseguenza, migliora le prestazioni delle query.    
    
-   Gli indici columnstore leggono i dati compressi dal disco, quindi il numero di byte che deve essere letto nella memoria risulta ridotto.    
    
-   Gli indici columnstore archiviano i dati in formato compresso nella memoria. In questo modo diminuisce il numero di volte in cui gli stessi dati vengono letti in memoria e si riducono di conseguenza le operazioni I/O.  Ad esempio, con una compressione di 10 volte superiore, gli indici columnstore possono mantenere in memoria volumi di dati 10 volte maggiori di quelli archiviati in formato non compresso. La presenza di più dati nella memoria incrementa la probabilità che l'indice columnstore trovi i dati necessari nella memoria, senza ulteriori letture dal disco.    
    
-   Gli indici columnstore comprimono i dati per colonne anziché per righe. Questo consente di ottenere percentuali di compressione maggiori e di ridurre le dimensioni dei dati archiviati su disco. Ogni colonna viene compressa e archiviata in modo indipendente.  Tutti i dati all'interno di una colonna sono sempre dello tipo e tendono ad avere valori simili. Le tecniche di compressione dei dati sono molto efficaci per raggiungere percentuali di compressione maggiori quando i valori sono simili.    
    
-   Ad esempio, se una tabella dei fatti archivia gli indirizzi dei clienti e include una colonna per il paese, il numero totale di valori possibili è inferiore a 200.  Alcuni di questi valori saranno ripetuti più volte.  Se la tabella dei fatti contiene 100 milioni di righe, la colonna per il paese verrà compressa facilmente e non richiederà molto spazio di archiviazione. La compressione riga per riga non riesce a sfruttare appieno la somiglianza dei valori di colonna e userà più byte per comprimere i valori nella colonna per il paese.    
    
### <a name="column-elimination"></a>Eliminazione di colonne    
 Gli indici columnstore non leggono le colonne non rilevanti ai fini della query. Questa capacità, denominata eliminazione di colonne, riduce ulteriormente le operazioni I/O per l'esecuzione delle query e, di conseguenza, migliora le prestazioni delle query.    
    
-   L'eliminazione di colonne è possibile perché i dati sono organizzati e compressi colonna per colonna.   Al contrario, quando i dati sono archiviati riga per riga, i valori della colonna in ogni riga vengono archiviati fisicamente insieme e non possono essere separati facilmente. Query Processor deve leggere un'intera riga per recuperare specifici valori della colonna, aumentando così le operazioni I/O a causa delle letture superflue dei dati aggiuntivi in memoria.    
    
-   Ad esempio, se una tabella contiene 50 colonne e la query ne usa solo 5, l'indice columnstore recupera solo le 5 colonne rilevanti dal disco. Non legge i dati delle altre 45 colonne. In questo modo, le operazioni I/O vengono ridotte di un altro 90%, presupponendo che tutte le colonne abbiano dimensioni simili.  Se gli stessi dati vengono archiviati in un rowstore, Query Processor deve leggere le altre 45 colonne.    
    
### <a name="rowgroup-elimination"></a>Eliminazione di rowgroup    
 Per le scansioni di tabelle complete, un'alta percentuale di dati spesso non corrisponde ai criteri del predicato della query. Usando i metadati, l'indice columnstore può ignorare la lettura nei rowgroup che non contengono dati necessari per il risultato della query, senza eseguire operazioni I/O.  Questa capacità, denominata eliminazione di rowgroup, riduce le operazioni I/O per le scansioni di tabelle complete e, di conseguenza, migliora le prestazioni delle query.    
    
 **Quando è necessario che un indice columnstore esegua una scansione di tabella completa?**    
    
 A partire da SQL Server 2016, è possibile creare uno o più indici BTree non cluster normali in un indice columnstore cluster con una procedura analoga a quella per un heap rowstore.  Gli indici BTree non cluster possono velocizzare una query con un predicato di uguaglianza o un predicato con un intervallo di valori limitato.  Per i predicati più complessi, Query Optimizer potrebbe optare per una scansione di tabella completa. Senza la possibilità di ignorare i rowgroup, una scansione di tabella completa richiederebbe molto tempo, in particolare per tabelle di grandi dimensioni.    
    
 **In che occasioni una query di analisi trae vantaggio dall'eliminazione di rowgroup per una scansione di tabella completa?**    
    
 Ad esempio, un'azienda di vendita al dettaglio ha modellato i dati di vendita usando una tabella dei fatti con un indice columnstore cluster. Per ogni nuova vendita vengono archiviati diversi attributi della transazione inclusa la data della vendita. È interessante notare che, anche se gli indici columnstore non garantiscono un ordinamento, le righe in questa tabella vengono caricate ordinate per data.   Questa tabella si espande nel tempo. Anche se l'azienda di vendita al dettaglio conserva i dati di vendita degli ultimi 10 anni, per una query di analisi potrebbe essere necessario solo il calcolo di un'aggregazione dell'ultimo trimestre. Gli indici columnstore possono eliminare l'accesso ai dati dei 39 trimestri precedenti semplicemente esaminando i metadati per la colonna della data.  Si tratta di un'ulteriore riduzione del 97% della quantità di dati letti in memoria ed elaborati.    
    
 **Quali rowgroup vengono ignorati in una scansione di tabella completa?**    
    
 Per determinare quali rowgroup eliminare, l'indice columnstore usa i metadati per archiviare i valori minimi e massimi di ogni segmento di colonna per ogni rowgroup. Se nessuno degli intervalli dei segmenti di colonna soddisfa i criteri del predicato della query, l'intero rowgroup viene ignorato senza eseguire alcuna operazione I/O. Questo procedimento funziona perché in genere i dati vengono caricati con un ordinamento e, anche se l'ordinamento delle righe non è sempre garantito, i valori dei dati simili spesso si trovano all'interno dello stesso rowgroup o in un rowgroup adiacente.    
    
 Per altri dettagli sui rowgroup, vedere Guida agli indici columnstore    
    
### <a name="batch-mode-execution"></a>Esecuzione in modalità batch    
 L'esecuzione in modalità batch indica l'elaborazione congiunta di un set di righe, generalmente non più di 900, per migliorare l'efficienza di esecuzione. Ad esempio, la query  `Select SUM (Sales)from SalesData` aggrega le vendite totali della tabella SalesData.    Nell'esecuzione in modalità batch, il motore di esecuzione delle query calcola l'aggregato in gruppi di 900 valori.  In questo modo, invece di pagare il costo delle singole righe, i metadati, i costi di accesso e altri tipi di costi generali vengono suddivisi su tutte le righe in un batch, riducendo notevolmente il percorso del codice.  L'elaborazione in modalità batch funziona sui dati compressi, quando disponibili, ed elimina alcuni degli operatori di scambio usati dall'elaborazione in modalità riga.  Questo velocizza l'esecuzione delle query di analisi per ordini di grandezza.    
    
 Non tutti gli operatori di esecuzione delle query possono essere eseguiti in modalità batch. Ad esempio, le operazioni DML di inserimento, eliminazione o aggiornamento vengono eseguite una riga alla volta. Gli operatori in modalità batch fanno riferimento agli operatori per velocizzare le prestazioni delle query in operazioni di analisi, join, aggregazione, ordinamento e così via.  Poiché l'indice columnstore è stato introdotto in SQL Server 2012, si sta lavorando costantemente per aumentare gli operatori che possono essere eseguiti in modalità batch. La tabella seguente illustra gli operatori eseguiti in modalità batch in base alla versione del prodotto.    
    
|Operatori in modalità batch|Quando si usa?|SQL Server 2012|SQL Server 2014|SQL Server 2016 e database SQL¹|Commenti|    
|---------------------------|------------------------|---------------------|---------------------|---------------------------------------|--------------|    
|Operazioni DML (insert, delete, update, merge)||no|no|no|DML non è un'operazione in modalità batch perché non è parallela. Anche quando si abilita l'elaborazione batch in modalità seriale e si consente l'elaborazione in modalità batch di DML, non si rilevano vantaggi significativi.|    
|Index Scan columnstore|SCAN|ND|sì|sì|Per gli indici columnstore è possibile eseguire il push del predicato nel nodo SCAN.|    
|Index Scan (nonclustered) columnstore|SCAN|sì|sì|sì|sì|    
|Index Seek||ND|ND|no|L'operazione di ricerca viene eseguita con un indice BTree non cluster in modalità riga.|    
|Compute Scalar|Espressione che restituisce un valore scalare.|sì|sì|sì|Esistono alcune restrizioni sul tipo di dati. Questo vale per tutti gli operatori in modalità batch.|    
|Concatenation|UNION e UNION ALL|no|sì|sì||    
|filter|Applicare i predicati|sì|sì|sì||    
|Hash Match|Funzioni di aggregazione basate su hash, outer hash join, right hash join, left hash join, right inner join, left inner join|sì|sì|sì|Restrizioni per l'aggregazione: nessun valore min e max per le stringhe. Le funzioni di aggregazione disponibili sono sum/count/avg/min/max.<br />Restrizioni per il join: nessun join con tipo non corrispondente per i tipi non integer.|    
|Merge Join||no|no|no||    
|Query multithreading||sì|sì|sì||    
|Nested Loops||no|no|no||    
|Query a thread singolo in esecuzione in MAXDOP 1||no|no|sì||    
|Query a thread singolo con un piano di query seriale||no|no|sì||    
|Sort|Ordinare per clausola in SCAN con l'indice columnstore.|no|no|sì||    
|Top Sort||no|no|sì||    
|Window Aggregates||ND|ND|sì|Nuovo operatore in SQL Server 2016.|    
    
 ¹Si applica a SQL Server 2016, database SQL V12 Premium Edition e SQL Data Warehouse    
    
### <a name="aggregate-pushdown"></a>Distribuzione dell'aggregazione    
 Un percorso di esecuzione normale per il calcolo di aggregazione che consente di recuperare le righe idonee dal nodo SCAN e aggregare i valori in modalità batch.  Questo metodo offre buone prestazioni, ma con SQL Server 2016 è possibile eseguire il push dell'operazione di aggregazione nel nodo SCAN per migliorare le prestazioni di calcolo di aggregazione per ordini di grandezza durante l'esecuzione in modalità batch, purché vengano soddisfatte le condizioni seguenti 
 
-    Le aggregazioni sono MIN, MAX, SUM, COUNT e COUNT(*). 
-  L'operatore di aggregazione deve essere sopra il nodo SCAN o il nodo SCAN con GROUP BY.
-  L'aggregazione non è un'aggregazione distinta.
-  La colonna di aggregazione non è una colonna stringa.
-  La colonna di aggregazione non è una colonna virtuale. 
-  Il tipo di dati di input e di output deve essere uno dei seguenti e deve rientrare nei 64 bit:
    -  tiny int, int, big int, small int, bit
    -  small money, money, decimale e numerico con precisione <= 18
    -  small date, date, datetime, datetime2, time
    
 La distribuzione dell'aggregazione viene ulteriormente accelerata da un'aggregazione efficiente dei dati compressi/codificati durante un'esecuzione di facile integrazione con la cache e sfruttando SIMD    
    
 ![aggregate pushdown](../../relational-databases/indexes/media/aggregate-pushdown.jpg "aggregate pushdown")    
    
 Ad esempio, la distribuzione dell'aggregazione viene eseguita in entrambe le query seguenti    
    
```    
    
SELECT  productkey, SUM(TotalProductCost)    
FROM FactResellerSalesXL_CCI    
GROUP BY productkey    
    
SELECT  SUM(TotalProductCost)    
FROM FactResellerSalesXL_CCI    
```    
    
### <a name="string-predicate-pushdown"></a>Distribuzione del predicato stringa    
 Motivazione: quando si progetta uno schema del data warehouse, la modellazione dello schema consigliata consiste nell'usare uno schema star o snowflake costituito da una o più tabelle dei fatti e da più tabelle delle dimensioni. La [tabella dei fatti](https://en.wikipedia.org/wiki/Fact_table) archivia le misure o le transazioni aziendali e la [tabella delle dimensioni](https://en.wikipedia.org/wiki/Dimension_table) archivia le dimensioni di cui analizzare i fatti.    
    
 Ad esempio, un fatto può essere un record che rappresenta la vendita di un certo prodotto in un'area specifica, mentre la dimensione rappresenta un set di regioni, prodotti e così via. Le tabelle dei fatti e delle dimensioni sono connesse con una relazione di chiave primaria/esterna. Le query di analisi più diffuse creano un join di una o più tabelle delle dimensioni con la tabella dei fatti.    
    
 Si prendano in considerazione i prodotti di una tabella delle dimensioni. Una chiave primaria tipica è ProductCode, generalmente rappresentata con un tipo di dati stringa.  Per le prestazioni delle query, è consigliabile creare una chiave surrogata, in genere una colonna di tipo integer, per fare riferimento alla riga nella tabella delle dimensioni dalla tabella dei fatti.    
    
 L'indice columnstore esegue in modo efficace le query di analisi con join/predicati che includono chiavi di tipo numerico o integer.   Tuttavia, in molti carichi di lavoro del cliente vengono usate colonne basate su stringhe per il collegamento delle tabelle dei fatti e delle dimensioni e le prestazioni delle query con l'indice columnstore si sono rivelate non altrettanto soddisfacenti.    SQL Server 2016 migliora in modo significativo le prestazioni delle query di analisi con le colonne basate su stringhe grazie alla distribuzione dei predicati con colonne di tipo stringa nel nodo SCAN    
    
 La distribuzione del predicato stringa sfrutta il dizionario primario o secondario creato per le colonne per migliorare le prestazioni delle query.  Ad esempio, prendere in considerazione il segmento di colonna stringa all'interno di un rowgroup costituito da 100 valori stringa distinti. Ipotizzando la presenza di un milione di righe, la media di riferimenti a ogni singolo valore stringa è di 10.000 volte.    
    
 Con la distribuzione del predicato stringa, l'esecuzione della query calcola il predicato in base ai valori nel dizionario e, se è qualificato, tutte le righe che fanno riferimento al valore del dizionario risultano automaticamente qualificate.   Ciò migliora le prestazioni in due modi. In primo luogo, vengono restituite solo le righe qualificate, riducendo il numero di righe da trasmettere dal nodo SCAN. In secondo luogo, il numero dei confronti di stringhe viene notevolmente ridotto. In questo esempio sono necessari solo 100 confronti di stringhe invece di un milione.     Esistono alcune limitazioni, come descritto di seguito    
    
-   Non è consentita la distribuzione del predicato stringa per i rowgroup delta. Non esiste un dizionario per le colonne nei rowgroup delta    
    
-   Non è consentita la distribuzione del predicato stringa se il dizionario supera le 64.000 voci    
    
-   Le espressioni che restituiscono NULL non sono supportate    
    
## <a name="see-also"></a>Vedere anche    
 Guida agli indici columnstore     
 Caricamento dati di indici columnstore     
 Riepilogo delle funzionalità con versione degli indici columnstore     
 [Prestazioni delle query per gli indici columnstore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)     
 [Introduzione a columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)     
 Indici columnstore per il data warehousing     
 [Deframmentazione degli indici columnstore](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)    
    
  
