---
title: Utilizzo del modello di Python in SQL per il training e assegnazione dei punteggi | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b7f5883356ff6878f869ee10f915bcb93a2dba17
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-python-model-in-sql-for-training-and-scoring"></a>Utilizzare il modello di Python in SQL per il training e assegnazione dei punteggi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Nel [lezione precedente](wrap-python-in-tsql-stored-procedure.md), si è appreso il modello comune per l'utilizzo di Python con SQL. Si è appreso che il Python codice deve data.frame definito chiaramente uno di output e può facoltativamente restituire più variabili scalari o binarie. Si è appreso che la stored procedure SQL deve essere progettata per passare il tipo di dati corretto in Python e gestire i risultati.

In questa sezione, utilizzare questo stesso modello per eseguire il training di un modello di dati che aggiunti a SQL Server e salvare il modello in una tabella di SQL Server:

+ Si progetta una stored procedure che chiama un Python funzione di machine learning.
+ La stored procedure richiede dati da SQL Server da utilizzare nel training del modello.
+ La stored procedure genera un modello con training come valore binario. 
+ Salvare il modello con training inserendo il modello di variabile in una tabella. 

## <a name="create-the-stored-procedure-and-train-a-python-model"></a>Creare la stored procedure e il training di un modello di Python

1. Eseguire il codice seguente in SQL Server Management Studio per creare la stored procedure che consente di compilare un modello.

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python',
    @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[[0,1,2,3]], iris_data[[4]]))
    '
    , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@trained_model varbinary(max) OUTPUT'
    , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

2. Se questo comando viene eseguito senza errori, una nuova stored procedure viene creata e aggiunto al database. È possibile trovare le stored procedure in Management Studio **Esplora oggetti**in **programmabilità**.

3. A questo punto, eseguire la stored procedure.

    ```sql
    EXEC generate_iris_model
    ```

    È necessario ottenere un errore, perché non sono state fornite che richiede l'input della stored procedure.

    "Procedura o funzione 'generate_iris_model' prevede il parametro '@trained_model', che non è stato fornito."

4. Per generare il modello con gli input obbligatori e salvarlo in una tabella richiede alcune istruzioni aggiuntive:

    ```sql
    DECLARE @model varbinary(max);
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values('Naive Bayes', @model);
    ```

5. A questo punto, provare a eseguire il codice di generazione del modello ancora una volta. 

    È necessario ottenere l'errore: "violazione del vincolo di chiave primaria non è possibile inserire la chiave duplicata nell'oggetto 'dbo.iris_models'. Il valore di chiave duplicata è (Naive Bayes) ".

    Ciò avviene perché è stato specificato il nome del modello immettendo manualmente in "Naive Bayes" come parte dell'istruzione INSERT. Supponendo che si intende creare un numero elevato di modelli di utilizzo di parametri diversi o algoritmi diversi a ogni esecuzione, è consigliabile impostare una combinazione di metadati in modo che è possibile assegnare automaticamente i modelli e identificare più facilmente in.

6. Per evitare questo errore, è possibile apportare alcune modifiche secondarie per il wrapper SQL. Questo esempio genera un nome di modello univoco aggiungendo la data e ora correnti:

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes ' + CAST(GETDATE()as varchar)
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    ```

7. Per visualizzare i modelli, eseguire un'istruzione SELECT semplice.

    ```sql
    SELECT * FROM iris_models;
    GO
    ```

    **Risultati**

    |MODEL_NAME | model |
    |------|------|
    | Naive Bayes | 0x800363736B6C656172... |
    | Naive Bayes 2018 01 gennaio 9:39 AM | 0x800363736B6C656172... |
    | Naive Bayes Feb 01 2018 10:51 AM | 0x800363736B6C656172... |

## <a name="generate-scores-from-the-model"></a>Generare punteggi da modello

Infine, si caricare questo modello dalla tabella in una variabile e passarlo al Python per generare punteggi.

1. Eseguire il codice seguente per creare la stored procedure che esegue l'assegnazione dei punteggi. 

    ```sql
    CREATE PROCEDURE predict_species (@model varchar(100))
    AS
    BEGIN
    DECLARE @nb_model varbinary(max) = (SELECT model FROM iris_models WHERE model_name = @model);
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    import pickle
    irismodel = pickle.loads(nb_model)
    species_pred = irismodel.predict(iris_data[[1,2,3,4]])
    iris_data["PredictedSpecies"] = species_pred
    OutputDataSet = iris_data.query( ''PredictedSpecies != SpeciesId'' )[[0, 5, 6]]
    print(OutputDataSet)
    '
    , @input_data_1 = N'select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@nb_model varbinary(max)'
    , @nb_model = @nb_model
    WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));
    END;
    GO
    ```

    La stored procedure Ottiene il modello Naïve Bayes dalla tabella e utilizza le funzioni associate al modello per generare punteggi. In questo esempio, la stored procedure Ottiene il modello della tabella utilizzando il nome del modello. Tuttavia, a seconda di quale tipo di metadati viene salvato con il modello, è possibile anche ottenere il modello più recente o il modello con la massima accuratezza.

2. Eseguire le seguenti righe per passare il nome del modello "Naive Bayes" per la stored procedure che esegue il codice di assegnazione dei punteggi. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    Quando si esegue la stored procedure, viene restituito un data.frame Python. Questa riga di T-SQL specifica lo schema per i risultati restituiti: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`

    È possibile inserire i risultati in una tabella nuova o ripristinare un'applicazione.

    In questo esempio è semplice utilizzando i dati dal set di dati iris Python per il punteggio. (Vedere la riga `iris_data[[1,2,3,4]])`.) Tuttavia, in genere si potrebbe eseguire una query SQL per ottenere i nuovi dati e si passa che in Python come `InputDataSet`. 

### <a name="remarks"></a>Osservazioni

Se si è abituati a lavorare in Python, potrebbe essere abituati a il caricamento dei dati, creazione di alcuni dei riepiloghi e dei grafici, quindi training di un modello e la generazione di punteggi tutti nelle stesse 250 righe di codice.

Tuttavia, se l'obiettivo consiste nel rendere operativo il processo (creazione di modelli, assegnazione dei punteggi e così via) in SQL Server, è importante considerare i modi che è possibile separare il processo passi ripetibile che può essere modificato utilizzando i parametri. Per quanto possibile, è necessario il codice Python che vengono eseguiti in una stored procedure per definire chiaramente input e output che eseguono il mapping a stored procedure input e output.

Inoltre, in genere per migliorare le prestazioni suddividendo il processo di esplorazione dei dati dai processi di training di un modello o la generazione di punteggi. 

Punteggio e i processi di formazione possono spesso essere ottimizzati sfruttando le funzionalità di SQL Server, ad esempio l'elaborazione parallela, o con gli algoritmi in [revoscalepy](../python/what-is-revoscalepy.md) o [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) il supporto di flusso e l'esecuzione parallela, anziché utilizzare le librerie standard di Python. 

## <a name="next-lesson"></a>Lezione successiva

Nell'ultima lezione, si esegue codice Python da un client remoto, l'utilizzo di SQL Server come contesto di calcolo. Questo passaggio è facoltativo, se si dispone di un client Python o non si intende eseguire Python all'esterno di una stored procedure.

+ [Creare un modello revoscalepy da un client Python](use-python-revoscalepy-to-create-model.md)
