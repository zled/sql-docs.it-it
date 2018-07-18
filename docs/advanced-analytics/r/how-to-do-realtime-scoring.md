---
title: Come eseguire l'assegnazione dei punteggi in tempo reale o punteggio nativo in SQL Server Machine Learning | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 91928b20316ec8555c7f309f134d083dea5c7569
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-perform-realtime-scoring-or-native-scoring-in-sql-server"></a>Come eseguire l'assegnazione dei punteggi in tempo reale o punteggio nativo in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fornisce istruzioni e il codice di esempio per come eseguire l'assegnazione dei punteggi in tempo reale e le caratteristiche di assegnazione dei punteggi native di SQL Server 2017 e SQL Server 2016. L'obiettivo di assegnazione dei punteggi in tempo reale e il punteggio nativo è per migliorare le prestazioni delle operazioni di assegnazione dei punteggi nel batch di piccole dimensioni.

Assegnazione dei punteggi in tempo reale sia native di punteggio sono progettati per consentono di utilizzare un modello di machine learning senza dover installare R. È sufficiente è ottenere un modello con training preliminare in un formato compatibile e salvarlo in un database di SQL Server.

## <a name="choosing-a-scoring-method"></a>Scelta di un metodo di assegnazione dei punteggi

Le opzioni seguenti sono supportate per la stima batch veloce:

+ **Assegnazione dei punteggi native**: funzione stimare T-SQL in SQL Server 2017
+ **Assegnazione dei punteggi in tempo reale**: tramite sp\_rxPredict stored procedure in SQL Server 2016 o in SQL Server 2017.

> [!NOTE]
> È consigliabile usare la funzione di stima in SQL Server 2017.
> Per utilizzare sp\_rxPredict richiede l'abilitazione integrazione SQLCLR. Prima di abilitare questa opzione, considerare le implicazioni di sicurezza.

Il processo generale di preparazione del modello e quindi la generazione di punteggi è simile:

1. Creare un modello usando un algoritmo supportato.
2. Serializza il modello utilizzando un formato binario speciale.
3. Rendere disponibile il modello a SQL Server. In genere, ciò significa archiviare il modello serializzato in una tabella di SQL Server.
4. Chiamare la stored procedure o funzione e passare il modello e i dati di input.

### <a name="requirements"></a>Requisiti

+ La funzione di stima è disponibile in tutte le edizioni di SQL Server 2017 ed è abilitata per impostazione predefinita. Non è necessario installare R o abilitare funzionalità aggiuntive.

+ Se si utilizza sp\_rxPredict, sono necessari alcuni passaggi aggiuntivi. Vedere [abilitare l'assegnazione dei punteggi in tempo reale](#bkmk_enableRtScoring).

+ In questo momento, è possibile creare modelli compatibili solo RevoScaleR e MicrosoftML. Tipi di modelli aggiuntivi potrebbero essere disponibili in futuro. Per l'elenco degli algoritmi attualmente supportati, vedere [assegnazione dei punteggi in tempo reale](../real-time-scoring.md).

### <a name="serialization-and-storage"></a>La serializzazione e archiviazione

Per utilizzare un modello con una delle opzioni di assegnazione dei punteggi veloce, salvare il modello utilizzando un formato serializzato speciale, cui è stato ottimizzato per dimensioni e l'efficienza di punteggio.

+ Chiamare `rxSerializeModel` per scrivere un modello supportato dal **raw** formato.
+ Chiamare `rxUnserializeModel` per ricostituire il modello per l'utilizzo in altro codice R, o per visualizzare il modello.

Per ulteriori informazioni, vedere [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel).

**Utilizzo di SQL**

Dal codice SQL, è possibile eseguire il training del modello tramite `sp_execute_external_script`e inserire direttamente i modelli con Training in una tabella, una colonna di tipo **varbinary (max)**.

Per un esempio semplice, vedere [questa esercitazione](../tutorials/rtsql-create-a-predictive-model-r.md)

**Uso di R**

Dal codice R, esistono due modi per salvare il modello in una tabella:

+ Chiamare il `rxWriteObject` (funzione), dal pacchetto RevoScaleR, scrivere il modello direttamente al database.

  Il `rxWriteObject()` funzione può recuperare gli oggetti di R da un'origine dati ODBC come SQL Server, o scrivere gli oggetti di SQL Server. L'API viene modellato in un archivio chiave-valore semplice.
  
  Se si utilizza questa funzione, assicurarsi di serializzare il modello con la nuova funzione di serializzazione. Quindi, impostare il *serializzare* argomento `rxWriteObject` su FALSE, per evitare di ripetere il passaggio di serializzazione.

+ È possibile inoltre salvare il modello in formato non elaborato in un file e quindi leggere il file in SQL Server. Questa opzione potrebbe essere utile se si sta spostando o copiando i modelli tra ambienti.

## <a name="native-scoring-with-predict"></a>Punteggio con Stima originale

In questo esempio, creare un modello e quindi chiamare la funzione di stima in tempo reale da T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Passaggio 1. Preparare e salvare il modello

Eseguire il codice seguente per creare i database di esempio e le tabelle necessarie.

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

Utilizzare l'istruzione seguente per popolare la tabella di dati con i dati di **iris** set di dati.

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
> Assicurarsi di utilizzare il [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) RevoScaleR per salvare il modello di funzione. R standard `serialize` funzione non è possibile generare il formato richiesto.

È possibile eseguire un'istruzione simile al seguente per visualizzare il modello archiviato in formato binario:

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Passaggio 2. Eseguire una stima sul modello

L'istruzione semplice PREDICT Ottiene una classificazione dal modello di albero delle decisioni utilizzando il **punteggio native** (funzione). Consente di prevedere specie iris in base agli attributi forniti, lunghezza petalo e larghezza.

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

Se viene visualizzato l'errore, "Errore durante l'esecuzione della funzione di stima. Modello è danneggiato o non valido", in genere significa che la query non ha restituito un modello. Controllare se il nome di modello sia digitato correttamente oppure se la tabella di modelli è vuota.

> [!NOTE]
> Poiché le colonne e valori restituiti da **PREDICT** possono variare in base al tipo di modello, è necessario definire lo schema dei dati restituiti tramite un **WITH** clausola.

## <a name="realtime-scoring-with-sprxpredict"></a>In tempo reale con sp_rxPredict di punteggio

In questa sezione descrive i passaggi necessari per configurare **in tempo reale** stima e fornisce un esempio di come chiamare la funzione da T-SQL.

### <a name ="bkmk_enableRtScoring"></a> Passaggio 1. Abilitare la procedura di assegnazione dei punteggi in tempo reale

È necessario abilitare questa funzionalità per ogni database che si desidera utilizzare per il punteggio. L'amministratore del server deve eseguire l'utilità della riga di comando, RegisterRExt.exe, che è incluso nel pacchetto RevoScaleR.

> [!NOTE]
> Affinché in tempo reale di lavoro di punteggio, deve essere abilitato nell'istanza; funzionalità CLR SQL Inoltre, il database deve essere contrassegnato come attendibile. Quando si esegue lo script, queste azioni vengono eseguite automaticamente. Tuttavia, prendere in considerazione le implicazioni di sicurezza aggiuntiva prima di procedere!

1. Aprire un prompt dei comandi con privilegi elevati e passare alla cartella in cui si trova RegisterRExt.exe. In un'installazione predefinita, è possibile utilizzare il seguente percorso:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Eseguire il comando seguente, sostituendo il nome di istanza e database di destinazione in cui si desidera abilitare le stored procedure estese:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Ad esempio, per aggiungere la stored procedure estesa per il database CLRPredict nell'istanza predefinita, digitare:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Il nome dell'istanza è facoltativo se il database nell'istanza predefinita. Se si utilizza un'istanza denominata, è necessario specificare il nome dell'istanza.

3. RegisterRExt.exe crea gli oggetti seguenti:

    + Assembly attendibili
    + La stored procedure `sp_rxPredict`
    + Un nuovo ruolo del database `rxpredict_users`. L'amministratore del database è possibile utilizzare questo ruolo per concedere l'autorizzazione per gli utenti che utilizzano la funzionalità di assegnazione dei punteggi in tempo reale.

4. Aggiungere tutti gli utenti che desiderano eseguire `sp_rxPredict` al nuovo ruolo.

> [!NOTE]
> 
> In SQL Server 2017, ulteriori misure di sicurezza siano soddisfatti per evitare problemi di integrazione con CLR. Queste misure impongano restrizioni aggiuntive per l'utilizzo di questa stored procedure. 

### <a name="step-2-prepare-and-save-the-model"></a>Passaggio 2. Preparare e salvare il modello

Il formato binario richiesto da sp\_rxPredict corrisponde al formato richiesto di utilizzare la funzione di stima. Pertanto, nel codice R, includere una chiamata a [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)e assicurarsi di specificare `realtimeScoringOnly = TRUE`, come nel seguente esempio:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Passaggio 3. Chiamare sp_rxPredict

Chiamare sp\_rxPredict come si sarebbe qualsiasi altra stored procedure. Nella versione corrente, la stored procedure accetta solo due parametri: _@model_ per il modello in formato binario, e _@inputData_ per i dati da utilizzare nell'assegnazione dei punteggi, definito come una query SQL valida .

Poiché il formato binario è lo stesso utilizzato dalla funzione di stima, è possibile utilizzare la tabella di modelli e dati dell'esempio precedente.

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
> La chiamata a sp\_rxPredict ha esito negativo se i dati di input per il punteggio non include colonne che corrispondono ai requisiti del modello. Attualmente, sono supportati solo i seguenti tipi di dati .NET: double, float, short, ushort, long, ulong e stringa.
> 
> Di conseguenza, potrebbe essere necessario filtrare i tipi non supportati nei dati di input prima di utilizzarlo per l'assegnazione dei punteggi in tempo reale.
> 
> Per informazioni sui tipi SQL corrispondente, vedere [Mapping dei tipi CLR SQL](https://msdn.microsoft.com/library/bb386947.aspx) o [Mapping dei dati di parametro CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-realtime-scoring"></a>Disabilitare l'assegnazione dei punteggi in tempo reale

Per disabilitare la funzionalità di assegnazione dei punteggi in tempo reale, aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente: `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="realtime-scoring-in-microsoft-r-server-or-machine-learning-server"></a>In tempo reale di punteggio in Microsoft R Server o Server di Machine Learning

Server di Machine Learning supporta distribuito in tempo reale di punteggio da modelli pubblicati come servizio web. Per altre informazioni, vedere gli articoli seguenti:

+ [Quali sono i servizi web di Machine Learning Server?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Che cos'è rendere operativo?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-operationalize-deploy-consume)
+ [Distribuire un modello di Python come un servizio web con Azure ml-modello-management-sdk](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Pubblicare un blocco di codice R o un modello in tempo reale come un nuovo servizio web](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [pacchetto mrsdeploy per R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)
