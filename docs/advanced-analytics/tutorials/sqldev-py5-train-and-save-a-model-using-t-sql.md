---
title: 'Passaggio 5: Eseguire il training e salvare un modello di Python con T-SQL | Documenti Microsoft'
ms.custom: ''
ms.date: 10/17/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: 1511be6615805e7842ace3e0065591c41f3b40eb
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="step-5-train-and-save-a-python-model-using-t-sql"></a>Passaggio 5: Eseguire il training e salvare un modello di Python utilizzando T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo fa parte di un'esercitazione, [analitica Python nel database per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md). 

In questo passaggio, è illustrato come eseguire il training di un modello di machine learning con i pacchetti Python **scikit-informazioni su** e **revoscalepy**. Queste librerie Python sono già installate con servizi di SQL Server Machine Learning.

Caricare i moduli e chiamare le funzioni necessarie per creare ed eseguire il training del modello tramite una stored procedure SQL Server. Il modello richiede le funzionalità di dati che è progettato nelle lezioni precedenti. Infine, si salva il modello con training per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.

> [!IMPORTANT]
> Sono state apportate numerose modifiche nel **revoscalepy** pacchetto, che ha richiesto modifiche minori nel codice per questa esercitazione. Vedere il [l'elenco delle modifiche](sqldev-py6-operationalize-the-model.md#changes) alla fine di questa esercitazione. 
> 
> Se è installato Servizi di Python utilizzando una versione provvisoria di SQL Server 2017, si consiglia di eseguire l'aggiornamento alla versione più recente. 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Suddividere i dati di esempio in set di training e set di testing

1. È possibile utilizzare la stored procedure **TrainTestSplit** per dividere i dati di nyctaxi\_tabella di esempio in due parti: nyctaxi\_esempio\_training e nyctaxi\_esempio\_test. 

    Questa stored procedure debba essere creata automaticamente, ma è possibile eseguire il codice seguente per crearla:

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

2. Per dividere i dati utilizzando una divisione personalizzata, eseguire la stored procedure, digitare un numero intero che rappresenta la percentuale di dati allocati al set di training. Ad esempio, l'istruzione seguente sarebbe allocare il 60% dei dati al set di training.

    ```SQL
    EXEC TrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Compilare un modello di regressione logistica

Dopo aver preparati i dati, è possibile utilizzare, per il training di un modello. Questo caso chiamando una stored procedure che esegue codice Python, accettando come input nella tabella di dati di training. Per questa esercitazione, creare due modelli, entrambi i modelli di classificazione binaria:

+ La stored procedure **TrainTipPredictionModelRxPy** crea un modello di stima suggerimento utilizzando il **revoscalepy** pacchetto.
+ La stored procedure **TrainTipPredictionModelSciKitPy** crea un modello di stima suggerimento utilizzando il **scikit-informazioni** pacchetto.

Ogni stored procedure utilizza i dati di input fornite per creare ed eseguire il training di un modello di regressione logistica. Viene eseguito il wrapping di tutto il codice Python in stored procedure di sistema, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Per rendere più semplice ripetere il training del modello su nuovi dati, eseguire il wrapping della chiamata a sp_execute_exernal_script in un'altra stored procedure e passare i nuovi dati di training come parametro. In questa sezione verrà illustrati il processo.

### <a name="traintippredictionmodelscikitpy"></a>TrainTipPredictionModelSciKitPy

1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], aprire una nuova **Query** finestra ed eseguire l'istruzione seguente per creare la stored procedure _TrainTipPredictionModelSciKitPy_.  La stored procedure contiene una definizione dei dati di input, pertanto non è necessario fornire una query di input.

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

    *linear_model* *0x800363736B6C6561726E2E6C696E6561....*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

Questa stored procedure utilizza il nuovo **revoscalepy** pacchetto, ovvero un nuovo pacchetto per Python. Contiene gli oggetti, trasformazione e algoritmi simili a quelli forniti per il linguaggio R **RevoScaleR** pacchetto. 

Utilizzando **revoscalepy**, è possibile creare contesti di calcolo remoto, spostare i dati tra contesti, i dati di trasformazione e training di modelli predittivi utilizzando algoritmi comuni, ad esempio la regressione logistica e lineare, gli alberi delle decisioni, di calcolo e altre. Per altre informazioni, vedere [novità revoscalepy?](../python/what-is-revoscalepy.md)

1. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], aprire una nuova **Query** finestra ed eseguire l'istruzione seguente per creare la stored procedure _TrainTipPredictionModelRxPy_.  Poiché la stored procedure include già una definizione dei dati di input, non è necessario fornire una query di input.

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
    from revoscalepy.functions.RxLogit import rx_logit
    
    ## Create a logistic regression model using rx_logit function from revoscalepy package
    logitObj = rx_logit("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
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

    - La query SELECT si applica la funzione scalare personalizzata _fnCalculateDistance_ per calcolare la distanza tra i percorsi di ritiro e deposito diretta. I risultati della query vengono archiviati nella variabile di input predefinito Python, `InputDataset`.
    - La variabile binaria _inclinato_ viene utilizzato come il *etichetta* o colonna risultato e il modello si adatta utilizzando queste colonne di funzionalità: _passenger_count_, _trip_ distanza_, _trip_time_in_secs_, e _direct_distance_.
    - Il modello con Training viene serializzato e archiviato nella variabile Python `logitObj`. Aggiungendo la parola chiave T-SQL OUTPUT, è possibile aggiungere la variabile come output della stored procedure. Nel passaggio successivo, tale variabile viene utilizzata per inserire il codice binario del modello in una tabella di database _nyc_taxi_models_. Questo meccanismo rende è più facile archiviare e riutilizzare i modelli.

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

    *rx_model* *0x8003637265766F7363616c....*

Nel passaggio successivo, utilizzare i modelli con training per creare stime.

## <a name="next-step"></a>Passaggio successivo

[Passaggio 6: Rendere operativo il modello di Python utilizzando SQL Server](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Passaggio precedente

[Passaggio 4: Creare funzionalità di dati mediante T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
