---
title: "Case Study di prestazioni (R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e902312-ad9c-480d-b82f-b871cd1052d9
caps.latest.revision: 8
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 6
---
# Case Study di prestazioni (R Services)

Per dimostrare l'effetto delle indicazioni fornite nelle sezioni precedenti, i test sono stati eseguiti utilizzando le tabelle dal set di dati aerea. 

## Test e dati di esempio

Esistono sei tabelle, con 10M righe in ogni tabella:

| Nome tabella | Description |
| ---------- | ----------- |
| _compagnia aerea_ | I dati convertiti dal file xdf originale utilizzando *rxDataStep*. |
| _airlineWithIntCol_ | *DayOfWeek* convertito in un valore integer anziché una stringa. Aggiunge inoltre un *rowNum* colonna. |
| _airlineWithIndex_ | Gli stessi dati di *airlineWithIntCol* tabella, ma con un singolo indice cluster tramite il *rowNum* colonna. |
| _airlineWithPageComp_ | Gli stessi dati di *airlineWithIndex* tabella, ma con attivata la compressione di pagina. Aggiunge inoltre due colonne, *CRSDepHour* e *ritardo*, che vengono calcolate da *CRSDepTime* e *ArrDelay*. |
| _airlineWithRowComp_ | Gli stessi dati di *airlineWithIndex* tabella, ma con abilitata la compressione di riga. Aggiunge inoltre due colonne, *CRSDepHour* e *ritardo* che vengono calcolate da *CRSDepTime* e *ArrDelay*. 
| _airlineColumnar_ | Un archivio colonne con un singolo indice cluster. Questa tabella viene popolata con i dati da un file csv puliti i file. |

Gli script utilizzati per eseguire i test descritti in questa sezione, nonché i collegamenti ai dati di esempio viene utilizzati per i test, sono disponibili in [https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning).

Ogni test è stato eseguito sei volte, l'ora della prima esecuzione (freddo eseguito) è stato eliminato. Per consentire l'outlier occasionale, è stato eliminato anche il tempo massimo per l'esecuzione di cinque rimanente. La media delle quattro esecuzioni rimanenti è stata eseguita per calcolare il tempo di esecuzione trascorso medio di ogni test. R garbage collection è stata causata prima di ogni test. Il valore di *rowsPerRead* per ogni test è stato impostato su 500000.

## Dimensioni dei dati quando si utilizza la compressione e una tabella di archivio colonne

Di seguito sono indicati i risultati dell'utilizzo di una tabella a colonne e la compressione per ridurre le dimensioni dei dati:

| Nome tabella | Righe | Riservato | Dati | index_size | Non utilizzato | % Salvataggio (riservato) |
| ---------- | ---- | -------- | ---- | ---------- | ------ | ------------------- |
| airlineWithIndex | 10000000 | 2978816 KB | 2972160 KB | 6128 KB | 528 KB | 0 |
| airlineWithPageComp | 10000000 | 625784 KB | 623744 KB | 1352 KB | 688 KB | 79% |
| airlineWithRowComp | 10000000 | 1262520 KB | 1258880 KB | 2552 KB | 1088 KB | 58% |
| airlineColumnar | 9999999 | 201992 KB | 201624 KB | n/d | 368 KB | 93% |

## Utilizzando Visual Studio di Integer. Stringa nella Formula

In questo esperimento, `rxLinMod` è stato utilizzato con la tabella aerea (dove *DayOfWeek* è una stringa) e *airlineWithIndex* (dove *DayOfWeek* è un numero intero). Nel primo caso, `colInfo` è stato utilizzato per specificare i livelli di fattore (`Monday`, `Tuesday`, ...). Per il secondo, `colInfo` non è stato specificato. In entrambi i casi, è stata utilizzata la stessa formula. La formula utilizzata è `ArrDelay ~ CRSDepTime + DayOfWeek`. I seguenti risultati mostra chiaramente il vantaggio dell'utilizzo della stringa di tipo integer vs:

| Nome tabella | Nome test | Tempo medio |
| ---------- | --------- | ------------ |
| compagnia aerea | FactorCol | 10.72 |
| airlineWithIntCol | IntCol | 3.4475 |

## Utilizzo della compressione

In questo esperimento, `rxLinMod` è stato utilizzato con il *airlineWithIndex*, *airlineWithPageComp*, e *airlineWithRowComp* tabelle. La stessa formula e la stessa query è stato utilizzato per tutte le tabelle. 

| Nome tabella | Nome test | numTasks | Tempo medio |
| ---------- | --------- | -------- | ------------ |
| airlineWithIndex | NoCompression | 1 | 5.6775 |
| &nbsp; | &nbsp; | 4 | 5.1775 |
| airlineWithPageComp | PageCompression | 1 | 6.7875 |
| &nbsp; | &nbsp; | 4 | 5.3225 |
| airlineWithRowComp | RowCompression | 1 | 6.1325 |
| &nbsp; | &nbsp; | 4 | 5.2375 |

Si noti che la compressione solo (*numTasks* impostata su 1) non sembra aiutare in questo esempio, poiché consente di compensare l'aumento della CPU per gestire la compressione per la riduzione nel tempo i/o. Tuttavia, quando il test viene eseguito in parallelo impostando *numTasks* a 4, riduce il tempo medio. Per set di dati più grande, l'effetto della compressione può essere più evidente. La compressione dipende il set di dati e valori, potrebbe essere necessario sperimentazione per determinare che la compressione effetto ha sul set di dati.

## Evitare di funzione di trasformazione

In questo esperimento, `rxLinMod` viene utilizzato con la tabella airlineWithIndex con e senza utilizzare una funzione di trasformazione.  

| Nome test | Tempo medio |
| --------- | ------------ |
| WithTransformation | 5.1675 |
| WithoutTransformation | 4.7 |

Si noti che il miglioramento nel tempo quando non si utilizza una funzione di trasformazione (tramite le colonne precalcolate e mantenute nella tabella). Il risparmio è molto maggiore se esistono molte altre trasformazioni e il set di dati è maggiore (> 100M).

## Utilizzo archivio colonne

In questo esperimento, `rxLinMod` è stato utilizzato con le tabelle airlineWithIndex e airlineColumnar senza utilizzare alcuna trasformazione. I risultati indicano che l'archivio colonne può risultare più efficace di archiviazione su righe. Esisterà una differenza significativa delle prestazioni nel set di dati maggiore (> 100 M).  

| Nome tabella | Nome test |Tempo medio |
| ---------- | --------- | ------------ |
| airlineWithIndex | RowStore | 4.67 |
| airlineColumnar | ColStore | 4.555 |

## Effetto del parametro del cubo

In questo esperimento, `rxLinMod` viene utilizzato con la tabella compagnia aerea in `DayOfWeek` viene archiviato come stringa. La formula utilizzata è `ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime`. I risultati mostrano chiaramente che l'utilizzo di `cube` parametro favorire le prestazioni. 

| Nome test | Parametro del cubo | numTasks | Tempo medio | Una riga stima (ArrDelay_Pred) |
| --------- | -------------- | -------- | ------------ | ------------------------------- |
| CubeArgEffect | `cube = F` | 1 | 91.0725 | 9.959204 |
| &nbsp; | &nbsp; | 4 | 44.09 | 9.959204 |
| &nbsp; | `cube = T` | 1 | 21.1125 | 9.959204 |
| &nbsp; | &nbsp; | 4 | 8.08 | 9.959204 |

## Effetto di maxDepth per rxDTree

In questo esperimento, `rxDTree` viene utilizzato con la tabella airlineColumnar. Valori diversi per *maxDepth* utilizzati per illustrare come ciò influisce sulla complessità della fase di esecuzione. Man mano che aumenta il livello di profondità, il numero totale di nodi aumenta in modo esponenziale e aumenta significativamente il tempo trascorso. Per questo test *numTasks* è stata impostata su 4.

| Nome test | maxDepth | Tempo medio |
| --------- | -------- | ------------ |
| TreeDepthEffect | 1 | 10.1975 |
| &nbsp; | 2 | 13.2575 |
| &nbsp; | 4 | 19.27 |
| &nbsp; | 8 | 45.5775 |
| &nbsp; | 16 | 339.54 |

## Effetto dell'opzione di risparmio energia

In questo esperimento, `rxLinMod` è stato utilizzato con la tabella airlineWithIntCol mentre Windows è stato impostato su Bilanciamento nonché a prestazioni elevate opzioni risparmio energia. Per tutti i test, *numTasks* è stata impostata su 1. Il test è stato eseguito 6 volte ed è stato eseguito due volte in entrambe le opzioni risparmio energia per illustrare la variabilità dei risultati quando si utilizza l'opzione energia bilanciato. I risultati mostrano che i numeri siano più coerenti e più veloce per l'opzione di risparmio energia ad alte prestazioni. 

__Prestazioni elevate__ power opzione:

| Nome test | Esegui # | Tempo trascorso | Tempo medio |
| --------- | ----- | ------------ | ------------ |
| IntCol | 1 | 3,57 secondi | &nbsp; |
| &nbsp; | 2 | 3,45 secondi | &nbsp; |
| &nbsp; | 3 | 3,45 secondi | &nbsp; |
| &nbsp; | 4 | 3.55 secondi | &nbsp; |
| &nbsp; | 5 | 3.55 secondi | &nbsp; |
| &nbsp; | 6 | 3,45 secondi | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.475 |
| &nbsp; | 1 | 3,45 secondi | &nbsp; |
| &nbsp; | 2 | 3.53 secondi | &nbsp; |
| &nbsp; | 3 | 3.63 secondi | &nbsp; |
| &nbsp; | 4 | 3.49 secondi | &nbsp; |
| &nbsp; | 5 | 3.54 secondi | &nbsp; |
| &nbsp; | 6 | 3.47 secondi | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.5075 |

__Bilanciato__ power opzione:

| Nome test | Esegui # | Tempo trascorso | Tempo medio |
| --------- | ----- | ------------ | ------------ |
| IntCol | 1 | 3.89 secondi | &nbsp; |
| &nbsp; | 2 | 4.15 secondi | &nbsp; |
| &nbsp; | 3 | 3.77 secondi | &nbsp; |
| &nbsp; | 4 | 5 secondi | &nbsp; |
| &nbsp; | 5 | 3.92 secondi | &nbsp; |
| &nbsp; | 6 | 3.8 secondi | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.91 |
| &nbsp; | 1 | 3,82 secondi | &nbsp; |
| &nbsp; | 2 | appena 3,84 secondi | &nbsp; |
| &nbsp; | 3 | 3.86 secondi | &nbsp; |
| &nbsp; | 4 | 4.07 secondi | &nbsp; |
| &nbsp; | 5 | 4.86 secondi | &nbsp; |
| &nbsp; | 6 | secondi 3,75 | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.88 |

## Stima utilizzando un modello archiviato

In questo esperimento, un modello viene creato e archiviato in un database. Il modello archiviato viene quindi caricato dal database e le stime create utilizzando un frame di dati di una riga in memoria (contesto del computer locale). Di seguito è riportato il tempo impiegato per eseguire il training, salvare, caricare il modello e stimare. Ciò è chiaramente un modo più veloce di stima. I risultati del test mostrano il tempo necessario per salvare il modello e il tempo impiegato per caricare il modello e stima. 

| Nome tabella | Nome test | Tempo medio (per il training del modello) | Tempo di salvataggio o caricamento modello |
| ---------- | --------- | ----- | ----- |
| compagnia aerea | SaveModel | 21.59 | 2.08 | 
| &nbsp; | LoadModelAndPredict | &nbsp; |  2.09 (include il tempo da stimare) |


## Risoluzione dei problemi di prestazioni

I test utilizzati in questa sezione offrono i file di output per ogni esecuzione utilizzando il *reportProgress* parametro, che viene passato per il test con valore `3`. L'output di console viene indirizzato a un file nella directory di output. Il file di output contiene informazioni riguardanti il tempo impiegato nel tempo di calcolo, i/o e tempo di transizione. Tali tempi sono utili per la diagnosi e risoluzione dei problemi. Questi tempi per le varie esecuzioni ideare il tempo medio in esecuzioni di elaborazione degli script di test. Questi script di test e le tecniche possono risultare utili nella risoluzione dei problemi problemi quando si utilizzano le funzioni analitiche rx il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Ad esempio, di seguito viene illustrato l'esempio di volte per l'esecuzione. Gli intervalli principali di interesse sono totale di lettura (i/o durata) e transizione sovraccarichi di esecuzione (nell'impostazione dei processi per il calcolo).

    Running IntCol Test. Using airlineWithIntCol table.  
        run  1  took  3.66  seconds  
        run  2  took  3.44  seconds  
        run  3  took  3.44  seconds  
        run  4  took  3.44  seconds  
        run  5  took  3.45  seconds  
        run  6  took  3.75  seconds  

    Average Time:  3.4425  
                    metric   time    pct 
    1           Total time 3.4425 100.00 
    2 Overall compute time 2.8512  82.82 
    3      Total read time 2.5378  73.72 
    4      Transition time 0.5913  17.18 
    5    Total non IO time 0.3134   9.10 
 
 ## Vedere anche
 [Guida di ottimizzazione delle prestazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 [Configurazione di SQL Server per i servizi di R](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [R e ottimizzazione dei dati](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)