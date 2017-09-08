---
title: 'Passaggio 6: Rendere operativo il modello | Documenti Microsoft'
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- python-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b33f3876f054d7e7150a18967d5cfa37dd2d82bf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="step-6-operationalize-the-model"></a>Passaggio 6: Rendere operativo il modello

In questo passaggio, si apprenderà a *rendere operative le* i modelli che è stato eseguito il training e salvato nel passaggio precedente. Utilizzare in questo caso significa "distribuzione del modello nell'ambiente di produzione per il punteggio". Si tratta di un'operazione semplice se il codice Python è contenuto in una stored procedure. È quindi possibile chiamare la stored procedure dalle applicazioni, per eseguire stime sui nuovi osservazioni.

Si apprenderà due metodi per chiamare un modello di Python da una stored procedure:

- **Modalità di valutazione batch**: usare una query SELECT per rendere disponibili più righe di dati. La stored procedure restituisce una tabella di osservazioni corrispondenti ai casi di input.
- **Modalità di valutazione singola**: passare come input un set di valori di parametro singoli.  La stored procedure restituisce una singola riga o un singolo valore.

## <a name="scoring-using-the-scikit-learn-model"></a>Assegnazione dei punteggi usando il scikit-informazioni su modello

La stored procedure _PredictTipSciKitPy_ utilizza il scikit-informazioni su modello. Questa stored procedure viene illustrata la sintassi di base per il wrapping di una chiamata di stima Python in una stored procedure.

- Il nome del modello da utilizzare viene fornito come parametro di input per la stored procedure. 
- La stored procedure verrà quindi caricare il modello serializzato dalla tabella di database `nyc_taxi_models`.table, utilizzando l'istruzione SELECT nella stored procedure.
- Il modello serializzato è archiviato nella variabile Python `mod` per un'ulteriore elaborazione usando Python.
- Vengono ottenuti i nuovi case che devono essere calcolato il punteggio di [!INCLUDE[tsql](../../includes/tsql-md.md)] query specificata in `@input_data_1`. Man mano che vengono letti i dati della query, le righe vengono salvate nel frame di dati predefinito `InputDataSet`.
- Questo frame di dati viene passato al `predict_proba` funzione del modello di regressione logistica, `mod`, cui è stato creato utilizzando scikit-informazioni su modello. 
- Il `predict_proba` funzione (`probArray = mod.predict_proba(X)`) restituisce un **float** che rappresenta la probabilità che verrà assegnato un suggerimento (qualsiasi valore).
- La stored procedure calcola anche una metrica di accuratezza, AUC (area nella curva). Metriche di accuratezza, ad esempio AUC possono essere generate solo se si specifica anche l'etichetta di destinazione (ad esempio la colonna inclinata). Le stime non richiedono l'etichetta di destinazione (variabile `y`), ma non il calcolo di metriche di accuratezza.

  Pertanto, se non si dispone di etichette di destinazione per i dati da classificare, è possibile modificare la stored procedure per rimuovere i calcoli AUC e limitino a restituire le probabilità di suggerimento dalle funzionalità (variabile `X` nella stored procedure).

```SQL
CREATE PROCEDURE [dbo].[PredictTipSciKitPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
  EXEC sp_execute_external_script
    @language = N'Python',
    @script = N'
        import pickle;
        import numpy;
        import pandas;
        from sklearn import metrics
        
        mod = pickle.loads(lmodel2)
        
        X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
        y = numpy.ravel(InputDataSet[["tipped"]])
        
        probArray = mod.predict_proba(X)
        probList = []
        for i in range(len(probArray)):
          probList.append((probArray[i])[1])
        
        probArray = numpy.asarray(probList)
        fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
        aucResult = metrics.auc(fpr, tpr)
        print ("AUC on testing data is: " + str(aucResult))
        
        OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
        ',  
    @input_data_1 = @inquery,
    @input_data_1_name = N'InputDataSet',
    @params = N'@lmodel2 varbinary(max)',
    @lmodel2 = @lmodel2
  WITH RESULT SETS ((Score float));
END
GO
```

## <a name="scoring-using-the-revoscalepy-model"></a>Assegnazione dei punteggi usando il modello revoscalepy

La stored procedure _PredictTipRxPy_ utilizza un modello che è stato creato utilizzando il **revoscalepy** libreria. Funziona molto nello stesso modo di _PredictTipSciKitPy_ routine, ma con alcune modifiche per il **revoscalepy** funzioni.

```SQL
CREATE PROCEDURE [dbo].[PredictTipRxPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from sklearn import metrics
      from revoscalepy.functions.RxPredict import rx_predict_ex;
      
      mod = pickle.loads(lmodel2)
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      probArray = rx_predict_ex(mod, X)
      probList = []
      for i in range(len(probArray._results["tipped_Pred"])):
        probList.append((probArray._results["tipped_Pred"][i]))
      
      probArray = numpy.asarray(probList)
      fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
      aucResult = metrics.auc(fpr, tpr)
      print ("AUC on testing data is: " + str(aucResult))
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
      ',    
    @input_data_1 = @inquery,
    @input_data_1_name = N'InputDataSet',
    @params = N'@lmodel2 varbinary(max)',
    @lmodel2 = @lmodel2
  WITH RESULT SETS ((Score float));
END
GO
```

## <a name="batch-scoring-using-a-select-query"></a>Valutazione batch mediante una query SELECT

Le stored procedure **PredictTipSciKitPy** e **PredictTipRxPy** richiedono due parametri di input: 

- La query che recupera i dati per l'assegnazione dei punteggi
- Il nome di un modello con training

In questa sezione si apprenderà come passare gli argomenti per la stored procedure da modificare con facilità il modello sia i dati utilizzati per l'assegnazione dei punteggi.

1. Definire i dati di input e chiamare le stored procedure per il punteggio come indicato di seguito. In questo esempio viene utilizzata la stored procedure PredictTipSciKitPy per il punteggio e passa il nome del modello e di stringa di query

    ```SQL
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    La stored procedure restituisce la probabilità stimate per ogni versione di andata e ritorno passato come parte della query di input. Se si utilizza SQL Server Management Studio (SQL Server Management Studio) per l'esecuzione di query, le probabilità verranno visualizzati come una tabella di **risultati** riquadro. Il **messaggi** riquadro restituisce la metrica di accuratezza (AUC o area nella curva) con un valore pari a circa 0,56.

2. Utilizzare il **revoscalepy** del modello per il punteggio, chiamare la stored procedure **PredictTipRxPy**, passando la stringa di query e nome del modello.

    ```SQL
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="score-individual-rows-using-scikit-learn-model"></a>Assegnare un punteggio singole righe utilizzando scikit-informazioni su modello

In alcuni casi, invece di punteggio batch, si desidera passare un singolo case, il recupero di valori da un'applicazione e ottenere un singolo risultato in base a tali valori. Ad esempio è possibile impostare un foglio di lavoro di Excel, un'applicazione web o un report di Reporting Services in modo che chiami la stored procedure e renda disponibili input digitati o selezionati dagli utenti.

In questa sezione si apprenderà come creare stime singole chiamando una stored procedure.

1. È opportuno esaminare il codice delle stored procedure [PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy) e [PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy), incluso come parte del download. Queste stored procedure utilizzano il scikit-informazioni e i modelli revoscalepy ed eseguire l'assegnazione dei punteggi come indicato di seguito:

  - Il nome del modello e più valori singoli vengono forniti come input. I dati di input includono il numero di passeggeri, la distanza di andata e ritorno e così via.
  - Una funzione con valori di tabella, `fnEngineerFeatures`, accetta valori di input e converte la Latitude e la longitudine per indicare a distanza. [Lezione 4](sqldev-py4-create-data-features-using-t-sql.md) contiene una descrizione di questa funzione con valori di tabella.
  - Se si chiama la stored procedure da un'applicazione esterna, assicurarsi che i dati di input corrispondano le funzionalità necessarie di input del modello di Python. Potrebbe trattarsi di cast o conversione di dati di input in un tipo di dati, Python o convalida tipo di dati e lunghezza dei dati.
  - La stored procedure crea un punteggio in base al modello di Python stored.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

Qui è la definizione della stored procedure che esegue l'assegnazione dei punteggi usando il **scikit-informazioni** modello.

```SQL
CREATE PROCEDURE [dbo].[PredictTipSingleModeSciKitPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
  SELECT * FROM [dbo].[fnEngineerFeatures]( 
    @passenger_count,
    @trip_distance,
    @trip_time_in_secs,
    @pickup_latitude,
    @pickup_longitude,
    @dropoff_latitude,
    @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      probList = []
      probList.append((mod.predict_proba(X)[0])[1])
      
      # Create output data frame
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
    ',
    @input_data_1 = @inquery,
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      @model = @lmodel2,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance,
      @trip_time_in_secs=@trip_time_in_secs,
      @pickup_latitude=@pickup_latitude,
      @pickup_longitude=@pickup_longitude,
      @dropoff_latitude=@dropoff_latitude,
      @dropoff_longitude=@dropoff_longitude
  WITH RESULT SETS ((Score float));
END
GO
```

### <a name="predicttipsinglemoderxpy"></a>PredictTipSingleModeRxPy

Qui è la definizione della stored procedure che esegue l'assegnazione dei punteggi usando il **revoscalepy** modello.

```SQL
CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
    SELECT * FROM [dbo].[fnEngineerFeatures]( 
      @passenger_count,
      @trip_distance,
      @trip_time_in_secs,
      @pickup_latitude,
      @pickup_longitude,
      @dropoff_latitude,
      @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from revoscalepy.functions.RxPredict import rx_predict_ex;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      
      probArray = rx_predict_ex(mod, X)
      
      probList = []
      probList.append(probArray._results["tipped_Pred"])
      
      # Create output data frame
      OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
      ',
    @input_data_1 = @inquery,
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      @model = @lmodel2,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance,
      @trip_time_in_secs=@trip_time_in_secs,
      @pickup_latitude=@pickup_latitude,
      @pickup_longitude=@pickup_longitude,
      @dropoff_latitude=@dropoff_latitude,
      @dropoff_longitude=@dropoff_longitude
  WITH RESULT SETS ((Score float));
END
GO
```

2.  Per eseguire una prova, aprire una nuova **Query** finestra e chiamare la stored procedure, digitare i parametri per ognuna delle colonne di funzionalità.

    ```SQL
    -- Call stored procedure PredictTipSingleModeSciKitPy to score using SciKit-Learn model
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'linear_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    -- Call stored procedure PredictTipSingleModeRxPy to score using revoscalepy model
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```
    
    I valori di sette sono per le colonne di funzionalità, nell'ordine:
    
    -   *passenger_count*
    -   *trip_distance*
    -   *trip_time_in_secs*
    -   *pickup_latitude*
    -   *pickup_longitude*
    -   *dropoff_latitude*
    -   *dropoff_longitude*

3. L'output di entrambe le procedure è la probabilità di un suggerimento viene pagato il viaggio taxi con parametri o funzionalità precedente.

## <a name="conclusions"></a>Conclusioni

In questa esercitazione appreso come utilizzare il codice Python incorporato nelle stored procedure. L'integrazione con [!INCLUDE[tsql](../../includes/tsql-md.md)] rende molto più semplice per distribuire modelli di Python per la stima e incorporare la ripetizione di training del modello come parte di un flusso di lavoro di dati dell'organizzazione.

## <a name="previous-step"></a>Passaggio precedente
[Passaggio 6: Rendere operativo il modello](sqldev-py6-operationalize-the-model.md)

## <a name="see-also"></a>Vedere anche

[Servizi di Machine Learning con Python](../python/sql-server-python-services.md)

