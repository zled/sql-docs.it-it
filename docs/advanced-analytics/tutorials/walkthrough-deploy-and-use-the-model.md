---
title: Distribuire il modello R e usarlo in SQL (procedura dettagliata) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a5d8b7ac8bd36a6ce76b895b2dde4a07f5ea96
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085353"
---
# <a name="deploy-the-r-model-and-use-it-in-sql"></a>Distribuire il modello R e usarlo in SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa lezione è usare modelli R in un ambiente di produzione, chiamando un modello con Training da una stored procedure. È quindi possibile richiamare la stored procedure da R o qualsiasi linguaggio di programmazione dell'applicazione che supporta [!INCLUDE[tsql](../../includes/tsql-md.md)] (ad esempio c#, Java, Python, e così via), usare il modello per creare stime sulle nuove osservazioni.

Questo esempio illustra due modi più comuni per usare un modello nell'assegnazione dei punteggi:

- **Modalità di valutazione batch** viene usato quando è necessario creare più stime molto rapidamente, passando un database SQL di query o di tabella come input. Viene restituita una tabella dei risultati, cui è possibile inserire direttamente in una tabella o scrivere in un file.

- **Modalità di assegnazione dei punteggi singoli** viene usato quando è necessario creare una stima alla volta. Si passa un set di valori singoli alla stored procedure. I valori corrispondono alle funzionalità nel modello, che utilizza il modello per creare una stima, o generano un altro risultato, ad esempio un valore di probabilità. È quindi possibile restituire tale valore per l'applicazione o utente.

## <a name="batch-scoring"></a>Punteggio batch

È stata creata una stored procedure per l'assegnazione dei punteggi batch quando è stato inizialmente eseguito lo script di PowerShell. Questa stored procedure *PredictTipBatchMode*, esegue le operazioni seguenti:

- Ottiene un set di dati di input come query SQL
- Chiama il modello di regressione logistica di cui è stato eseguito il training e che è stato salvato nella lezione precedente
- Stima la probabilità che il driver Ottiene qualsiasi suggerimento diverso da zero

1. Per esaminare lo script per la stored procedure, è opportuno *PredictTipBatchMode*. Illustra diversi aspetti della modalità con la quale un modello può diventare operativo usando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].
  
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

    + Utilizzare un'istruzione SELECT per chiamare il modello archiviato da una tabella SQL. Il modello viene recuperato dalla tabella **varbinary (max)** i dati, archiviati nella variabile SQL  _\@lmodel2_e passato come parametro *mod* al sistema stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + I dati usati come input per l'assegnazione dei punteggi è definito come una query SQL e archiviata come una stringa nella variabile SQL  _\@input_. I dati recuperati dal database, questo viene archiviato in un frame di dati denominato *InputDataSet*, che è semplicemente il nome predefinito per i dati di input per il [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) procedure; è possibile definire un altro nome di variabile se necessario, usando il parametro   *_\@input_data_1_name_*.

    + Per generare i punteggi, la stored procedure chiama la funzione `rxPredict` dalla libreria **RevoScaleR** .

    + Il valore restituito *punteggio*, indica la probabilità dato il modello, tale driver Ottiene un suggerimento. Facoltativamente, è possibile applicare facilmente un tipo di filtro ai valori restituiti per suddividere i valori restituiti in gruppi "senza Mancia" e "suggerimento".  Una probabilità minore dello 0,5 significa, ad esempio, che è improbabile che un suggerimento.
  
2.  Per chiamare la stored procedure in modalità batch, si definisce la query richiesto come input per la stored procedure. Ecco la query SQL. è possibile eseguirlo in SSMS per verificarne il funzionamento.

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

3. Usare questo codice R per creare la stringa di input della query SQL:

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @inquery = ", input, sep="");
    ```

4. Per eseguire la stored procedure da R, chiamare il **sqlQuery** metodo per il **RODBC** pacchetto e usare la connessione SQL `conn` definita in precedenza:

    ```R
    sqlQuery (conn, q);
    ```

    Se si verifica un errore ODBC, controllare la sintassi di query, e se si hanno il numero corretto di virgolette. 
    
    Se viene visualizzato un errore di autorizzazione, assicurarsi che l'account di accesso ha la possibilità di eseguire la stored procedure.

## <a name="single-row-scoring"></a>Singola riga di assegnazione dei punteggi

Quando si chiama il modello di stima in base a una riga per riga, si passa un set di valori che rappresentano le funzionalità per ogni singolo caso. La stored procedure restituisce quindi una sola stima o probabilità. 

La stored procedure *PredictTipSingleMode* illustra questo approccio. Accetta come input più parametri che rappresentano i valori delle funzionalità (ad esempio, passeggeri count e ottimizzazione dei viaggi distanza), assegna un punteggio a queste funzionalità usando il modello R archiviato e restituisce la probabilità di suggerimento.

1. Se la stored procedure *PredictTipSingleMode* non è stato creato dallo script di PowerShell iniziale, è possibile eseguire l'istruzione Transact-SQL seguente per crearla adesso.

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

2. In SQL Server Management Studio, è possibile usare la [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** procedure (o **EXECUTE**) per chiamare la stored procedure e passarlo gli input obbligatori. Ad esempio, provare a eseguire questa istruzione in Management Studio:

    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    I valori passati sono, rispettivamente, per le variabili _passeggeri\_conteggio_, _trip_distance_, _trip\_ora\_in\_secs_, _pickup\_latitudine_, _pickup\_longitudine_, _salita\_latitudine_, e _salita\_longitudine_.

3. Per eseguire questa stessa chiamata dal codice R, è sufficiente definire una variabile R contenente la chiamata intera stored procedure, simile alla seguente:

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    I valori passati sono, rispettivamente, per le variabili _passeggeri\_conteggio_, _ottimizzazione dei viaggi\_distanza_, _trip\_ora\_nelle\_secs_, _pickup\_latitudine_, _pickup\_longitudine_, _salita\_ latitudine_, e _salita\_longitudine_.

4. Chiamare `sqlQuery` (dal **RODBC** pacchetto) e passare la stringa di connessione, con la variabile di stringa che contiene la chiamata alla stored procedure.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > R Tools per Visual Studio (RTVS) offre un'ottima integrazione con SQL Server e R. Vedere questo articolo per altri esempi di uso RODBC con una connessione di SQL Server: [funziona con SQL Server e R](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="summary"></a>Riepilogo

Ora che si è appreso come usare i [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dei dati e mantenere modelli R sottoposti a training per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dovrebbe essere relativamente semplice per creare nuovi modelli basati su questo set di dati. Ad esempio, è possibile creare questi modelli aggiuntivi:

- Un modello di regressione che stima l'importo della mancia

- Un modello di classificazione multiclasse che stima se il suggerimento è grande, Media o piccola

È inoltre consigliabile controllare alcuni di questi esempi e risorse aggiuntivi:

+ [Scenari di analisi scientifica dei dati e modelli di soluzioni](data-science-scenarios-and-solution-templates.md)

+ [Analisi avanzata nel database](sqldev-in-database-r-for-sql-developers.md)

+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)

+ [Risorse aggiuntive](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)

## <a name="previous-lesson"></a>Lezione precedente

[Compilare un modello R e salvarlo in SQL Server](walkthrough-build-and-save-the-model.md)

## <a name="next-steps"></a>Passaggi successivi

[Esercitazioni di SQL Server R](sql-server-r-tutorials.md)

[Come creare una stored procedure con sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)
