---
title: 'Lezione 6: Rendere operativo il modello R | Documenti Microsoft'
ms.custom: 
ms.date: 11/10/2017
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
- TSQL
ms.assetid: 52b05828-11f5-4ce3-9010-59c213a674d1
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: ec610a6276c51611dc470693d25b12b239baf333
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="lesson-6-operationalize-the-r-model"></a>Lezione 6: Rendere operativo il modello R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo fa parte di un'esercitazione per gli sviluppatori SQL su come usare il linguaggio R in SQL Server.

In questo passaggio descritto come *rendere operative le* del modello tramite una stored procedure. La stored procedure può essere chiamata direttamente da altre applicazioni, per l'esecuzione di stime relative a nuove osservazioni. La procedura dettagliata illustra due modi per eseguire l'assegnazione dei punteggi usando un modello R in una stored procedure:

- **Modalità di punteggio batch**: utilizzare una query di selezione come input per la stored procedure. La stored procedure restituisce una tabella di osservazioni corrispondenti ai casi di input.

- **Modalità di valutazione singola**: passare come input un set di valori di parametro singoli.  La stored procedure restituisce una singola riga o un singolo valore.

In primo luogo si prenderà in analisi il funzionamento generale della valutazione.

## <a name="basic-scoring"></a>Il punteggio di base

La stored procedure _PredictTip_ illustra la sintassi di base per il wrapping di una chiamata di stima in una stored procedure.

```SQL
CREATE PROCEDURE [dbo].[PredictTip] @inquery nvarchar(max) 
AS 
BEGIN 
  
DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);  
EXEC sp_execute_external_script @language = N'R',
  @script = N' 
    mod <- unserialize(as.raw(model)); 
    print(summary(mod)) 
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE); 
    str(OutputDataSet) 
    print(OutputDataSet) 
    ', 
  @input_data_1 = @inquery, 
  @params = N'@model varbinary(max)',
  @model = @lmodel2 
  WITH RESULT SETS ((Score float));
END
GO
```

+ Ottiene il modello serializzato dal database, l'istruzione SELECT e il modello viene archiviato nella variabile R `mod` per un'ulteriore elaborazione tramite R.

+ I nuovi case per l'assegnazione dei punteggi ottenuti dal [!INCLUDE[tsql](../../includes/tsql-md.md)] query specificata in `@inquery`, il primo parametro della stored procedure. Man mano che vengono letti i dati della query, le righe vengono salvate nel frame di dati predefinito `InputDataSet`. Tale frame di dati viene passato alla funzione `rxPredict` di R, che genera le valutazioni.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Poiché un data.frame può contenere una riga singola, è possibile usare lo stesso codice per la valutazione batch e la valutazione singola.
  
+ Il valore restituito dal `rxPredict` funzione è un **float** che rappresenta la probabilità che il driver Ottiene un suggerimento di qualsiasi importo.

## <a name="batch-scoring"></a>Punteggio batch

Ora si procede ad analizzare il funzionamento della valutazione batch.

1.  Per iniziare si ottiene un set di dati di input più piccolo sul quale lavorare. Questa query crea un elenco "top 10" delle corse, con il numero di passeggeri e altre funzionalità necessarie per effettuare una stima.
  
    ```SQL
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Risultati di esempio**
    
    ```
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

    Questa query può essere utilizzata come input per la stored procedure, _PredictTipBatchMode_, fornito come parte del download.

2. È opportuno esaminare il codice della stored procedure _PredictTipBatchMode_ in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

    ```SQL
    /****** Object:  StoredProcedure [dbo].[PredictTipBatchMode]  ******/
    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @inquery nvarchar(max)
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);
    EXEC sp_execute_external_script 
      @language = N'R',
      @script = N'
        mod <- unserialize(as.raw(model));
        print(summary(mod))
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);
        str(OutputDataSet)
        print(OutputDataSet)
      ',
      @input_data_1 = @inquery,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

3.  Specificare il testo della query in una variabile e passarlo come parametro alla stored procedure:

    ```SQL
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'

    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[PredictTip] @inquery = @query_string;
    ```
  
4. La stored procedure restituisce una serie di valori che rappresentano la stima per ogni trip i primi 10. Tuttavia, il superiore sono anche trip singolo passeggeri con una distanza di andata e ritorno relativamente breve, per cui il driver è improbabile che venga restituito un suggerimento.
  

> [!TIP]
> 
> Anziché restituire solo il "Sì-suggerimento" e "no-suggerimento" risultati, è possibile inoltre restituire il punteggio di probabilità per la stima e quindi applicare una clausola WHERE di _punteggio_ valori di colonna per classificare il punteggio come "probabilmente suggerimento" o " difficilmente suggerimento", utilizzando un valore di soglia, ad esempio 0,5 o 0,7. Questo passaggio non è incluso nella stored procedure, ma la sua implementazione non sarebbe difficile.

## <a name="single-row-scoring"></a>Assegnazione dei punteggi a riga singola

A volte risulta utile passare valori singoli da un'applicazione e ottenere un risultato singolo basato su tali valori. Ad esempio è possibile impostare un foglio di lavoro di Excel, un'applicazione web o un report di Reporting Services in modo che chiami la stored procedure e renda disponibili input digitati o selezionati dagli utenti.

In questa sezione imparare a creare singole stime utilizzando una stored procedure.

1. Esaminare in dettaglio il codice della stored procedure _PredictTipSingleMode_inclusa nel download.
  
    ```SQL
    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);
    EXEC sp_execute_external_script  
      @language = N'R',
      @script = N'  
        mod <- unserialize(as.raw(model));  
        print(summary(mod));  
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
        str(OutputDataSet);
        print(OutputDataSet); 
        ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float', @model = @lmodel2, @passenger_count =@passenger_count, @trip_distance=@trip_distance, @trip_time_in_secs=@trip_time_in_secs, @pickup_latitude=@pickup_latitude, @pickup_longitude=@pickup_longitude, @dropoff_latitude=@dropoff_latitude, @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END
    ```
  
    - Questa stored procedure accetta come input più valori singoli, quali il numero di passeggeri, la distanza della corsa e così via.
  
        Se si chiama la stored procedure da un'applicazione esterna, assicurarsi che i dati soddisfano i requisiti del modello di R. Ciò può includere la verifica che i dati di input siano sottoponibili a cast o convertibili in un tipo di dati di R o la convalida del tipo di dati e della lunghezza dei dati. 
  
    -   La stored procedure crea un punteggio in base al modello R archiviato.
  
2. Provare la stored procedure inserendo manualmente i valori.
  
    Aprire una nuova **Query** finestra e chiamare la stored procedure, che fornisce valori per ognuno dei parametri. I parametri rappresentano le colonne di funzionalità utilizzate dal modello e sono necessari.

    ```
    EXEC [dbo].[PredictTipSingleMode] @passenger_count = 0,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = 73.977303
    ```

    In alternativa, utilizzare questa forma più breve è supportata per [parametri a una stored procedure](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. I risultati indicano che la probabilità di ottenere un suggerimento è insufficiente questi 10 trip superiore, poiché tutti sono trip singolo passeggeri su una distanza relativamente breve.

## <a name="conclusions"></a>Conclusioni

In questo modo si conclude l'esercitazione. Ora che si è appreso come incorporare il codice R nelle stored procedure, è possibile estendere queste procedure consigliate per creare modelli personalizzati. L'integrazione con [!INCLUDE[tsql](../../includes/tsql-md.md)] semplifica notevolmente la distribuzione di modelli R per le stime e l'inclusione delle ripetizioni del training dei modelli nel flusso di lavoro dei dati enterprise.

## <a name="previous-lesson"></a>Lezione precedente

[Lezione 5: Eseguire il training e salvare un modello R con T-SQL](../r/sqldev-train-and-save-a-model-using-t-sql.md)
