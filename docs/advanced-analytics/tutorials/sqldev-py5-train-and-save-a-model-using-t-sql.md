---
title: 'Passaggio 5: Training e salvataggio di un modello usando T-SQL | Microsoft Docs'
ms.custom: 
ms.date: 07/26/2017
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
ms.openlocfilehash: 80a47819dfbb2e96162a49730e0dcf0b1b340f07
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="step-5-train-and-save-a-model-using-t-sql"></a>Passaggio 5: Eseguire il training e salvare un modello utilizzando T-SQL

In questo passaggio, è illustrato come eseguire il training di un modello di machine learning con i pacchetti Python **scikit-informazioni su** e **revoscalepy**. Queste librerie Python sono già installate con SQL Server Machine Learning Services, pertanto è possibile caricare i moduli e chiamare le funzioni necessarie all'interno di una stored procedure. Il training del modello sarà eseguito usando le funzionalità di dati appena create. Il modello sarà poi salvato in una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Suddividere i dati di esempio in set di training e set di testing

1. Eseguire i comandi T-SQL seguenti per creare una stored procedure che divide i dati di nyctaxi\_tabella di esempio in due parti: nyctaxi\_esempio\_training e nyctaxi\_esempio\_test.

    ```SQL
    CREATE PROCEDURE [dbo].[TrainTestSplit] (@pct int)
    AS
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_training
    SELECT * into nyctaxi_sample_training FROM nyctaxi_sample WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) < @pct
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_testing
    SELECT * into nyctaxi_sample_testing FROM nyctaxi_sample
    WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) > @pct
    GO
    ```

2. Eseguire la stored procedure e digitare un numero intero che rappresenta la percentuale di dati allocati al set di training. Ad esempio, l'istruzione seguente sarebbe allocare il 60% dei dati al set di training. Set di training e dati di test vengono archiviati in due tabelle separate.

    ```SQL
    EXEC TrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model-using-scikit-learn"></a>Compila un modello di regressione logistica utilizzando scikit-informazioni su

In questa sezione creare una stored procedure che può essere usata per eseguire il training di un modello utilizzando i dati di training che è stato appena predisposto. Questa stored procedure definisce i dati di input e utilizza un **scikit-informazioni** funzione per eseguire il training di un modello di regressione logistica. Chiamare il runtime di Python che viene installato con SQL Server utilizzando la stored procedure di sistema [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Per rendere più semplice ripetere il training del modello, è possibile eseguire il wrapping della chiamata a sp_execute_exernal_script in un'altra stored procedure e passare i nuovi dati di training come parametro. In questa sezione verrà illustrati il processo.

1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], aprire una nuova **Query** finestra ed eseguire l'istruzione seguente per creare la stored procedure _TrainTipPredictionModelSciKitPy_.  Si noti che la stored procedure contiene una definizione dei dati di input, in modo che non è necessario fornire una query di input.

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelSciKitPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelSciKitPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
      EXEC sp_execute_external_script
      @language = N'Python',
      @script = N'
      import numpy
      import pickle
      import pandas
      from sklearn.linear_model import LogisticRegression
      
      ##Create SciKit-Learn logistic regression model
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      SKLalgo = LogisticRegression()
      logitObj = SKLalgo.fit(X, y)
      
      ##Serialize model
      trained_model = pickle.dumps(logitObj)
      ',
      @input_data_1 = N'
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_training
      ',
      @input_data_1_name = N'InputDataSet',
      @params = N'@trained_model varbinary(max) OUTPUT',
      @trained_model = @trained_model OUTPUT;
      ;
    END;
    GO
    ```

2. Eseguire le seguenti istruzioni SQL per inserire il modello con training nella tabella nyc\_taxi_models.

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelSciKitPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    L'elaborazione dei dati e l'adattamento del modello potrebbe richiedere un paio di minuti. I messaggi che potrebbero essere reindirizzati di Python **stdout** flusso vengono visualizzati di **messaggi** finestra di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Esempio:

    *Messaggi STDOUT dallo script esterno:*
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. Aprire la tabella *nyc\_taxi_models*. È possibile notare che è stata aggiunta una riga nuova contenente il modello serializzato nella colonna _model_.

    *linear_model* *0x800363736B6C6561726E2E6C696E6561...*

## <a name="build-a-logistic-model-using-the-revoscalepy-package"></a>Compila un modello logistic utilizzando il _revoscalepy_ pacchetto

A questo punto, creare una stored procedure diversa che utilizza il nuovo **revoscalepy** pacchetto per il training di un modello di regressione logistica. Il **revoscalepy** del pacchetto di Python contiene gli oggetti, trasformazione e algoritmi simili a quelli forniti per il linguaggio R **RevoScaleR** pacchetto. Con questa libreria, è possibile creare un contesto di calcolo, spostare dati tra i contesti di calcolo, la trasformazione dei dati ed eseguire il training di modelli predittivi utilizzando algoritmi comuni, ad esempio la regressione logistica e lineare, gli alberi delle decisioni e altro ancora. Per ulteriori informazioni, vedere [novità revoscalepy?](../python/what-is-revoscalepy.md)

1. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], aprire una nuova **Query** finestra ed eseguire l'istruzione seguente per creare la stored procedure _TrainTipPredictionModelRxPy_.  Questo modello utilizza anche i dati di training che è stato appena predisposto. Poiché la stored procedure include già una definizione dei dati di input, non è necessario fornire una query di input.

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    import pandas
    from revoscalepy.functions.RxLogit import rx_logit_ex
    
    ## Create a logistic regression model using rx_logit_ex function from revoscalepy package
    logitObj = rx_logit_ex("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    GO
    ```

    Questa stored procedure esegue i passaggi seguenti come parte del training del modello:

    - Eseguire il training di un modello di regressione logistica usando revoscalepy pacchetto su nyctaxi\_esempio\_dati di training.
    - La query SELECT usa la funzione scalare personalizzata _fnCalculateDistance_ per calcolare la distanza diretta tra la posizione di salita e discesa dei passeggeri. I risultati della query vengono archiviati nella variabile di input predefinito Python, `InputDataset`.
    - Lo script Python chiama la funzione LogisticRegression del revoscalepy, incluso in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], per creare il modello di regressione logistica.
    - La variabile binaria _tipped_ viene usata come *etichetta* o come colonna dei risultati. Il modello si adatta usando le colonne delle funzionalità seguenti:  _passenger_count_, _trip_distance_, _trip_time_in_secs_e _direct_distance_.
    - Il modello con training, incluso nella variabile Python `logitObj`viene serializzata e inserire il parametro di output [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Che l'output viene inserito nella tabella di database _nyc_taxi_models_, insieme al nome, come una nuova riga, in modo che è possibile recuperare e usarlo per le stime future.

2. Eseguire la stored procedure come indicato di seguito per inserire il modello con training **revoscalepy** modello in _nyc la tabella\_taxi\_modelli.

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    L'elaborazione dei dati e l'adattamento del modello potrebbe richiedere qualche istante. I messaggi che potrebbero essere reindirizzati di Python **stdout** flusso vengono visualizzati di **messaggi** finestra di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Esempio:

    *Messaggi STDOUT dallo script esterno:*
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. Aprire la tabella *nyc_taxi_models*. È possibile notare che è stata aggiunta una riga nuova contenente il modello serializzato nella colonna _model_.

    *rx_model* *0x8003637265766F7363616c...*

Nel passaggio successivo, utilizzare i modelli con training per creare stime.

## <a name="next-step"></a>Passaggio successivo

[Passaggio 6: Rendere operativo il modello](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Passaggio precedente

[Passaggio 4: Creare funzionalità di dati con T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

