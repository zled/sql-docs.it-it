---
title: Consente di visualizzare e riepilogare i dati usando R (procedura dettagliata) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ba464bafdb077649dad9633bcb21ca2b026221ca
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203393"
---
# <a name="view-and-summarize-data-using-r"></a>Consente di visualizzare e riepilogare i dati con R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ora possibile lavorare con gli stessi dati mediante il codice R. In questa lezione si imparare a utilizzare le funzioni di **RevoScaleR** pacchetto.

In questa procedura dettagliata, oltre a tutti i codici necessari per creare gli oggetti dati, generare riepiloghi e creare modelli, è incluso uno script R. Il file di script R **RSQL_RWalkthrough.R**è disponibile nel percorso in cui sono stati installati i file di script.

+ Se si ha familiarità con R, è possibile eseguire lo script in una sola volta.
+ Per gli utenti di imparare a utilizzare RevoScaleR, in questa esercitazione è illustrati lo script riga per riga.
+ Per eseguire singole righe dello script, è possibile evidenziare una o più righe nel file e premere CTRL + INVIO.

> [!TIP]
> Salvare l'area di lavoro R nel caso in cui si voglia completare il resto della procedura dettagliata in un secondo momento.  In questo modo gli oggetti dati e altre variabili sono pronti per il riutilizzo.

## <a name="define-a-sql-server-compute-context"></a>Definire un contesto di calcolo di SQL Server

Microsoft R rende più semplice ottenere dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da utilizzare nel codice R. Il processo è il seguente:
  
- Creare una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
- Definire una query che contiene i dati necessari oppure specificare una tabella o una vista
- Definire uno o più contesti di calcolo da usare durante l'esecuzione del codice R
- È inoltre possibile definire le trasformazioni applicate all'origine dati durante la lettura dall'origine

I passaggi seguenti sono parte del codice R e devono essere eseguito in un ambiente di R. È stato utilizzato Microsoft R Client, perché include tutti i pacchetti RevoScaleR, nonché un set di strumenti R base e leggero.

1. Se il **RevoScaleR** pacchetto non è già caricato, eseguire la seguente riga di codice R:

    ```R
    library("RevoScaleR")
    ```

     Le virgolette sono facoltative, in questo caso, sebbene consigliabile.
     
     Se si verifica un errore, assicurarsi che l'ambiente di sviluppo R utilizza una libreria che include il pacchetto RevoScaleR. Utilizzare un comando, ad esempio `.libPaths()` per visualizzare il percorso di libreria corrente.

2. Creare la stringa di connessione per SQL Server e salvarlo in una variabile di R _connStr_.
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=Your_Database_Name;Uid=Your_User_Name;Pwd=Your_Password"
    ```

    Per il nome del server, potrebbe essere in grado di utilizzare solo il nome dell'istanza o potrebbe essere necessario qualificare completamente il nome, a seconda della rete.

    Per l'autenticazione di Windows, la sintassi è leggermente diversa:
    
    ```R
    connStr <- "Driver=SQL Server;Server=SQL_instance_name;Database=database_name;Trusted_Connection=Yes"
    ```

    Lo script R disponibile per il download usa solo account di accesso SQL. In genere, è consigliabile utilizzare l'autenticazione di Windows in cui è possibile, per evitare il salvataggio delle password nel codice R. Tuttavia, per garantire che il codice in questa esercitazione corrisponde al codice scaricato da Github, si userà un account di accesso SQL per il resto della procedura dettagliata.

3. Definire le variabili da utilizzare per creare un nuovo _contesto di calcolo_. Dopo aver creato l'oggetto di contesto di calcolo, è possibile utilizzare, per eseguire codice R nell'istanza di SQL Server.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R usa una directory temporanea per la serializzazione degli oggetti R tra la workstation e il computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . È possibile specificare la directory locale che viene usata come *sqlShareDir*o accettare quella predefinita.
  
    - Utilizzare *sqlWait* per indicare se si desidera R per attendere i risultati dal server.  Per una discussione di attesa e i processi non in attesa, vedere [distribuita e l'elaborazione in parallelo con ScaleR nella Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Utilizzare l'argomento *sqlConsoleOutput* per indicare che non si desidera visualizzare l'output dalla console di R.


4. Chiamare il [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) costruttore per creare l'oggetto di contesto di calcolo con le variabili e stringhe di connessione già definite e salvare il nuovo oggetto nella variabile R *sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. Per impostazione predefinita, il contesto di calcolo è locale, pertanto è necessario impostare in modo esplicito il *active* contesto di calcolo.

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + `rxSetComputeContext` restituisce il contesto di calcolo precedentemente attivo in modo invisibile in modo che sia possibile usarlo
    + `rxGetComputeContext` restituisce il contesto di calcolo attivo
    
    L'impostazione di un contesto di calcolo ha effetto solo alle operazioni che usano le funzioni nel pacchetto **RevoScaleR** . Il contesto di calcolo non ha alcun effetto sul modo in cui vengono eseguite le operazioni R open source.

## <a name="create-a-data-source-using-rxsqlserver"></a>Creare un'origine dati tramite RxSqlServer

In Microsoft R un *origine dati* è un oggetto creato utilizzando le funzioni RevoScaleR. L'oggetto origine dati specifica un set di dati che si desidera utilizzare per un'attività, ad esempio estrazione training o la funzionalità di modello. È possibile ottenere dati da un'ampia gamma di origini. per l'elenco delle origini attualmente supportate, vedere [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

In precedenza è definita una stringa di connessione e salvate le informazioni in una variabile di R. È possibile riutilizzare tali informazioni di connessione per specificare i dati che si desidera ottenere.

1. Salvare una query SQL come una variabile di stringa. La query definisce i dati per il training del modello.

    ```R
    sampleDataQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    È stata utilizzata una clausola TOP qui per semplificare l'esecuzione più veloce, ma le righe restituite dalla query possono variare a seconda dell'ordine. Di conseguenza, i risultati di riepilogo anche potrebbero essere diversi da quelli elencati di seguito. È possibile rimuovere la clausola TOP.

2. Passare la definizione di query come argomento alla funzione [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata).

    ```R
    inDataSource <- RxSqlServerData(
      sqlQuery = sampleDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )
    ```
    
    + L'argomento  *colClasses* specifica i tipi di colonna da usare durante lo spostamento dei dati tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e R. Questo aspetto è importante perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa tipi di dati diversi rispetto a R e più tipi di dati. Per ulteriori informazioni, vedere [tipi di dati e delle librerie R](../r/r-libraries-and-data-types.md).
  
    + L'argomento *rowsPerRead* è importante per la gestione dell'utilizzo della memoria e i calcoli efficiente.  La maggior parte delle funzioni analitiche avanzate in[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] elabora i dati in blocchi e raggruppa risultati intermedi, restituendo i calcoli finali dopo che tutti i dati sono stati letti.  Aggiungendo il *rowsPerRead* parametro, è possibile controllare il numero di righe di dati viene letti in ogni blocco per l'elaborazione.  Se il valore di questo parametro è troppo alto, l'accesso ai dati potrebbe risultare lento perché la memoria disponibile non è sufficiente a elaborare in modo efficiente un blocco troppo grande di dati.  In alcuni sistemi, l'impostazione *rowsPerRead* a un valore eccessivamente basso anche possibile riduzione delle prestazioni.

3. A questo punto, si crea il *inDataSource* oggetto, ma non contiene dati. I dati non viene spostati dalla query SQL nell'ambiente locale finché non si esegue una funzione, ad esempio [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) o [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary).

    Tuttavia, dopo aver definito gli oggetti dati, è possibile utilizzarlo come argomento ad altre funzioni.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Utilizzare i dati di SQL Server nei riepiloghi di R

In questa sezione si proverà alcune delle funzioni incluse [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] contesti di calcolo remoto tale supporto. Tramite l'applicazione funzioni R all'origine dati, è possibile esplorare, riepilogare e del grafico di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati.

1. Chiamare la funzione [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) per ottenere un elenco delle variabili nell'origine dati e i relativi tipi di dati.

    **rxGetVarInfo** è una funzione utile; è possibile chiamare su qualsiasi frame di dati o in un set di dati in un oggetto dati remoti, per ottenere informazioni quali i valori massimo e minimo valori, il tipo di dati e il numero di livelli nelle colonne fattore.
    
    È consigliabile eseguire questa funzione dopo qualsiasi tipo di input dei dati, dopo la trasformazione o la progettazione di una funzionalità. In questo modo, è possibile assicurarsi che tutte le funzionalità che si desidera utilizzare nel modello sono i dati previsti digitare e di evitare errori.
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **Risultati**
    
    ```
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: integer
    Var 4: trip_time_in_secs, Type: numeric, Storage: int64
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: pickup_longitude, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: dropoff_longitude, Type: numeric
    ```

2. A questo punto, chiamare la funzione RevoScaleR [rxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary) per ottenere ulteriori statistiche dettagliate sulle singole variabili.

    rxSummary si basa su R `summary` funzionare, ma presenta alcuni vantaggi e la funzionalità aggiuntive. rxSummary funziona in più contesti di calcolo e supporta la suddivisione in blocchi.  È inoltre possibile utilizzare rxSummary per trasformare i valori o riepilogare in base ai livelli di fattore.
    
    In questo esempio, si riepiloga la quantità di tariffa in base al numero di persone.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Il primo argomento rxSummary specifica la formula o il termine da riepilogare. In questo caso, il `F()` funzione viene utilizzata per convertire i valori in _passeggeri\_conteggio_ in fattori prima di sommare. È inoltre necessario specificare il valore minimo (1) e il valore massimo (6) per il _passeggeri\_conteggio_ variabile fattore.
    + Se non si specifica l'output delle statistiche, per impostazione predefinita rxSummary output StDev, Media, Min, Max e il numero di osservazioni valide e mancante.
    + Questo esempio include anche una parte di codice per tenere traccia dell'ora in cui la funzione ha inizio e termina in modo da poter confrontare le prestazioni.
  
    **Risultati**

    Se la funzione rxSummary viene eseguito correttamente, verranno visualizzati risultati simili, seguita da un elenco delle statistiche di categoria. 

    ```
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Esercizio aggiuntivo sui big data

Provare a definire una nuova stringa di query con tutte le righe. è consigliabile che impostare un nuovo oggetto di origine dati per questa sperimentazione. È anche possibile provare a modificare il *rowsToRead* parametro per visualizzare il relativo impatto sulla velocità effettiva.

```R
bigDataQuery  <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"

bigDataSource <- RxSqlServerData(
      sqlQuery = bigDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )

start.time <- proc.time()
rxSummary(~fare_amount:F(passenger_count,1,6), data = bigDataSource)
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
  Elapsed Time=", round(used.time[3],2),
  " seconds to summarize the inDataSource.", sep=""))
```

> [!TIP]
> Durante l'esecuzione, è possibile utilizzare uno strumento come [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) o SQL Profiler per vedere come viene stabilita la connessione e il codice R viene eseguito tramite servizi di SQL Server.
> 
> È anche possibile monitorare i processi di R in esecuzione in SQL Server utilizzando questi [report personalizzati](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="next-lesson"></a>Lezione successiva

[Creare grafici e tracciati con R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="previous-lesson"></a>Lezione precedente

[Esplorare i dati usando R](walkthrough-view-and-explore-the-data.md)
