---
title: Distribuire il modello R e usarla in SQL (procedura dettagliata) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
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
ms.assetid: f28a7aac-6d08-4781-ad28-b48d18cc16a0
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 771683f472af17292de62fb1591539f1215ebf57
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="deploy-the-r-model-and-use-it-in-sql"></a>Distribuire il modello R e usarla in SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa lezione, utilizzare i modelli R in un ambiente di produzione, mediante la chiamata di un modello con Training da una stored procedure. È quindi possibile richiamare la stored procedure da R o qualsiasi linguaggio di programmazione che supporta [!INCLUDE[tsql](../../includes/tsql-md.md)] (ad esempio c#, Java, Python e così via), utilizzare il modello per eseguire stime sui nuovi osservazioni.

Questo esempio illustra due modi più comuni per usare un modello di assegnazione dei punteggi:

- **Modalità di punteggio batch** viene utilizzato quando è necessario creare più stime molto veloce, passando un database SQL di query o la tabella come input. Viene restituita una tabella dei risultati, che è possibile inserire direttamente in una tabella o scrivere in un file.

- **Modalità di assegnazione dei punteggi singoli** viene utilizzato quando è necessario creare una stima alla volta. Passare un set di valori singoli alla stored procedure. I valori corrispondono alle funzionalità nel modello, che il modello utilizzato per creare una stima, o generano i risultati di un'altra, ad esempio un valore di probabilità. È quindi possibile restituire tale valore per l'applicazione o un utente.

## <a name="batch-scoring"></a>Punteggio batch

Quando è stato inizialmente eseguito lo script di PowerShell, è stata creata una stored procedure per il punteggio batch. Questa stored procedure, *PredictTipBatchMode*, esegue le operazioni seguenti:

- Ottiene un set di dati di input come query SQL
- Chiama il modello di regressione logistica di cui è stato eseguito il training e che è stato salvato nella lezione precedente
- Consente di stimare la probabilità che il driver Ottiene qualsiasi suggerimento diverso da zero

1. Richiedere un minuto, per esaminare lo script per la stored procedure, *PredictTipBatchMode*. Illustra diversi aspetti della modalità con la quale un modello può diventare operativo usando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].
  
    ```tsql
    CREATE PROCEDURE [dbo].[PredictTipBatchMode]
    @input nvarchar(max)
    AS
    BEGIN
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  FROM nyc_taxi_models);
      EXEC sp_execute_external_script @language = N'R',
         @script = N'
           mod <- unserialize(as.raw(model));
           print(summary(mod))
           OutputDataSet<-rxPredict(modelObject = mod,
             data = InputDataSet,
             outData = NULL,
             predVarNames = "Score", type = "response",
             writeModelVars = FALSE, overwrite = TRUE);
           str(OutputDataSet)
           print(OutputDataSet)',
      @input_data_1 = @input,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

    + Utilizzare un'istruzione SELECT per chiamare il modello archiviato da una tabella SQL. Il modello viene recuperato dalla tabella **varbinary (max)** dati, archiviati nella variabile SQL  _@lmodel2_ e passato come parametro *mod* al sistema archiviato procedura [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + I dati utilizzati come input per il punteggio è definito come una query SQL e archiviato come una stringa in variabile SQL  _@input_ . Come i dati vengono recuperati dal database, questo viene archiviato in un frame di dati denominato *InputDataSet*, che è semplicemente il nome predefinito per i dati di input di [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) procedura; è possibile definire un altro nome variabile, se necessario, utilizzando il parametro   *_@input_data_1_name_*  .

    + Per generare i punteggi, la stored procedure chiama la funzione `rxPredict` dalla libreria **RevoScaleR** .

    + Il valore restituito, *punteggio*, indica la probabilità, dato il modello, il driver Ottiene un suggerimento. Facoltativamente, è possibile applicare facilmente un tipo di filtro per i valori restituiti per classificare i valori restituiti in "descrizione" e "Nessun suggerimento".  Ad esempio, una probabilità di minore di 0,5 indica che è improbabile che un suggerimento.
  
2.  Per chiamare la stored procedure in modalità batch, si definisce la query richiesta come input per la stored procedure. Ecco la query SQL. è possibile eseguirlo in SSMS per verificarne il funzionamento.

    ```SQL
    SELECT TOP 10
      a.passenger_count AS passenger_count,
      a.trip_time_in_secs AS trip_time_in_secs,
      a.trip_distance AS trip_distance,
      a.dropoff_datetime AS dropoff_datetime,
      dbo.fnCalculateDistance( pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance
      FROM 
        (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude 
        FROM nyctaxi_sample)a 
      LEFT OUTER JOIN
      ( SELECT medallion, hack_license, pickup_datetime
      FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b
      ON a.medallion=b.medallion
      AND a.hack_license=b.hack_license
      AND a.pickup_datetime=b.pickup_datetime
      WHERE b.medallion is null
    ```

3. Utilizzare questo codice R per creare la stringa di input della query SQL:

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @inquery = ", input, sep="");
    ```

4. Per eseguire la stored procedure da R, chiamare il **sqlQuery** metodo il **RODBC** pacchetto e utilizzare la connessione SQL `conn` definita in precedenza:

    ```R
    sqlQuery (conn, q);
    ```

    Se si verifica un errore ODBC, controllare la sintassi di query, e che sia il numero corretto di virgolette. 
    
    Se viene visualizzato un errore di autorizzazione, assicurarsi che l'account di accesso ha la possibilità di eseguire la stored procedure.

## <a name="single-row-scoring"></a>Singola riga di punteggio

Quando si chiama il modello per la stima in base a una riga per riga, si passa un set di valori che rappresentano le funzionalità per ogni singolo caso. La stored procedure restituisce quindi una sola stima o probabilità. 

La stored procedure *PredictTipSingleMode* illustra questo approccio. Accetta come input più parametri che rappresentano i valori delle funzionalità (ad esempio, passeggeri conteggio e andata e ritorno distanza), punteggi di queste funzionalità usando il modello R archiviato e restituisce la probabilità di suggerimento.

1. Se la stored procedure *PredictTipSingleMode* non è stato creato tramite lo script di PowerShell iniziale, è possibile eseguire l'istruzione Transact-SQL seguente per crearla.

    ```tsql
    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0,
    @trip_distance float = 0,
    @trip_time_in_secs int = 0,
    @pickup_latitude float = 0,
    @pickup_longitude float = 0,
    @dropoff_latitude float = 0,
    @dropoff_longitude float = 0
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs, @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)'
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);

      EXEC sp_execute_external_script @language = N'R',  @script = N'
            mod <- unserialize(as.raw(model));
            print(summary(mod))
            OutputDataSet<-rxPredict(
              modelObject = mod,
              data = InputDataSet,
              outData = NULL,
              predVarNames = "Score",
              type = "response",
              writeModelVars = FALSE,
              overwrite = TRUE);
            str(OutputDataSet)
            print(OutputDataSet)
            ',
      @input_data_1 = @inquery,
      @params = N'
      -- passthrough columns
      @model varbinary(max) ,
      @passenger_count int ,
      @trip_distance float ,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      -- mapped variables
      @model = @lmodel2 ,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance ,
      @trip_time_in_secs=@trip_time_in_secs ,
      @pickup_latitude=@pickup_latitude ,
      @pickup_longitude=@pickup_longitude ,
      @dropoff_latitude=@dropoff_latitude ,
      @dropoff_longitude=@dropoff_longitude
      WITH RESULT SETS ((Score float));
    END
    ```

2. In SQL Server Management Studio, è possibile utilizzare il [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** procedure (o **EXECUTE**) per chiamare la stored procedure e passarlo input obbligatori. Ad esempio, provare a eseguire l'istruzione in Management Studio:

    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    I valori passati in questa pagina sono, rispettivamente, per le variabili _passeggeri\_conteggio_, _trip_distance_, _viaggi\_tempo\_in\_sec_, _prelievo\_latitudine_, _prelievo\_longitudine_, _dropoff\_latitudine_, e _dropoff\_longitudine_.

3. Per eseguire la stessa chiamata dal codice R, definire semplicemente una variabile di R che contiene la chiamata intera stored procedure, simile alla seguente:

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    I valori passati in questa pagina sono, rispettivamente, per le variabili _passeggeri\_conteggio_, _viaggi\_distanza_, _viaggi\_ora\_in\_sec_, _prelievo\_latitudine_, _prelievo\_longitudine_, _dropoff\_ latitudine_, e _dropoff\_longitudine_.

4. Chiamare `sqlQuery` (dal **RODBC** pacchetto) e passare la stringa di connessione, con la variabile di stringa contenente la chiamata della stored procedure.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > Strumenti R per Visual Studio (RTVS) fornisce un'integrazione ottima con SQL Server e R. Vedere l'articolo per ulteriori esempi di utilizzo RODBC con una connessione di SQL Server: [utilizzo di SQL Server e R](https://docs.microsoft.com/en-us/visualstudio/rtvs/sql-server)

## <a name="summary"></a>Riepilogo

Ora che si è appreso come utilizzare i [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati e mantenere modelli R con training per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], deve essere relativamente semplice per creare nuovi modelli basati su questo set di dati. Ad esempio, è possibile creare questi modelli aggiuntivi:

- Un modello di regressione che stima l'importo della mancia

- Un modello di classificazione multiclasse che consente di stimare se il suggerimento è piccola, Media o grande

È inoltre consigliabile controllare alcuni di questi esempi e risorse aggiuntivi:

+ [Scenari di analisi scientifica dei dati e modelli di soluzioni](data-science-scenarios-and-solution-templates.md)

+ [Analisi avanzata nel database](sqldev-in-database-r-for-sql-developers.md)

+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)

+ [Risorse aggiuntive](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)

## <a name="previous-lesson"></a>Lezione precedente

[Compilare un modello R e salvarlo in SQL Server](walkthrough-build-and-save-the-model.md)

## <a name="next-steps"></a>Passaggi successivi

[Esercitazioni di SQL Server R](sql-server-r-tutorials.md)

[Come creare una stored procedure utilizzando sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)
