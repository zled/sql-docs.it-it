---
title: Passaggio 6 di rendere operativo il modello di Python usando SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: aedd6beeb720c24a6960950abc6a29c1bf89a5fa
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203473"
---
# <a name="step-6-operationalize-the-python-model-using-sql-server"></a>Passaggio 6: Rendere operativo il modello di Python utilizzando SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo fa parte di un'esercitazione, [analitica Python nel database per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md). 

In questo passaggio descritto come *rendere operative le* i modelli che è stato eseguito il training e salvato nel passaggio precedente.

In questo scenario, si intende rendere operativo distribuzione del modello nell'ambiente di produzione per il punteggio. L'integrazione con SQL Server è piuttosto semplice, poiché è possibile incorporare codice Python in una stored procedure. Per ottenere stime dal modello in base a nuovi input, chiamare la stored procedure da un'applicazione e passare i nuovi dati.

In questa lezione illustra due metodi per la creazione di stime basate su un modello di Python: batch classificazione e assegnazione dei punteggi di riga per riga.

- **Operazione di punteggio batch:** per fornire più righe di dati di input, passare una query di selezione come argomento alla stored procedure. Il risultato è una tabella di osservazioni corrispondente al case di input.
- **Assegnazione dei punteggi singoli:** passare un set di valori di parametri singoli come input.  La stored procedure restituisce una singola riga o un singolo valore.

Tutto il codice Python necessario per il punteggio viene fornito come parte delle stored procedure.

| Nome della stored procedure | Batch o singolo | Origine del modello|
|----|----|----|
|PredictTipRxPy|batch| modello revoscalepy|
|PredictTipSciKitPy|batch |scikit-informazioni su modello|
|PredictTipSingleModeRxPy|riga singola| modello revoscalepy|
|PredictTipSingleModeSciKitPy|riga singola| scikit-informazioni su modello|

## <a name="batch-scoring"></a>Punteggio batch

Le prime due stored procedure illustrano la sintassi di base per il wrapping di una chiamata di stima Python in una stored procedure. Entrambe le stored procedure è necessaria una tabella di dati come input.

- Il nome del modello esatto da utilizzare viene fornito come parametro di input per la stored procedure. La stored procedure carica il modello serializzato dalla tabella di database `nyc_taxi_models`.table, utilizzando l'istruzione SELECT nella stored procedure.
- Il modello serializzato è archiviato nella variabile Python `mod` per un'ulteriore elaborazione usando Python.
- Vengono ottenuti i nuovi case che devono essere calcolato il punteggio di [!INCLUDE[tsql](../../includes/tsql-md.md)] query specificata in `@input_data_1`. Man mano che vengono letti i dati della query, le righe vengono salvate nel frame di dati predefinito `InputDataSet`.
- Sia stored procedure usare funzioni `sklearn` per calcolare una metrica di accuratezza, AUC (area nella curva). Metriche di accuratezza, ad esempio AUC possono essere generate solo se si specifica anche l'etichetta di destinazione (il _inclinato_ colonna). Le stime non richiedono l'etichetta di destinazione (variabile `y`), ma non il calcolo di metriche di accuratezza.

    Pertanto, se non si dispone di etichette di destinazione per i dati da classificare, è possibile modificare la stored procedure per i calcoli AUC rimuovere e restituire solo le probabilità di suggerimento dalle funzionalità (variabile `X` nella stored procedure).

### <a name="predicttipscikitpy"></a>PredictTipSciKitPy

La stored procedure deve avere stato già creata per l'utente. Se si riesce a trovare, eseguire le istruzioni T-SQL seguenti per creare le stored procedure.

Questa stored procedure richiede un modello basato sul scikit-informazioni su pacchetto, poiché utilizza le funzioni specifiche per tale pacchetto:

+ Il frame di dati contenente l'input viene passato per il `predict_proba` funzione del modello di regressione logistica `mod`. Il `predict_proba` funzione (`probArray = mod.predict_proba(X)`) restituisce un **float** che rappresenta la probabilità che verrà assegnato un suggerimento (qualsiasi valore).

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

### <a name="predicttiprxpy"></a>PredictTipRxPy

Questa stored procedure utilizza gli stessi input e crea lo stesso tipo di punteggi la stored procedure precedente, ma utilizzate funzioni di **revoscalepy** pacchetto fornito con machine learning di SQL Server.

> [!NOTE] 
> Il codice per questa stored procedure è stato modificato leggermente tra prime versioni rilasciate e la versione RTM, in modo da riflettere le modifiche al pacchetto revoscalepy. Vedere il [modifiche](#changes) tabella per informazioni dettagliate.

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
      from sklearn import metrics
      from revoscalepy.functions.RxPredict import rx_predict;
      
      mod = pickle.loads(lmodel2)
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      probArray = rx_predict(mod, X)
      prob_list = prob_array["tipped_Pred"].values 
      
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

## <a name="run-batch-scoring-using-a-select-query"></a>Esecuzione dell'assegnazione punteggio batch utilizzando una query di selezione

Le stored procedure **PredictTipSciKitPy** e **PredictTipRxPy** richiedono due parametri di input: 

- La query che recupera i dati per l'assegnazione dei punteggi
- Il nome di un modello con training

Passando gli argomenti per la stored procedure, è possibile selezionare un particolare modello o modificare i dati utilizzati per l'assegnazione dei punteggi.

1. Utilizzare il **scikit-informazioni su** del modello per il punteggio, chiamare la stored procedure **PredictTipSciKitPy**, passando il nome del modello e stringa di query come input.

    ```SQL
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    La stored procedure restituisce la probabilità stimate per ogni versione di andata e ritorno passato come parte della query di input. 
    
    Se si utilizza SQL Server Management Studio (SQL Server Management Studio) per l'esecuzione di query, le probabilità verranno visualizzati come una tabella di **risultati** riquadro. Il **messaggi** riquadro restituisce la metrica di accuratezza (AUC o area nella curva) con un valore pari a circa 0,56.

2. Utilizzare il **revoscalepy** del modello per il punteggio, chiamare la stored procedure **PredictTipRxPy**, passando il nome del modello e stringa di query come input.

    ```SQL
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>Assegnazione dei punteggi a riga singola

In alcuni casi, invece di punteggio batch, si potrebbe decidere di passare in un singolo case, il recupero di valori da un'applicazione e la restituzione di un singolo risultato in base a tali valori. Ad esempio, è possibile impostare un foglio di lavoro Excel, l'applicazione web o report per chiamare la stored procedure e passare a tale input digitati o selezionati dagli utenti.

In questa sezione si apprenderà come creare stime singole chiamando due stored procedure:

+ [PredictTipSingleModeSciKitPy](#PredictTipSingleModeSciKitPy) è progettato per il punteggio di singola riga mediante il scikit-informazioni su modello.
+ [PredictTipSingleModeRxPy](#PredictTipSingleModeRxPy) è progettato per il punteggio di singola riga utilizzando il modello revoscalepy.
+ Se non hai training ancora un modello, tornare alla [passaggio 5](sqldev-py5-train-and-save-a-model-using-t-sql.md)!

Entrambi i modelli di accettano come input una serie di valori singoli, ad esempio il numero di passeggeri, la distanza di andata e ritorno e così via. Una funzione con valori di tabella, `fnEngineerFeatures`, viene utilizzato per convertire i valori di latitudine e longitudine dagli input a una nuova funzionalità, indirizzare distanza. [Lezione 4](sqldev-py4-create-data-features-using-t-sql.md) contiene una descrizione di questa funzione con valori di tabella.

Entrambe le stored procedure creano un punteggio in base al modello di Python.

> [!NOTE]
> 
> È importante specificare tutte le funzionalità di input richieste dal modello Python quando si chiama la stored procedure da un'applicazione esterna. Per evitare errori, potrebbe essere necessario eseguire il cast o convertire i dati di input in un tipo di dati di Python, oltre alla convalida tipo di dati e lunghezza dei dati.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

È opportuno esaminare il codice della stored procedure che esegue l'assegnazione dei punteggi usando il **scikit-informazioni** modello.

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

La stored procedure seguente esegue l'assegnazione dei punteggi usando il **revoscalepy** modello.

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
      from revoscalepy.functions.RxPredict import rx_predict;
      
      # Load model and unserialize
      mod = pickle.loads(model)
      
      # Get features for scoring from input data
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      
      # Score data to get tip prediction probability as a list (of float)
      
      probArray = rx_predict(mod, X)
      
      probList = []
      prob_list = prob_array["tipped_Pred"].values
      
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

### <a name="generate-scores-from-models"></a>Generare punteggi da modelli

Dopo aver create le stored procedure, è facile generare un punteggio in base a entrambi i modelli. La semplice apertura di un nuovo **Query** finestra e digitare o incollare i parametri per ognuna delle colonne di funzionalità. I sette necessari sono i valori per queste colonne di funzionalità, nell'ordine:
    
+ *passenger_count*
+ *trip_distance* v*trip_time_in_secs*
+ *pickup_latitude*
+ *pickup_longitude*
+ *dropoff_latitude*
+ *dropoff_longitude*

1. Per generare una stima utilizzando il **revoscalepy** modello, eseguita l'istruzione seguente:
  
    ```SQL
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

2. Per generare un punteggio usando il **scikit-informazioni** modello, eseguita l'istruzione seguente:

    ```SQL
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'linear_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

L'output di entrambe le procedure è la probabilità di un suggerimento viene pagato il viaggio taxi con i parametri specificati o le funzionalità.

### <a name="changes"></a> Modifiche

In questa sezione elenca le modifiche al codice utilizzati in questa esercitazione. Queste modifiche sono state apportate in modo da riflettere la versione più recente **revoscalepy** versione. Per informazioni sull'API, vedere [Python funzione riferimenti alla libreria](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference).

| Modificare i dettagli | Note|
| ----|----|
| eliminare `import pandas` in tutti i campioni| pandas caricati per impostazione predefinita|
| funzione `rx_predict_ex` modificata in `rx_predict`| Le versioni RTM e definitive richiedono `rx_predict_ex`|
| funzione `rx_logit_ex` modificata in `rx_logit`| Le versioni RTM e definitive richiedono `rx_logit_ex`|
| ` probList.append(probArray._results["tipped_Pred"])` modificato in `prob_list = prob_array["tipped_Pred"].values`| aggiornamenti all'API|

Se è installato Servizi di Python utilizzando una versione provvisoria di SQL Server 2017, si consiglia di eseguire l'aggiornamento. È inoltre possibile aggiornare solo i componenti di Python e R usando la versione più recente del Server di Machine Learning. Per ulteriori informazioni, vedere [utilizzando l'associazione per aggiornare un'istanza di SQL Server](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="conclusions"></a>Conclusioni

In questa esercitazione appreso come utilizzare il codice Python incorporato nelle stored procedure. L'integrazione con [!INCLUDE[tsql](../../includes/tsql-md.md)] rende molto più semplice per distribuire modelli di Python per la stima e incorporare la ripetizione di training del modello come parte di un flusso di lavoro di dati dell'organizzazione.

## <a name="previous-step"></a>Passaggio precedente

[Passaggio 5: Eseguire il training e salvare un modello di Python](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>Vedere anche

[Servizi di Machine Learning con Python](../python/sql-server-python-services.md)
