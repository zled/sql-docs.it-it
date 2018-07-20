---
title: Utilizzo del modello di Python in SQL per il training e assegnazione dei punteggi | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 02ffd5a25c076ef5a65a6e3a998aae485e37d982
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085023"
---
# <a name="use-python-model-in-sql-for-training-and-scoring"></a>Usare il modello di Python in SQL per il training e assegnazione dei punteggi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Nel [lezione precedente](wrap-python-in-tsql-stored-procedure.md), si è appreso il modello comune per l'uso di Python con SQL. Si è appreso che Python codice deve restituire un frame di dati chiaramente definiti e può facoltativamente restituire come output più variabili scalari o binarie. Si è appreso che le stored procedure SQL deve essere progettata per passare il tipo di dati corretto in Python e gestire i risultati.

In questa sezione si usa questo stesso modello per addestrare un modello sui dati che aggiunti a SQL Server e Salva il modello in una tabella di SQL Server:

+ Si progetta una stored procedure che chiama un Python di machine learning (funzione).
+ La stored procedure richiede dati da SQL Server da utilizzare nel training del modello.
+ La stored procedure restituisce un modello con training come una variabile binaria. 
+ Si salva il modello con training, inserendo il modello di variabile in una tabella. 

## <a name="create-the-stored-procedure-and-train-a-python-model"></a>Creare la stored procedure ed eseguire il training di un modello Python

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

2. Se questo comando viene eseguito senza errori, una nuova stored procedure viene creata e aggiunto al database. È possibile trovare le stored procedure in Management Studio **Esplora oggetti**, in **programmabilità**.

3. A questo punto eseguire la stored procedure.

    ```sql
    EXEC generate_iris_model
    ```

    Viene visualizzato un errore, perché sono ancora state fornite che richiede l'input della stored procedure.

    "Procedura o funzione 'generate_iris_model' prevede il parametro '\@trained_model', che non è stato specificato."

4. Per generare il modello con gli input obbligatori e salvarlo in una tabella richiede alcune istruzioni aggiuntive:

    ```sql
    DECLARE @model varbinary(max);
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values('Naive Bayes', @model);
    ```

5. A questo punto, provare a eseguire il codice di generazione del modello ancora una volta. 

    È necessario ottenere l'errore: "violazione del vincolo PRIMARY KEY non è possibile inserire la chiave duplicata nell'oggetto 'dbo.iris_models'. Il valore di chiave duplicata è (Naive Bayes) ".

    Ciò avviene perché è stato specificato il nome del modello digitando manualmente in "Naive Bayes" come parte dell'istruzione INSERT. Supponendo che si intende creare un numero elevato di modelli, usando i diversi parametri o algoritmi diversi a ogni esecuzione, è consigliabile impostare gli uno schema di metadati in modo che è possibile assegnare automaticamente i modelli e identificare più facilmente in.

6. Per risolvere questo errore, è possibile apportare alcune modifiche secondarie per il wrapper SQL. Questo esempio genera un nome di modello univoco aggiungendo la data e ora correnti:

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
    | Naive Bayes gennaio 2018 01 alle 09:00: 39 | 0x800363736B6C656172... |
    | Naive Bayes Feb 01 2018 10 51 AM | 0x800363736B6C656172... |

## <a name="generate-scores-from-the-model"></a>Generare punteggi da modello

Infine, è possibile caricare tale modello dalla tabella in una variabile e restituirla al Python per generare punteggi.

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

    La stored procedure Ottiene il modello Naïve Bayes dalla tabella e Usa le funzioni associate al modello per generare punteggi. In questo esempio, la stored procedure Ottiene il modello della tabella utilizzando il nome del modello. Tuttavia, a seconda di quale tipo di metadati da salvare con il modello, è possibile anche ottenere il modello più recente o il modello di con la precisione più elevata.

2. Eseguire le seguenti righe per passare il nome del modello "Naive Bayes" per la stored procedure che esegue il codice di assegnazione dei punteggi. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    Quando si esegue la stored procedure, viene restituito un frame Python. La seguente riga di T-SQL consente di specificare lo schema per i risultati restituiti: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`

    È possibile inserire i risultati in una tabella nuova o restituirle a un'applicazione.

    In questo esempio è stato reso semplice utilizzando i dati dal set di dati iris Python per l'assegnazione dei punteggi. (Vedere la riga `iris_data[[1,2,3,4]])`.) Tuttavia, in genere si sarebbe eseguire una query SQL per ottenere i nuovi dati e passarlo in Python come `InputDataSet`. 

### <a name="remarks"></a>Note

Se è abituati a usare in Python, è possibile il caricamento dei dati, creare alcuni riepiloghi e grafici, quindi un modello di training e generazione di punteggi nelle stesse 250 righe di codice.

Tuttavia, se l'obiettivo consiste nel rendere operativo il processo (la creazione di modelli, assegnazione dei punteggi e così via) in SQL Server, è importante prendere in considerazione modi che è possibile separare il processo in passaggi ripetibili che possono essere modificati usando i parametri. Quanto più possibile, si desidera che il codice Python che vengono eseguiti in una stored procedure di aver chiaramente definito gli input e output che eseguono il mapping a stored procedure input e output.

Inoltre, in genere per migliorare le prestazioni, separando il processo di esplorazione dei dati dai processi di training di un modello o generazione di punteggi. 

Punteggio e i processi di training possono spesso essere ottimizzati, sfruttando le funzionalità di SQL Server, ad esempio l'elaborazione parallela, o tramite algoritmi in [revoscalepy](../python/what-is-revoscalepy.md) oppure [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) tale supporto di streaming e l'esecuzione parallela, anziché usare le librerie Python standard. 

## <a name="next-lesson"></a>Lezione successiva

Nella lezione finale si esegue codice Python da un client remoto, l'utilizzo di SQL Server come contesto di calcolo. Questo passaggio è facoltativo, se si ha un client Python oppure non si intende eseguire Python di fuori di una stored procedure.

+ [Creare un modello revoscalepy da un client Python](use-python-revoscalepy-to-create-model.md)
