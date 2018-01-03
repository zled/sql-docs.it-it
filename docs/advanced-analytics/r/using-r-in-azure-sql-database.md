---
title: Uso di R in Database SQL di Azure | Documenti Microsoft
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 8960f8a8c5dadaa0c53cd4fcb1ab786ce6e720a7
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="using-r-in-azure-sql-database"></a>Uso di R in Database SQL di Azure

In ottobre 2017, il team di sviluppo di SQL Server ha presentato piani di supporto dell'esecuzione di R codice nel database utilizzando le stored procedure, simile a R Services in SQL Server 2016. 

Per mantenere aggiornato sulla pianificazione versione pubblica e gli eventi, vedere il [blog di SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/) o [blog di Microsoft R Server](https://blogs.msdn.microsoft.com/rserver/).

> [!IMPORTANT]
> Attualmente l'anteprima del supporto di R è disponibile nel Database di SQL Azure in occidentale Stati Uniti centro solo e funzionalità sono limitate rispetto al numero di funzionalità per R ed esecuzione in SQL Server 2016 o 2017 del codice Python.

## <a name="whats-included"></a>Cosa è incluso

I seguenti livelli di servizio e livelli di prestazioni, è possibile utilizzare la funzionalità di R nel database:
 
- Livello di servizio Premium: P1, P2, P4, P6, P11, P15
- Premium servizio RS livello: PRS1, PRS2, PRS4, PRS6
- Pool elastico Premium: numero di 125 Edtu o versione successiva
- Pool elastici RS Premium – 125 Edtu o versione successiva

La versione di anteprima include questi pacchetti:

+   Microsoft R Open con R versione 3.3.3
+   Funzioni e i pacchetti di base R sono pre-installate
+   Microsoft R Server 9.2, tra cui il pacchetto RevoScaleR

Nella versione di anteprima corrente, è possibile eseguire le attività seguenti:

+ Training dei modelli di utilizzo di dati che si adatta in memoria
+   Assegnazione dei punteggi di modelli di utilizzo di dati che si adatta in memoria
+   Parallelismo semplice per l'esecuzione dello Script R (utilizzando la @parallel parametro in sp_execute_external_script)
+   Il flusso di esecuzione per l'esecuzione dello Script R (utilizzando @r_RowsPerRead parametro in sp_execute_external_script)
+   Eseguire un singolo script R in una sola volta


Le attività seguenti non sono supportate nella versione di anteprima di R in un Database SQL di Azure:

+ È possibile abilitare l'esecuzione di script R in un database specifico.
+ Viste a gestione dinamica fornite per il monitoraggio della CPU e utilizzo della memoria di script R non sono disponibili.
+ Può essere installato alcun pacchetto di terze parti. L'istruzione di creazione della libreria esterna non è supportata.

## <a name="example"></a>Esempio

Nel database di SQL Azure, tutti i comandi di R vengono eseguiti da T-SQL, utilizzando la stored procedure [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). 

Nell'esempio riportato di seguito viene illustrato come provare la funzionalità di anteprima, utilizzando il set di dati iris incluso in r di base.

### <a name="step-1-create-the-data-tables"></a>Passaggio 1. Creare le tabelle di dati

Iniziare creando due tabelle: uno per archiviare i dati di origine estratti da R e uno per archiviare il modello con training.

```sql
DROP TABLE IF EXISTS iris_data, iris_models;
GO
CREATE TABLE iris_data (
        id INT NOT NULL IDENTITY PRIMARY KEY
        , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
        , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
        , "Species" VARCHAR(100) NULL
);
CREATE TABLE iris_models (
    model_name VARCHAR(30) NOT NULL PRIMARY KEY,
    model VARBINARY(max) NOT NULL,
    native_model VARBINARY(MAX) NOT NULL
);
GO
```

### <a name="step-2-populate-table-with-data-from-the-iris-dataset"></a>Passaggio 2. Popolamento della tabella con i dati dal set di dati iris

Dopo aver create le tabelle, eseguire il codice seguente per inserire i dati di training nella tabella. La stored procedure sp_execute_external_script chiama R e restituisce il set di dati iris come frame di dati, utilizzando lo schema specificato nell'istruzione INSERT INTO.

```sql
INSERT INTO iris_data
("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
EXEC sp_execute_external_script @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

### <a name="step-3-create-the-stored-procedure-that-generates-the-model"></a>Passaggio 3. Creare la stored procedure che genera il modello

La seguente stored procedure esegue le operazioni di creazione e di training del modello, che può essere salvato in uno dei due formati binari effettivamente.

```sql
CREATE PROCEDURE generate_iris_model
    @trained_model VARBINARY(MAX) OUTPUT, 
    @native_trained_model VARBINARY(MAX) OUTPUT
AS
BEGIN
  EXEC sp_execute_external_script @language = N'R'
  , @script = N'
    iris_model <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris_rx_data);
    trained_model <- as.raw(serialize(iris_model, connection=NULL));
    native_trained_model <- rxSerializeModel(iris_model, realtimeScoringOnly = TRUE)
    '
  , @input_data_1 = N'SELECT "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" FROM iris_data'
  , @input_data_1_name = N'iris_rx_data'
  , @params = N'@trained_model VARBINARY(MAX) OUTPUT, @native_trained_model VARBINARY(MAX) OUTPUT
    , @trained_model = @trained_model OUTPUT
    , @native_trained_model = @native_trained_model OUTPUT;
End
```

+ Il **OUTPUT** (parola chiave) ai parametri di input indica che i valori devono essere passati e usati per l'output nonché.
+ La riga che inizia con `iris_model` definisce un modello di albero delle decisioni per stimare specie in base agli attributi fiore.
+ La chiamata a `serialize` Salva il modello in un formato binario adatto per l'archiviazione in SQL Server. 
+ In alternativa, con i modelli basati sugli algoritmi RevoScaleR, è possibile utilizzare il [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) funzione, che consente di salvare il modello in un nuovo formato binario nativo. I modelli salvati in questo formato possono essere caricati per il punteggio con la funzione di stima in SQL Server.

### <a name="step-4-train-and-save-the-model"></a>Passaggio 4. Eseguire il training e salvare il modello

Dopo aver creato la stored procedure, è possibile chiamarlo per elaborare i dati di input e creare un modello. Il codice seguente salva inoltre il modello per la tabella **iris_models**, in modo che è possibile utilizzarlo in un secondo momento per stimare specie di fiore.

```sql
DECLARE @model VARBINARY(MAX), @native_modelVARBINARY(MAX);
EXEC generate_iris_model @model OUTPUT, @native_model OUTPUT;
DELETE FROM iris_models WHERE model_name = 'iris.dtree';
INSERT INTO iris_models (model_name, model, native_model) VALUES('iris.dtree', @model, @native_model);
SELECT model_name, datalength(model)/1024. AS model_size_kb, datalength(native_model)/1024. AS native_model_size_kb FROM iris_models;
GO
```

### <a name="step-5-create-a-stored-procedure-for-scoring"></a>Passaggio 5. Creare una stored procedure per l'assegnazione dei punteggi

Successivamente, creare una stored procedure per il punteggio. Questa stored procedure carica un modello specificato dalla tabella e crea i punteggi in base ai dati di input.

```sql
CREATE PROCEDURE predict_iris_species (@model varchar(100))
AS
BEGIN
  DECLARE @rx_model VARBINARY(MAX) = (SELECT model FROM iris_models WHERE model_name = @model);
  EXEC sp_execute_external_script @language = N'R'
  , @script = N'
    irismodel<-unserialize(rx_model);
    OutputDataSet <-rxPredict(irismodel, iris_rx_data, extraVarsToWrite = c("Species", "id"));
      '
  , @input_data_1 = N'SELECT "id", "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" FROM iris_data'
  , @input_data_1_name = N'iris_rx_data'
  , @params = N'@rx_model varbinary(max)'
  , @rx_model = @rx_model
  WITH RESULT SETS ( ("setosa_Pred" FLOAT, "versicolor_Pred" FLOAT, "virginica_Pred" FLOAT, "Species.Actual" VARCHAR(100), "id" INT));
END;
GO
```

Questa stored procedure viene utilizzata la [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) funzione, ma è possibile anche utilizzare la funzione di stima nativa in T-SQL come illustrato [qui](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/09/25/announcing-general-availability-of-native-scoring-using-predict-function-in-azure-sql-database/). Utilizzo della funzione di stima è necessario utilizzare un [ **rx** modello](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler) e salvare il modello utilizzando [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel).

### <a name="step-6-use-the-stored-procedure-to-generate-predictions"></a>Passaggio 6. Utilizzare la stored procedure per generare stime

Per generare punteggi dal modello, eseguire la stored procedure. È possibile inserire i valori in una tabella o restituire le stime per un'applicazione chiamante.

```sql
EXEC predict_iris_species 'iris.dtree';
GO
```

## <a name="related-resources"></a>Risorse correlate

Azure Marketplace fornisce anche più macchine virtuali che includono 2017 di SQL Server:

+ [Eseguire il provisioning di una macchina virtuale per machine learning in Azure](provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

Vedere anche queste macchine virtuali, che sono preconfigurate con un'ampia gamma di strumenti di apprendimento automatico comune:

+ [Macchina virtuale per operazioni di data science](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview)
+ [Macchina virtuale di formazione](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)

