---
title: Come eseguire l'assegnazione dei punteggi in tempo reale o assegnazione dei punteggi nativa in SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dfea308f268d666ce070c21a7dd9afa513f95406
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2018
ms.locfileid: "40395318"
---
# <a name="how-to-perform-real-time-scoring-or-native-scoring-in-sql-server"></a>Come eseguire l'assegnazione dei punteggi in tempo reale o assegnazione dei punteggi nativa in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo illustra due approcci in SQL Server per la stima dei risultati in tempo quasi reale usando i modelli con training preliminare scritti in R. Assegnazione dei punteggi in tempo reale sia di assegnazione dei punteggi nativa sono progettati per consentono di usare un modello di machine learning senza dover installare R. Dato un modello con training preliminare in un formato compatibile con - salvato in un database di SQL Server - è possibile usare tecniche di accesso ai dati standard per generare rapidamente i punteggi di stima sui nuovi input.

## <a name="choose-a-scoring-method"></a>Scegliere un metodo di assegnazione dei punteggi

Le opzioni seguenti sono supportate per le stime batch veloce:

+ **Assegnazione dei punteggi nativa**: la funzione PREDICT T-SQL nel Database SQL di Azure, SQL Server 2017 su Linux e Windows di SQL Server 2017.
+ **Assegnazione dei punteggi in tempo reale**: tramite la stored procedure sp\_rxPredict stored procedure in SQL Server 2016 o SQL Server 2017 (solo Windows).

> [!NOTE]
> È consigliabile usare la funzione PREDICT in SQL Server 2017.
> Usare sp\_rxPredict richiede l'abilitazione integrazione SQLCLR. Prima di abilitare questa opzione, prendere in considerazione le implicazioni di sicurezza.

Il processo complessivo di preparare il modello e quindi la generazione di punteggi è simile:

1. Creare un modello usando un algoritmo supportato.
2. Serializza il modello utilizzando un formato binario speciale.
3. Rendere disponibile il modello a SQL Server. In genere questo si intende archiviare il modello serializzato in una tabella di SQL Server.
4. Chiamare la stored procedure o funzione e passare il modello e i dati di input.

### <a name="requirements"></a>Requisiti

+ La funzione di stima è disponibile in tutte le edizioni di SQL Server 2017 e viene abilitata per impostazione predefinita. È necessario non installare R o abilitare le funzionalità aggiuntive.

+ Se si usa sp\_rxPredict, sono necessari alcuni passaggi aggiuntivi. Visualizzare [abilitare l'assegnazione dei punteggi in tempo reale](#bkmk_enableRtScoring).

+ A questo punto, solo RevoScaleR e MicrosoftML possono creare modelli compatibili. Tipi di modelli aggiuntivi potrebbero essere disponibili in futuro. Per l'elenco degli algoritmi attualmente supportati, vedere [punteggio in tempo reale](../real-time-scoring.md).

### <a name="serialization-and-storage"></a>Serializzazione e archiviazione

Per usare un modello con una delle opzioni di assegnazione dei punteggi veloce, salvare il modello usando un formato serializzato speciale, cui è stato ottimizzato per le dimensioni e l'efficienza di assegnazione dei punteggi.

+ Chiamare `rxSerializeModel` per scrivere un modello supportato per il **raw** formato.
+ Chiamare `rxUnserializeModel` per ricostituire il modello per l'uso in un altro codice R o per visualizzare il modello.

Per altre informazioni, vedere [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel).

**Con SQL**

Dal codice SQL, è possibile eseguire il training usando il modello `sp_execute_external_script`e inserire direttamente i modelli addestrati in una tabella, in una colonna di tipo **varbinary (max)**.

Per un esempio semplice, vedere [in questa esercitazione](../tutorials/rtsql-create-a-predictive-model-r.md)

**Uso di R**

Dal codice R, esistono due modi per salvare il modello in una tabella:

+ Chiamare il `rxWriteObject` (funzione), dal pacchetto RevoScaleR, scrivere il modello direttamente al database.

  Il `rxWriteObject()` funzione può recuperare gli oggetti R da un'origine dati ODBC, ad esempio SQL Server, o scrivere gli oggetti di SQL Server. L'API viene modellato un semplice archivio chiave-valore.
  
  Se si usa questa funzione, assicurarsi di serializzare il modello con la nuova funzione di serializzazione. Quindi, impostare il *serializzare* argomento nella `rxWriteObject` su FALSE, per evitare di ripetere il passaggio di serializzazione.

+ È possibile inoltre salvare il modello in formato non elaborato in un file e quindi leggere dal file in SQL Server. Questa opzione potrebbe essere utile se si sta spostando o copia di modelli tra ambienti.

## <a name="native-scoring-with-predict"></a>Assegnazione dei punteggi con PREDICT nativa

In questo esempio, si crea un modello e quindi chiama la funzione di stima in tempo reale da T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Passaggio 1. Preparare e salvare il modello

Eseguire il codice seguente per creare il database di esempio e le tabelle necessarie.

```SQL
CREATE DATABASE NativeScoringTest;
GO
USE NativeScoringTest;
GO
DROP TABLE IF EXISTS iris_rx_data;
GO
CREATE TABLE iris_rx_data (
  "Sepal.Length" float not null, "Sepal.Width" float not null
  , "Petal.Length" float not null, "Petal.Width" float not null
  , "Species" varchar(100) null
);
GO
```

Usare l'istruzione seguente per popolare la tabella di dati con i dati di **iris** set di dati.

```SQL
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

A questo punto, creare una tabella per archiviare i modelli.

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Il codice seguente crea un modello basato sul **iris** set di dati e lo salva nella tabella denominata **modelli**.

```SQL
DECLARE @model varbinary(max);
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'
    iris.sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
    iris.dtree <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris[iris.sub, ])
    model <- rxSerializeModel(iris.dtree, realtimeScoringOnly = TRUE)
    '
  , @params = N'@model varbinary(max) OUTPUT'
  , @model = @model OUTPUT
  INSERT [dbo].[ml_models]([model_name], [model_version], [native_model_object])
  VALUES('iris.dtree','v1', @model) ;
```

> [!NOTE] 
> Assicurarsi di usare la [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) funzione RevoScaleR per salvare il modello. R standard `serialize` funzione non è possibile generare il formato richiesto.

È possibile eseguire un'istruzione, ad esempio il comando seguente per visualizzare il modello archiviato in formato binario:

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Passaggio 2. Esecuzione di stima sul modello

L'istruzione di stima semplice seguente ottiene una classificazione dal modello di albero delle decisioni usando il **assegnazione dei punteggi nativa** (funzione). Consente di prevedere la specie di iris in base agli attributi forniti, lunghezza del petalo e larghezza.

```SQL
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

Se viene visualizzato l'errore, "Errore durante l'esecuzione della funzione PREDICT. Modello è danneggiato o non valido", in genere significa che la query non ha restituito un modello. Controllare se il nome del modello aver digitato correttamente o se la tabella di modelli è vuota.

> [!NOTE]
> Poiché le colonne e valori restituiti da **PREDICT** possono variare in base al tipo di modello, è necessario definire lo schema dei dati restituiti tramite un **WITH** clausola.

## <a name="real-time-scoring-with-sprxpredict"></a>Assegnazione dei punteggi con sp_rxPredict in tempo reale

In questa sezione vengono descritti i passaggi necessari per configurare **in tempo reale** stima e viene fornito un esempio di come chiamare la funzione di T-SQL.

### <a name ="bkmk_enableRtScoring"></a> Passaggio 1. Abilitare la procedura di assegnazione dei punteggi in tempo reale

È necessario abilitare questa funzionalità per ogni database che si desidera utilizzare per l'assegnazione dei punteggi. L'amministratore del server deve eseguire l'utilità della riga di comando, RegisterRExt.exe, che viene incluso nel pacchetto RevoScaleR.

> [!NOTE]
> Affinché il punteggio in tempo reale per funzionare, deve essere abilitato nell'istanza; la funzionalità di CLR SQL Inoltre, il database deve essere contrassegnato come attendibile. Quando si esegue lo script, queste azioni vengono eseguite automaticamente. Tuttavia, prendere in considerazione le implicazioni di sicurezza aggiuntiva prima di procedere.

1. Aprire un prompt dei comandi con privilegi elevati e passare alla cartella in cui si trova RegisterRExt.exe. In un'installazione predefinita, è possibile utilizzare il percorso seguente:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Eseguire il comando seguente, sostituendo il nome dell'istanza e database di destinazione in cui si desidera abilitare le stored procedure estese:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Ad esempio, per aggiungere la stored procedure estesa al database CLRPredict nell'istanza predefinita, digitare:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Il nome dell'istanza è facoltativo se il database nell'istanza predefinita. Se si usa un'istanza denominata, è necessario specificare il nome dell'istanza.

3. RegisterRExt.exe crea gli oggetti seguenti:

    + Assembly attendibili
    + La stored procedure `sp_rxPredict`
    + Un nuovo ruolo del database, `rxpredict_users`. L'amministratore del database è possibile usare questo ruolo per concedere autorizzazioni agli utenti che usano la funzionalità di assegnazione dei punteggi in tempo reale.

4. Aggiungere gli utenti che dovranno essere eseguiti `sp_rxPredict` al nuovo ruolo.

> [!NOTE]
> 
> In SQL Server 2017, le misure di sicurezza aggiuntive sono disponibili per evitare problemi di integrazione con CLR. Queste misure impongono restrizioni aggiuntive per l'uso di questa stored procedure. 

### <a name="step-2-prepare-and-save-the-model"></a>Passaggio 2. Preparare e salvare il modello

Il formato binario richiesto da sp\_rxPredict corrisponde al formato richiesto per usare la funzione PREDICT. Pertanto, nel codice R, includere una chiamata a [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)e assicurarsi di specificare `realtimeScoringOnly = TRUE`, come in questo esempio:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Passaggio 3. Chiamare sp_rxPredict

Si chiama sp\_rxPredict come si procederebbe per un stored procedure. Nella versione corrente, la stored procedure accetta solo due parametri:  _\@model_ per il modello in formato binario, e  _\@inputData_ per i dati da utilizzare nell'assegnazione dei punteggi, definito come una query SQL valida.

Poiché il formato binario è uguale a quello usato dalla funzione di stima, è possibile usare la tabella di modelli e i dati dell'esempio precedente.

```SQL
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree' 
AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> La chiamata a sp\_rxPredict ha esito negativo se i dati di input per il punteggio non includono colonne che corrispondono ai requisiti del modello. Attualmente, sono supportati solo i seguenti tipi di dati .NET: double, float, short, ushort, long, ulong e stringa.
> 
> Di conseguenza, potrebbe essere necessario filtrare i tipi non supportati nei dati di input prima di usarlo per assegnare i punteggi in tempo reale.
> 
> Per informazioni sui tipi SQL corrispondenti, vedere [Mapping dei tipi SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) oppure [Mapping dei dati dei parametri CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Disabilita l'assegnazione dei punteggi in tempo reale

Per disabilitare la funzionalità di assegnazione dei punteggi in tempo reale, aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente: `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="real-time-scoring-in-other-microsoft-product"></a>Assegnazione dei punteggi in tempo reale in altri prodotti Microsoft

Se si usa il server autonomo o un Microsoft Machine Learning Server invece di analitica nel database di SQL Server, sono disponibili altre opzioni oltre a stored procedure e funzioni T-SQL per la generazione di stime.

Il server autonomo e il Machine Learning Server supportano il concetto di una *servizio web* per la distribuzione di codice. È possibile aggregare una R o Python eseguito il training del modello come servizio web, chiamato in fase di esecuzione per valutare nuovi input di dati. Per altre informazioni, vedere gli articoli seguenti:

+ [Quali sono i servizi web in Machine Learning Server?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Che cos'è messa in funzione?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-operationalize-deploy-consume)
+ [Distribuire un modello Python come un servizio web con Azure ml-model-management-sdk](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Pubblicare un blocco di codice R o un modello in tempo reale come nuovo servizio web](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [pacchetto mrsdeploy per R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)
