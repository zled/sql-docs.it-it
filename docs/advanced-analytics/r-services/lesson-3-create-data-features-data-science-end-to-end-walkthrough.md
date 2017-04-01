---
title: "Lezione 3: Creare funzionalit&#224; di dati (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 4981d4eb-0874-4fe9-82e1-edf99890e27a
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Lezione 3: Creare funzionalit&#224; di dati (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati)
Il data engineering è un'altra area importante dell'apprendimento automatico. Spesso i dati vanno trasformati per poter essere usati nella modellazione predittiva. Se i dati non dispongono delle funzionalità necessarie, è possibile crearle da valori esistenti.  
  
Per questa attività di modellazione, anziché usare i valori raw di latitudine e longitudine dei punti di inizio e fine della corsa si vuole avere la distanza in miglia tra le due posizioni. Per creare questa funzionalità si calcolerà la distanza lineare diretta tra due punti mediante la [formula dell'emisenoverso](https://en.wikipedia.org/wiki/Haversine_formula).  
Si confronteranno due metodi diversi per la creazione di una funzionalità a partire dai dati:  
  
-   Uso di R e della funzione `rxDataStep`    
-   Uso di una funzione personalizzata in [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
Per entrambi i metodi, il risultato del codice è un oggetto origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , `featureDataSource`, che include la nuova funzionalità numerica `direct_distance`.  
  
## <a name="creating-features-using-r"></a>Creare funzionalità mediante R  

Il linguaggio R è noto per le ricche e variate librerie statistiche, ma potrebbe essere ancora necessario creare trasformazioni di dati personalizzate. 

+ Verrà creata una nuova funzione R, `ComputeDist`, per calcolare la distanza lineare tra due punti specificati mediante i valori di latitudine e longitudine.  
+ Verrà chiamata la funzione per trasformare i dati nell'oggetto dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creato in precedenza e quindi l'oggetto verrà salvato nella nuova origine dati `featureDataSource`.  

### <a name="create-the-transformation-function"></a>Creare la funzione di trasformazione  
1.  Creare la funzione R personalizzata `ComputeDist`, che accetta due coppie di valori di latitudine e longitudine e calcola la distanza lineare fra tali coppie di valori.  La funzione restituisce una distanza in miglia.
  
    ```R  
    env <- new.env()  
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
  
    + La prima riga definisce un nuovo ambiente. In R un ambiente può essere usato per incapsulare gli spazi dei nomi in pacchetti e strutture simili.
    + È possibile usare la funzione `search()` per visualizzare gli ambienti nell'area di lavoro. Per visualizzare gli oggetti in un ambiente specifico, digitare `ls(<envname>)`. 
    + Le righe che iniziano con `$env.ComputeDistance` contengono il codice di definizione della formula dell'emisenoverso, che calcola la *distanza ortodromica* tra due punti su una sfera.  
 
  
### <a name="apply-the-transformation-function-to-data"></a>Applicare la funzione di trasformazione ai dati

Dopo aver definito la funzione la si applicherà ai dati per creare una nuova colonna di funzionalità, *direct_distance*.

1. Creare un'origine dati da usare mediante il costruttore `RxSqlServerData`.  
  
    ```R  
    featureDataSource = RxSqlServerData(table = "features",   
       colClasses = c(pickup_longitude = "numeric", 
       pickup_latitude = "numeric",   
       dropoff_longitude = "numeric", 
       dropoff_latitude = "numeric",  
       passenger_count  = "numeric", 
       trip_distance  = "numeric",  
       trip_time_in_secs  = "numeric", 
       direct_distance  = "numeric"),  
      connectionString = connStr)  
    ```  
  
3.  Chiamare la funzione `rxDataStep` per applicare la funzione `env$ComputeDist` ai dati specificati.  
    
    ```R  
    start.time <- proc.time()  
  
    rxDataStep(inData = inDataSource, outFile = featureDataSource,  
         overwrite = TRUE,  
         varsToKeep=c("tipped", "fare_amount", passenger_count", "trip_time_in_secs", 
            "trip_distance", "pickup_datetime", "dropoff_datetime", "pickup_longitude",
            "pickup_latitude", "dropoff_longitude", "dropoff_latitude")
         , transforms = list(direct_distance=ComputeDist(pickup_longitude, 
            pickup_latitude, dropoff_longitude, dropoff_latitude)),
            transformEnvir = env, rowsPerRead=500, reportProgress = 3)  
  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))    
    ```  
  
    + La funzione `rxDataStep` può modificare dati sul posto. Gli argomenti includono un vettore caratteri di colonne da passare (*varsToKeep*) e un elenco che definisce le trasformazioni.
    + Tutte le colonne che vengono trasformate vengono aggiunte automaticamente all'output e pertanto non è necessario che siano incluse nell'argomento *varsToKeep* .
    + In alternativa, mediante l'argomento *varsToDrop* è possibile specificare che vengano incluse tutte le colonne dell'origine ad eccezione delle variabili specificate.  
  
4.  Infine, chiamare `rxGetVarInfo` per controllare lo schema della nuova origine dati:  
  
    ```R  
    rxGetVarInfo(data = featureDataSource)  
    ```  
  
    *Risultati*
    
    *"It takes CPU Time=0.74 seconds, Elapsed Time=35.75 seconds to generate features."*  
    *Var 1: tipped, Type: integer*   
    *Var 2: fare_amount, Type: numeric*   
    *Var 3: passenger_count, Type: numeric*   
    *Var 4: trip_time_in_secs, Type: numeric*   
    *Var 5: trip_distance, Type: numeric*   
    *Var 6: pickup_datetime, Type: character*   
    *Var 7: dropoff_datetime, Type: character*   
    *Var 8: pickup_longitude, Type: numeric*   
    *Var 9: pickup_latitude, Type: numeric*   
    *Var 10: dropoff_longitude, Type: numeric*   
    *Var 11: dropoff_latitude, Type: numeric*   
    *Var 12: direct_distance, Type: numeric*   
  
## <a name="creating-features-using-transact-sql"></a>Creare funzionalità mediante Transact-SQL  
Ora che si è appreso come creare una funzionalità tramite una funzione R, si eseguirà la stessa operazione creando una funzione SQL personalizzata, `ComputeDist`. La funzione SQL `ComputeDist` opera su un oggetto di dati `RxSqlServerData` esistente per creare le nuove funzionalità di distanza basate sui valori di longitudine e latitudine esistenti.  
  
I risultati della trasformazione vengono salvati in un oggetto dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , `featureDataSource`, esattamente come con il codice R.  
  
Spesso la progettazione di funzionalità con [!INCLUDE[tsql](../../includes/tsql-md.md)] risulta più veloce che con R. Scegliere il metodo più efficiente in base ai dati e all'attività eseguita.  

### <a name="define-the-t-sql-custom-function"></a>Definire la funzione personalizzata T-SQL
  
1.  Definire la nuova funzione SQL `fnCalculateDistance`.  
  
    ```tsql  
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function calculates the direct distance between two geographical coordinates.  
    RETURNS float  
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

    + Il codice per questa *funzione SQL definita dall'utente* è incluso nello script PowerShell che è stato eseguito per creare e configurare il database.  La funzione dovrebbe esistere già nel database.  Se non esiste, usare SQL Server Management Studio per generare la funzione nello stesso database in cui vengono archiviati i dati dei taxi.

2.  Per vedere l'effetto della funzione, eseguire l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente da qualsiasi applicazione che supporti [!INCLUDE[tsql](../../includes/tsql-md.md)].   
  
    ```tsql  
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,       
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,  
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude   
    FROM nyctaxi_sample  
  
    ```  
### <a name="call-the-sql-function-from-r"></a>Chiamare la funzione SQL da R

1. Salvare l'istruzione SQL che chiama la funzione personalizzata in una variabile R.  
  
    ```R  
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,  
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,  
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude  
        FROM nyctaxi_joined_1_percent  
        tablesample (1 percent) repeatable (98052)"    
    ```  
  
    > [!TIP] Questa query è leggermente diversa dalla query [!INCLUDE[tsql](../../includes/tsql-md.md)] usata in precedenza. È stata modificata per ottenere un campione di dati più piccolo, al fine di velocizzare questa procedura dettagliata.  
  
4.  A questo punto usare le seguenti righe di codice per chiamare la funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] dall'ambiente R e applicarla ai dati definiti in `featureEngineeringQuery`.  
  
    ```R  
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,  
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",           
             dropoff_longitude = "numeric", dropoff_latitude = "numeric",  
             passenger_count  = "numeric", trip_distance  = "numeric",  
              trip_time_in_secs  = "numeric", direct_distance  = "numeric"),  
      connectionString = connStr)  
    ```  
  
5.  Dopo aver creato la nuova funzionalità, chiamare `rxGetVarsInfo` per creare un riepilogo della tabella delle funzionalità.  
  
    ```R  
    rxGetVarInfo(data = featureDataSource)  
    ```  
  
## <a name="comparing-r-functions-and-sql-functions"></a>Confronto tra funzioni R e funzioni SQL

Per questa particolare attività l'approccio che include la funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] risulta più veloce rispetto alla funzione R personalizzata. Pertanto nei passaggi successivi si userà la funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] per tali calcoli.  

Passare alla lezione successiva per apprendere come creare un modello predittivo con questi dati e come salvare il modello in una tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 4: Creare e salvare il modello &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Lezione precedente  
[Lezione 2: Visualizzare ed esplorare i dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
