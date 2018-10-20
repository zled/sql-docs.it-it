---
title: Usare un modello Python in SQL Server per il training e previsioni | Microsoft Docs
description: Creare ed eseguire il training di un modello usando Python e il set di dati Iris classico. Salvare il modello in SQL Server e quindi usarlo per generare i risultati stimati.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 839bcecdeaf7b5e2a7ea1297fe941353bffed20e
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461837"
---
# <a name="use-a-python-model-in-sql-server-for-training-and-scoring"></a>Usare un modello Python in SQL Server per il training e assegnazione dei punteggi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo esercizio di Python, informazioni su un modello comune per la creazione, training e tramite un modello in SQL Server. Questo esercizio crea due stored procedure. Il primo genera un modello Naïve Bayes per prevedere una specie di Iris in base alle caratteristiche del fiore. La seconda procedura sia per l'assegnazione dei punteggi. Chiama il modello generato nella prima procedura per un set di stime di output. Procedendo in questo esercizio, verrà illustrato le tecniche di base che sono fondamentali per l'esecuzione del codice Python in un'istanza di motore di database di SQL Server.

Dati di esempio usati in questo esercizio sono le [set di dati Iris](demo-data-iris-in-sql.md) nel **irissql** database.

## <a name="create-a-model-using-a-sproc"></a>Creare un modello utilizzando una stored procedure

1. Aprire una nuova finestra query in Management Studio connesso per il **irissql** database. 

    ```sql
    USE irissql
    GO
    ```

2. Eseguire il codice seguente in una nuova finestra di query per creare la stored procedure che compila ed esegue il training di un modello. I modelli archiviati per il riutilizzo in SQL Server sono serializzati come un flusso di byte e archiviati in una colonna varbinary (max) in una tabella di database. Dopo aver creato il modello, sottoposti a training, serializzati e salvati in un database, può essere chiamato da altre procedure o dalla funzione di stima T-SQL nell'assegnazione dei punteggi dei carichi di lavoro.

   Questo codice Usa pickle per serializzare il modello e scikit per fornire all'algoritmo Naïve Bayes. Il modello verrà eseguito il training usando i dati di colonne tra 0 e 4 i **iris_data** tabella. I parametri vedere nella seconda parte della procedura articolare dei dati di input e output dei modelli. 

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

3. Verificare che esista la stored procedure. Se lo script T-SQL nel passaggio precedente è stato eseguito senza errori, una nuova stored procedure denominata **generate_iris_model** viene creato e aggiunto per il **irissql** database. È possibile trovare le stored procedure in Management Studio **Esplora oggetti**, in **programmabilità**.

## <a name="execute-the-sproc-to-create-and-train-models"></a>Eseguire la stored procedure per creare ed eseguire il training di modelli

1. Dopo aver creata la stored procedure, eseguire il codice seguente sotto per eseguirlo. L'istruzione specifico per l'esecuzione di una stored procedure è `EXEC` nella quinta riga.

   Questo particolare script elimina un modello esistente con lo stesso nome ("Naive Bayes") per liberare spazio per nuovi file creati eseguendo nuovamente la stessa procedura. Senza l'eliminazione del modello, si verifica un errore che indica che l'oggetto esiste già. 

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes '
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

2. Visualizzare i risultati nell'area di output. Lo script include un'istruzione SELECT che mostra che il modello esistente. Un altro modo per restituire un elenco dei modelli consiste `SELECT * FROM iris_models` nelle **irissql**.

    **Risultati**

    |   | (Nessun nome di colonna |
    |---|-----------------|
    | 1 | Naive Bayes     | 


## <a name="create-and-execute-a-sproc-for-generating-predictions"></a>Creare ed eseguire una stored procedure per la generazione di stime

Ora che si hanno creati, sottoposti a training e salvato un modello, passare al passaggio successivo: creazione di una stored procedure che genera stime. Si sarà tal sp_execute_external_script chiamante per avviare Python e quindi passare nello script Python che carica un modello serializzato creato nell'esercizio precedente e quindi assegna per assegnare un punteggio dei dati di input.

1. Eseguire il codice seguente per creare la stored procedure che esegue l'assegnazione dei punteggi. In fase di esecuzione, questa procedura verrà caricato un modello binario, usare colonne `[1,2,3,4]` come input e specificare le colonne `[0,5,6]` come output.

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
    OutputDataSet = iris_data[[0,5,6]] 
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

2. Eseguire la stored procedure, fornendo il nome del modello "Naive Bayes" in modo che la procedura sa quale modello usare. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    Quando si esegue la stored procedure, viene restituito un frame Python. La seguente riga di T-SQL consente di specificare lo schema per i risultati restituiti: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`. È possibile inserire i risultati in una tabella nuova o restituirle a un'applicazione.

    ![Set di risultati di esecuzione di stored procedure](media/train-score-using-python-NB-model-results.png)

    I risultati sono 150 stime sui species utilizzando le caratteristiche giglio come input. Per la maggior parte delle osservazioni, specie stimato corrisponde a specie effettivo.

    In questo esempio è stato reso semplice usando il set di dati iris di Python per il training e assegnazione dei punteggi. Un approccio più tipico sarebbe prevedono l'esecuzione di una query SQL per ottenere i nuovi dati e che passare in Python come `InputDataSet`. 

## <a name="conclusion"></a>Conclusioni

In questo esercizio, si è appreso come creare le stored procedure per attività diverse, usare la stored procedure di sistema in cui ogni stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) per avviare un processo di Python. Gli input al processo di Python vengono passati allo script sp_execute_external come parametri. Script di Python stesso sia le variabili di dati in un database di SQL Server vengono passate come input.

Se è abituati a usare in Python, è possibile il caricamento dei dati, creare alcuni riepiloghi e grafici, quindi un modello di training e generazione di punteggi nelle stesse 250 righe di codice. Questo articolo è diverso da approcci consueti organizzando operazioni in procedure separate. Questa pratica è utile a vari livelli.

Un vantaggio è che è possibile separare i processi in passaggi ripetibili che possono essere modificati usando i parametri. Quanto più possibile, si desidera che il codice Python che vengono eseguiti in una stored procedure di aver chiaramente definito gli input e output su cui eseguire il mapping a stored procedure input e output che può essere passato fase di esecuzione. In questo esercizio, codice Python che consente di creare un modello, denominato "Naive Bayes" in questo esempio, viene passato come input per una seconda stored procedure che chiama il modello in un processo di assegnazione dei punteggi.

Un secondo miglioramento è corsi di formazione e i processi di assegnazione dei punteggi può essere ottimizzata, sfruttando le funzionalità di SQL Server, ad esempio l'elaborazione parallela, governance delle risorse, o usando gli algoritmi [revoscalepy](../python/what-is-revoscalepy.md) o [MicrosoftML ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) che supportano la trasmissione e l'esecuzione parallela. Separando i set di training e assegnazione dei punteggi, è possibile destinare le ottimizzazioni per i carichi di lavoro specifici.

## <a name="next-steps"></a>Passaggi successivi

Nelle esercitazioni precedenti è incentrato su esecuzione locale. Tuttavia, è possibile anche eseguire codice Python da una workstation client, usando SQL Server come contesto di calcolo remoto. Per altre informazioni sulla configurazione di una workstation client che si connette a SQL Server, vedere [configurare gli strumenti client di Python](../python/setup-python-client-tools-sql.md).

+ [Creare un modello revoscalepy da un client Python](use-python-revoscalepy-to-create-model.md)
