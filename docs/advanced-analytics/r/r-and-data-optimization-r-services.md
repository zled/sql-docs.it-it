---
title: Prestazioni per R Services - ottimizzazione dati | Documenti Microsoft
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6104878-ed19-47a7-ac37-21e4d6e2a1af
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 265f66c0dfba28e1f3c35fa560098b3a2d13cb0c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="performance-for-r-services---data-optimization"></a>Prestazioni per R Services - ottimizzazione dati

In questo articolo è il terzo in una serie che descrive l'ottimizzazione delle prestazioni per R Services in base alle due case study. In questo articolo descrive le ottimizzazioni delle prestazioni per R o Python script in esecuzione in SQL Server. Vengono inoltre descritti i metodi che è possibile utilizzare per aggiornare il codice R, per migliorare le prestazioni e per evitare problemi noti.

## <a name="choosing-a-compute-context"></a>Scelta di un contesto di calcolo

In SQL Server 2016 e 2017, è possibile utilizzare il **locale** o **SQL** contesto di calcolo durante l'esecuzione di script R o Python.

Quando si utilizza il **locale** contesto di calcolo, di analisi viene eseguita nel computer in uso e non nel server. Pertanto, se si ricevono dati da SQL Server da utilizzare nel codice, devono recuperare i dati attraverso la rete. Il calo di prestazioni riscontrato per questo trasferimento in rete dipende dalle dimensioni dei dati trasferiti, dalla velocità della rete e dagli eventuali altri trasferimenti in rete che si verificano nello stesso momento.

Quando si utilizza il **contesto di calcolo di SQL Server**, il codice viene eseguito nel server. Se si ricevono dati da SQL Server, i dati devono essere locali nel server che esegue l'analisi e pertanto non è stato introdotto alcun overhead di rete. Se si desidera importare dati da altre origini, provare a disposizione in anticipo ETL.

Quando si usano set di dati di grandi dimensioni, è consigliabile usare sempre il contesto di calcolo SQL.

## <a name="factors"></a>Fattori

Il linguaggio R è il concetto di "fattori", che sono variabili speciali per i dati categorici. Gli esperti di dati spesso utilizzano variabili di fattore in loro formula, perché le variabili di categoria come fattori di gestione garantisce che i dati viene elaborato correttamente da funzioni di machine learning. Per ulteriori informazioni, vedere [R per dummy: variabili Factor] (http://www.dummies.com/programming/r/how-to-look-at-the-structure-of-a-factor-in-r/).

Per impostazione predefinita, le variabili di fattore possono essere convertite da stringhe in numeri interi e viceversa nuovamente per l'archiviazione o l'elaborazione. R `data.frame` funzione gestisce tutte le stringhe come variabili fattore, a meno che l'argomento *stringsAsFactors* è impostato su **False**. Ciò significa che le stringhe vengono automaticamente convertito in un intero per l'elaborazione viene quindi eseguito il mapping alla stringa originale.

Se i dati di origine per i fattori sono archiviati come valore integer, le prestazioni possono risultare compromesse perché R converte i numeri interi fattore in stringhe in fase di esecuzione e quindi esegue il proprio conversione interna di stringa a valore intero.

Per evitare tali conversioni in fase di esecuzione, è consigliabile archiviare i valori come numeri interi nella tabella di SQL Server e l'utilizzo di _colInfo_ argomento per specificare i livelli per la colonna utilizzata come fattore. La maggior parte degli oggetti di origine dati in RevoScaleR prendono il parametro _colInfo_. Utilizzare questo parametro per denominare le variabili utilizzate dall'origine dei dati, specificare il tipo e definire i livelli di variabili o le trasformazioni per i valori della colonna.

Ad esempio, la chiamata di funzione R seguente ottiene i valori integer a 1, 2 e 3 da una tabella, ma viene eseguito il mapping di valori a un fattore con livelli di "apple", "arancione" e "banana".

```R
c("fruit" = c(type = "factor", levels=as.character(c(1:3)), newLevels=c("apple", "orange", "banana")))
```

Quando la colonna di origine contiene le stringhe, è sempre più efficiente per specificare i livelli preventivamente utilizzando il _colInfo_ parametro. Ad esempio, il seguente codice R considera le stringhe come fattori come vengono letti.

```R
c("fruit" = c(type = "factor", levels= c("apple", "orange", "banana")))
```

Se è presente alcuna differenza semantica la generazione del modello, il secondo approccio può comportare prestazioni migliori.

## <a name="data-transformations"></a>Trasformazioni di dati

I data scientist usano spesso le funzioni di trasformazione scritte in R nell'ambito dell'analisi. La funzione di trasformazione viene applicata a ogni riga recuperata dalla tabella. In SQL Server, tali trasformazioni vengono applicate a tutte le righe recuperate in un batch, che richiede la comunicazione tra l'interprete R e il motore analitica. Per eseguire la trasformazione, i dati vengono spostati da SQL al motore di analisi e quindi al processo dell'interprete R e viceversa.

Per questo motivo, l'utilizzo di trasformazioni come parte del codice R può avere un notevole effetto negativo sulle prestazioni dell'algoritmo, a seconda della quantità di dati coinvolti.

È più efficiente disporre di tutte le colonne necessarie nella tabella o vista prima di eseguire analisi ed evitare di trasformazioni durante il calcolo. Se non è possibile aggiungere altre colonne alle tabelle esistenti, è consigliabile creare un'altra tabella o vista con le colonne trasformate e usare una query appropriata per recuperare i dati.

## <a name="batch-row-reads"></a>Legge la riga batch

Se si utilizza un'origine dati di SQL Server (`RxSqlServerData`) nel codice, è consigliabile provare a usare il parametro _rowsPerRead_ per specificare le dimensioni di batch. Questo parametro definisce il numero di righe che vengono eseguite query e quindi inviati allo script esterno per l'elaborazione. In fase di esecuzione, l'algoritmo rileva solo il numero specificato di righe in ogni batch.

La possibilità di controllare la quantità di dati che viene elaborati in un momento consentono di risolvere o evitare problemi. Ad esempio, se il set di dati di input è molto ampia (contiene molte colonne), o se il set di dati dispone di alcune colonne di grandi dimensioni (ad esempio testo libero), è possibile ridurre le dimensioni del batch per evitare il paging dati dalla memoria.

Per impostazione predefinita, il valore di questo parametro è impostato su 50000, per garantire prestazioni ragionevole anche su computer con memoria insufficiente. Se il server è disponibile memoria sufficiente, aumentare questo valore su 500.000 o persino milioni di dollari può offrire prestazioni migliori, in particolare per tabelle di grandi dimensioni.

I vantaggi dell'aumento delle dimensioni di batch diventa evidenti in un set di dati di grandi dimensioni in un'attività che è possibile eseguire in più processi. Tuttavia, aumenta questo valore non produce sempre risultati ottimali. Si consiglia di sperimentare i dati e l'algoritmo per determinare il valore ottimale.

## <a name="parallel-processing"></a>Elaborazione parallela

Per migliorare le prestazioni di **rx** funzioni analitiche, è possibile sfruttare la possibilità di SQL Server per eseguire attività in parallelo utilizzando core disponibili nel computer del server.

Esistono due modi per ottenere la parallelizzazione di R in SQL Server:

-   **Utilizzare \@parallelo.** Quando si usa la stored procedure `sp_execute_external_script` per eseguire uno script R, impostare il parametro `@parallel` su `1`. Questo è il metodo migliore se lo script R non **non** usare funzioni RevoScaleR, che hanno altri meccanismi per l'elaborazione. Se lo script utilizza le funzioni RevoScaleR (in genere precedute da "rx"), l'elaborazione parallela viene eseguita automaticamente e non è necessario impostare in modo esplicito `@parallel` a `1`.

    Se lo script R può essere eseguito in parallelo e se la query SQL può essere eseguito in parallelo, il motore di database crea più processi paralleli. Il numero massimo di processi che possono essere create è uguale al **massimo grado di parallelismo** impostazione (MAXDOP) per l'istanza. Tutti i processi quindi eseguire lo stesso script, ma solo una parte dei dati di ricezione.
    
    Questo metodo non è pertanto utile con gli script che devono visualizzare tutti i dati, ad esempio quando un modello di training. Tuttavia, è utile quando si eseguono attività come la stima in batch in parallelo. Per ulteriori informazioni sull'utilizzo di parallelismo con `sp_execute_external_script`, vedere il **avanzate suggerimenti: l'elaborazione parallela** sezione [utilizzando codice R in Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

-   **Utilizzare numTasks = 1.** Quando si utilizza **rx** funzioni in un contesto di calcolo di SQL Server, impostare il valore della _numTasks_ parametro per il numero di processi che si desidera creare. Il numero di processi creati non può mai essere più **MAXDOP**; tuttavia, il numero effettivo di processi creati è determinato dal motore di database e può essere minore di è richiesto.

    Se lo script R può essere eseguito in parallelo e se la query SQL può essere eseguito in parallelo, SQL Server crea più processi paralleli quando si esegue le funzioni di ricezione. Il numero effettivo di processi creati dipende da diversi fattori, ad esempio la governance delle risorse, l'utilizzo corrente di risorse e le altre sessioni e il piano di esecuzione di query per la query utilizzata con lo script R.

## <a name="query-parallelization"></a>Parallelizzazione delle query

In Microsoft R, è possibile utilizzare con le origini dati di SQL Server, la definizione dei dati come un oggetto di origine dati RxSqlServerData.

Crea un'origine dati basata su un'intera tabella o vista:

```R
RxSqlServerData(table= "airline", connectionString = sqlConnString)
```

Crea un'origine dati basata su una query SQL:

```R
RxSqlServerData(sqlQuery= "SELECT [ArrDelay],[CRSDepTime],[DayOfWeek] FROM  airlineWithIndex WHERE rowNum <= 100000", connectionString = sqlConnString)
```

> [!NOTE]
> Se viene specificata una tabella nell'origine dati anziché una query, R Services utilizza l'approccio euristico interno per determinare le colonne necessarie per recuperare dalla tabella. Tuttavia, questo approccio è improbabile che l'esecuzione in parallelo.

Per garantire che i dati possono essere analizzati in parallelo, la query utilizzata per recuperare i dati debba essere racchiuse in modo che il motore di database può creare un piano di query parallele. Se il codice o l'algoritmo utilizza grandi volumi di dati, assicurarsi che la query in base a `RxSqlServerData` è ottimizzato per l'esecuzione parallela. Una query che non implica un piano di esecuzione parallela può comportare un singolo processo per il calcolo.

Se si desidera lavorare con grandi set di dati, è possibile utilizzare Management Studio o un altro SQL query analyzer prima di eseguire codice R, per analizzare il piano di esecuzione. Quindi, eseguire le procedure consigliate per migliorare le prestazioni della query. Ad esempio, un indice mancante in una tabella può influire sul tempo impiegato per eseguire una query. Per ulteriori informazioni, vedere [monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md).

Un altro errore comune che può influire sulle prestazioni è che una query recupera più colonne rispetto a quelle necessarie. Ad esempio, se una formula si basa su tre colonne, ma la tabella di origine contiene 30 colonne, ma lo spostamento dati inutilmente.

 + Evitare di utilizzare `SELECT *`!
 + Richiedere del tempo per esaminare le colonne nel set di dati e identificare solo quelli necessari per l'analisi
 + Rimuovere le query di tutte le colonne che contengono i tipi di dati che non sono compatibili con il codice R, ad esempio GUID e ROWGUID
 + Verifica della data non supportato e formati di ora
 + Invece di caricare una tabella, creare una visualizzazione che consente di selezionare determinati valori o esegue il cast di colonne per evitare errori di conversione

## <a name="optimizing-the-machine-learning-algorithm"></a>Ottimizzare l'algoritmo di apprendimento automatico

In questa sezione fornisce suggerimenti e le risorse che sono specifiche per RevoScaleR e altre opzioni disponibili in Microsoft R.

> [!TIP]
> Una discussione generale di ottimizzazione di R non rientra nell'ambito di questo articolo. Tuttavia, se è necessario rendere il codice più velocemente, è consigliabile l'articolo diffuso, [di R nel](http://www.burns-stat.com/pages/Tutor/R_inferno.pdf). Vengono illustrati i costrutti di programmazione in R e alcuni errori comuni nella lingua vivido e i dettagli e vengono forniti molti esempi specifici di R tecniche di programmazione.

### <a name="optimizations-for-revoscaler"></a>Ottimizzazioni per RevoScaleR

Molti algoritmi RevoScaleR supportano i parametri per controllare la modalità di generazione del modello con training. Mentre l'accuratezza e la correttezza del modello è importante, le prestazioni dell'algoritmo potrebbero essere altrettanto importante. Per ottenere il giusto equilibrio tra i tempi di training e l'accuratezza, è possibile modificare i parametri per aumentare la velocità di calcolo e in molti casi, migliorare le prestazioni senza ridurre la precisione o la correttezza.

+ [rxDTree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)

    `rxDTree`supporta il `maxDepth` parametro, che controlla la profondità dell'albero delle decisioni. Come `maxDepth` viene aumentato, le prestazioni possono ridursi, pertanto è importante analizzare i vantaggi di aumentare la profondità e incide negativamente sulle prestazioni.

    È inoltre possibile controllare il bilanciamento tra precisione complessità e la stima di tempo modificando i parametri, ad esempio `maxNumBins`, `maxDepth`, `maxComplete`, e `maxSurrogate`. L'aumento della profondità oltre 10 o 15 può rendere il calcolo molto dispendioso.

+ [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)

    Provare a utilizzare il `cube` argomento se la variabile dipendente prima della formula è una variabile di fattore.
    
    Quando `cube` è impostato su `TRUE`, la regressione viene eseguita utilizzando un partizionata inverso, che potrebbe essere più veloci e utilizzare meno memoria di calcolo di regressione standard. Se la formula contiene un numero elevato di variabili, il miglioramento delle prestazioni può essere significativo.

+ [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)

    Utilizzare il `cube` argomento se la variabile dipendente prima è una variabile di fattore.
    
    Quando `cube` è impostato su `TRUE`, l'algoritmo utilizza un'inverso partizionata, che potrebbe essere più veloci e utilizzare meno memoria. Se la formula contiene un numero elevato di variabili, il miglioramento delle prestazioni può essere significativo.

Per ulteriori informazioni sull'ottimizzazione di RevoScaleR, vedere i seguenti articoli:

+ Articolo del supporto tecnico: [le opzioni per rxDForest e rxDTree l'ottimizzazione delle prestazioni](https://support.microsoft.com/kb/3104235)

+ Metodi per il controllo del modello di base in un modello di struttura ad albero con Boosting: [stima dei modelli utilizzando stocastico Boosting dei gradienti](https://docs.microsoft.com/r-server/r/how-to-revoscaler-boosting)

+ Panoramica di come RevoScaleR Sposta ed elaborazione dei dati: [ScaleR di scrittura di algoritmi personalizzati di suddivisione in blocchi](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ Modello di programmazione per RevoScaleR: [gestendo i thread in RevoScaleR](https://docs.microsoft.com/r-server/r/how-to-developer-manage-threads)

+ Funzione di riferimento per [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

+ Funzione di riferimento per [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)

### <a name="use-microsoftml"></a>Utilizzare MicrosoftML

È inoltre consigliabile che cerca nel nuovo **MicrosoftML** pacchetto, che fornisce gli algoritmi di apprendimento scalabile di macchine che è possono utilizzare le trasformazioni fornite da RevoScaleR e i contesti di calcolo.

+ [Introduzione a MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

+ [Come scegliere un algoritmo MicrosoftML](https://docs.microsoft.com/r-server/r/how-to-choose-microsoftml-algorithms-cheatsheet)

### <a name="operationalize-a-solution-using-microsoft-r-server"></a>Utilizzare una soluzione utilizzando Microsoft R Server

Se lo scenario prevede una rapida stima utilizzando un modello archiviato o integrazione di apprendimento in un'applicazione, è possibile utilizzare il [rendere operativo il](https://docs.microsoft.com/r-server/what-is-operationalization) funzionalità di Microsoft R Server (precedentemente noto come DeployR).

+ Come un **esperto di dati**, utilizzare il [mrsdeploy pacchetto](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package) condividere il codice R con altri computer e l'integrazione analitica R all'interno di applicazioni web, desktop, mobili e dashboard: [come pubblicare e gestire i servizi web di R in R Server](https://docs.microsoft.com/r-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)

+ Come un **amministratore**, informazioni su come gestire i pacchetti, monitorare i nodi di web e nodi di calcolo e controllare la protezione per i processi R: [come interagire con e utilizzare i servizi web in R](https://docs.microsoft.com/r-server/operationalize/how-to-consume-web-service-interact-in-r)

## <a name="articles-in-this-series"></a>Articoli di questa serie

[Prestazioni di ottimizzazione per R: introduzione](sql-server-r-services-performance-tuning.md)

[Ottimizzazione delle prestazioni per R - configurazione di SQL Server](sql-server-configuration-r-services.md)

[Ottimizzazione delle prestazioni per R - R ottimizzazione di codice e i dati](r-and-data-optimization-r-services.md)

[Ottimizzazione delle prestazioni - risultati di case study](performance-case-study-r-services.md)
