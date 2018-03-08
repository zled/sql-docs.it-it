---
title: "Creare le funzionalità di dati con R e SQL (procedura dettagliata) | Documenti Microsoft"
ms.custom: 
ms.date: 08/23/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 4981d4eb-0874-4fe9-82e1-edf99890e27a
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 9b447f8c8faa834bea4360844308e468bf15d89c
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="create-data-features-using-r-and-sql-walkthrough"></a>Creare le funzionalità di dati con R e SQL (procedura dettagliata)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Il data engineering è un'area importante dell'apprendimento automatico. I dati richiedono spesso trasformazione prima che sia possibile utilizzarlo per la modellazione predittiva. Se i dati non dispongono delle funzionalità necessarie, è possibile crearle da valori esistenti.

Per questa attività di modellazione, anziché usare i valori raw di latitudine e longitudine dei punti di inizio e fine della corsa si vuole avere la distanza in miglia tra le due posizioni. Per creare questa funzionalità, si calcola la distanza lineare diretta tra due punti, utilizzando il [formula haversine](https://en.wikipedia.org/wiki/Haversine_formula).

In questo passaggio è confrontare due metodi diversi per la creazione di una funzionalità da dati:

- Utilizzo di una funzione R personalizzata
- Utilizzo di una funzione di T-SQL personalizzata in [!INCLUDE[tsql](../../includes/tsql-md.md)]

L'obiettivo consiste nel creare un nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di dati che includono le colonne originali e la nuova funzionalità numerica, *direct_distance*.

## <a name="featurization-using-r"></a>Uso di R Featurization

Il linguaggio R è noto per le ricche e variate librerie statistiche, ma potrebbe essere ancora necessario creare trasformazioni di dati personalizzate.

Prima di tutto, si farlo modalità R sono abituati a: ottenere i dati al computer portatile, e quindi eseguire una funzione personalizzata di R, *ComputeDist*, che consente di calcolare la distanza lineare tra due punti specificati dai valori di latitudine e longitudine.

1. Tenere presente che l'oggetto origine dati creata in precedenza ottiene solo le prime 1000 righe. Questo punto, definire una query che ottiene tutti i dati.

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. Creare una nuova origine dati di SQL Server utilizzando la query.

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) può richiedere una query composta da una query di selezione valida, fornita come argomento per il _sqlQuery_ parametro o il nome di un oggetto tabella, fornito come il _tabella_ parametro.
    
    - Se si desidera dati di esempio da una tabella, è necessario utilizzare il _sqlQuery_ parametro, definire i parametri di campionamento utilizzando la clausola TABLESAMPLE T-SQL e impostare il _rowBuffering_ argomento su FALSE.

3. Eseguire il codice seguente per creare la funzione di R personalizzata. ComputeDist accetta due coppie di valori di latitudine e longitudine e calcola la distanza tra di esse, restituisce la distanza in chilometri lineare.

    ```R
    env <- new.env();
    env$ComputeDist <- function(pickup_long, pickup_lat, dropoff_long, dropoff_lat){
      R <- 6371/1.609344 #radius in mile
      delta_lat <- dropoff_lat - pickup_lat
      delta_long <- dropoff_long - pickup_long
      degrees_to_radians = pi/180.0
      a1 <- sin(delta_lat/2*degrees_to_radians)
      a2 <- as.numeric(a1)^2
      a3 <- cos(pickup_lat*degrees_to_radians)
      a4 <- cos(dropoff_lat*degrees_to_radians)
      a5 <- sin(delta_long/2*degrees_to_radians)
      a6 <- as.numeric(a5)^2
      a <- a2+a3*a4*a6
      c <- 2*atan2(sqrt(a),sqrt(1-a))
      d <- R*c
      return (d)
    }
    ```
  
    + La prima riga definisce un nuovo ambiente. In R un ambiente può essere usato per incapsulare gli spazi dei nomi in pacchetti e strutture simili.  È possibile usare la funzione `search()` per visualizzare gli ambienti nell'area di lavoro. Per visualizzare gli oggetti in un ambiente specifico, digitare `ls(<envname>)`.
    + Le righe che iniziano con `$env.ComputeDistance` contengono il codice di definizione della formula dell'emisenoverso, che calcola la *distanza ortodromica* tra due punti su una sfera.

4. Dopo aver definito la funzione, si applica ai dati per creare una nuova colonna di funzionalità, *direct_distance*. ma prima di eseguire la trasformazione, modificare il contesto di calcolo locale.

    ```R
    rxSetComputeContext("local");
    ```

5. Chiamare il [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) funzione per ottenere la funzionalità dati di progettazione e applicare il `env$ComputeDist` funzione per i dati in memoria.

    ```R
    start.time <- proc.time();
  
    changed_ds <- rxDataStep(inData = featureEngineeringQuery,
    transforms = list(direct_distance=ComputeDist(pickup_longitude,pickup_latitude, dropoff_longitude, dropoff_latitude),
    tipped = "tipped", fare_amount = "fare_amount", passenger_count = "passenger_count",
    trip_time_in_secs = "trip_time_in_secs",  trip_distance="trip_distance",
    pickup_datetime = "pickup_datetime",  dropoff_datetime = "dropoff_datetime"),
    transformEnvir = env,
    rowsPerRead=500,
    reportProgress = 3);
  
    used.time <- proc.time() - start.time;
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""));
    ```

    + La funzione rxDataStep supporta vari metodi per la modifica dei dati sul posto. Per ulteriori informazioni, vedere l'articolo: [come subset e trasformazione dati in R Microsft](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    Tuttavia, alcuni punti non degni di nota riguardanti rxDataStep: 
    
    In altre origini dati, è possibile utilizzare gli argomenti *varsToKeep* e *varsToDrop*, ma non sono supportati per le origini dati di SQL Server. In questo esempio è stata utilizzata la _trasforma_ argomento per specificare le colonne pass-through e le colonne trasformate. Inoltre, quando in esecuzione in un Server SQL calcolo contesto, il _inData_ argomento può accettare solo un'origine dati di SQL Server.

    Il codice precedente può inoltre generare un messaggio di avviso quando viene eseguito il set di dati più grande. Quando il numero di righe volte il numero di colonne da creare supera il valore set (il valore predefinito è 3,000,000), rxDataStep restituisce un avviso e il numero di righe nel frame di dati restituiti verrà troncato. Per rimuovere l'avviso, è possibile modificare il _maxRowsByCols_ argomento nella funzione rxDataStep. Tuttavia, se _maxRowsByCols_ è troppo grande, potrebbero verificarsi problemi durante il caricamento di frame di dati in memoria.

7. Facoltativamente, è possibile chiamare [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) per controllare lo schema dell'origine dati trasformati.

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Definizione delle funzionalità con Transact-SQL

A questo punto, creare una funzione SQL personalizzata, *ComputeDist*, per eseguire la stessa attività come la funzione di R personalizzata.

1. Definire una nuova funzione SQL personalizzata, denominata *fnCalculateDistance*. Il codice per questa funzione SQL definita dall'utente è incluso nello script di PowerShell eseguito per creare e configurare il database.  La funzione dovrebbe esistere già nel database.

    Se non c'è, usare SQL Server Management Studio per generare la funzione nello stesso database in cui sono archiviati i dati dei taxi.

    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function calculates the direct distance between two geographical coordinates.
    RETURNS
    AS
    BEGIN
      DECLARE @distance decimal(28, 10)
      -- Convert to radians
      SET @Lat1 = @Lat1 / 57.2958
      SET @Long1 = @Long1 / 57.2958
      SET @Lat2 = @Lat2 / 57.2958
      SET @Long2 = @Long2 / 57.2958
      -- Calculate distance
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))
      --Convert to miles
      IF @distance <> 0
      BEGIN
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);
      END
      RETURN @distance
    END
    ```

2. Per vedere l'effetto della funzione, eseguire l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente da qualsiasi applicazione che supporti [!INCLUDE[tsql](../../includes/tsql-md.md)].

    ```sql
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
    FROM nyctaxi_sample
    ```
3. Dopo aver definito la funzione, sarebbe facile creare le funzionalità desiderate tramite SQL e quindi inserire i valori direttamente in una nuova tabella:

    ```
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. Tuttavia, di seguito viene illustrato come chiamare la funzione SQL personalizzata da codice R. In primo luogo, è possibile archiviare featurization query SQL in una variabile di R.

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > Questa query è stata modificata per ottenere un campione di dati per eseguire questa procedura dettagliata più velocemente più piccolo. È possibile rimuovere la clausola TABLESAMPLE se si desidera ottenere tutti i dati. Tuttavia, a seconda dell'ambiente, che non sia possibile caricare l'insieme completo in R, generando un errore.
  
5. Usare le righe di codice seguenti per chiamare la funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] dall'ambiente R e applicarla ai dati definiti in *featureEngineeringQuery*.
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
             dropoff_longitude = "numeric", dropoff_latitude = "numeric",
             passenger_count  = "numeric", trip_distance  = "numeric",
              trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  Dopo aver creato la nuova funzionalità, chiamare **rxGetVarsInfo** per creare un riepilogo dei dati nella tabella funzionalità.
  
    ```R
    rxGetVarInfo(data = featureDataSource)
    ```

    *Risultati*

    ```
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: numeric
    Var 4: trip_time_in_secs, Type: numeric
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: direct_distance, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: pickup_longitude, Type: numeric
    Var 11: dropoff_latitude, Type: numeric
    Var 12: dropoff_longitude, Type: numeric
    ```

    > [!NOTE]
    > In alcuni casi, si potrebbe ricevere un errore come questo: *eseguire l'autorizzazione è stata negata per l'oggetto 'fnCalculateDistance'* in tal caso, assicurarsi che l'account di accesso in uso disponga delle autorizzazioni per eseguire script e creare oggetti nel database, non solo nell'istanza.
    > Controllare lo schema per l'oggetto, fnCalculateDistance. Se l'oggetto è stato creato dal proprietario del database e l'account di accesso appartiene a db_datareader il ruolo, è necessario assegnare l'account di accesso le autorizzazioni esplicite per eseguire lo script.

## <a name="comparing-r-functions-and-sql-functions"></a>Confronto tra funzioni di R e SQL

Tenere presente questo frammento di codice utilizzato per il codice R ora?

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

È possibile provare l'utilizzo con l'esempio di funzione personalizzata di SQL per visualizzare la trasformazione dei dati tempo quando si chiama una funzione SQL. Inoltre, provare a passare i contesti di calcolo con rxSetComputeContext e confrontare gli intervalli di tempo.

I tempi possono variare notevolmente a seconda della velocità della rete e la configurazione hardware. Nelle configurazioni di cui è stato testato, il [!INCLUDE[tsql](../../includes/tsql-md.md)] approccio alla funzione è stata più veloce rispetto a una funzione R personalizzata. Pertanto, abbiamo utilizzare il [!INCLUDE[tsql](../../includes/tsql-md.md)] funzione per i calcoli nei passaggi successivi.

> [!TIP]
> Molto spesso, funzionalità di progettazione utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)] sarà più veloce rispetto a R. Ad esempio, T-SQL include windowing veloce e funzioni di rango che possono essere applicate ai calcoli di analisi scientifica dei dati comuni, ad esempio le medie mobili in sequenza e  *n* -riquadri. Scegliere il metodo più efficace in base ai dati e all'attività eseguita.

## <a name="next-lesson"></a>Lezione successiva

[Compilare un modello R e salvare in SQL](walkthrough-build-and-save-the-model.md)

## <a name="previous-lesson"></a>Lezione precedente

[Consente di visualizzare e riepilogare i dati con R](walkthrough-view-and-summarize-data-using-r.md)

