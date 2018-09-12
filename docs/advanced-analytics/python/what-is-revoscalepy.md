---
title: Introduzione a revoscalepy pacchetto Python in SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f1d4d8bbb47c34fce61bdb95a3184a1d2b10f4d1
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889477"
---
# <a name="introducing-revoscalepy-in-sql-server-machine-learning"></a>Introduzione a revoscalepy in SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** è una nuova libreria Python fornite da Microsoft per supportare l'elaborazione distribuita, remoto contesti di calcolo e gli algoritmi ad alte prestazioni per gli sviluppatori di Python.

Si basa il **RevoScaleR** pacchetto per R, che è stato fornito in Microsoft R Server e SQL Server R Services e mira a fornire la stessa funzionalità:

+ Supporta più contesti di calcolo, locali e remoti
+ Fornisce funzioni equivalenti a quelli in RevoScaleR per la visualizzazione e la trasformazione dei dati
+ Fornisce le versioni di Python di RevoScaleR algoritmi di machine learning per l'elaborazione distribuita o parallela
+ Miglioramento delle prestazioni, incluso l'uso delle librerie Intel math

Sono anche disponibili pacchetti di MicrosoftML per R e Python. Per altre informazioni, vedere [MicrosoftML con SQL Server](../using-the-microsoftml-package.md)

## <a name="versions-and-supported-platforms"></a>Versioni e piattaforme supportate

Il **revoscalepy** modulo è disponibile solo quando si installa uno dei seguenti prodotti Microsoft:

+ Machine Learning Services, in SQL Server 2017
+ Microsoft Machine Learning Server 9.2.0 o versione successiva

Per ottenere la versione più recente di revoscalepy, installare l'aggiornamento cumulativo 1 per SQL Server 2017. Include molti miglioramenti in Python, tra cui:

+ Una nuova funzione Python `rx_create_col_info`, che ottiene informazioni sullo schema da un'origine dati di SQL Server, ad esempio [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) per 
+ Miglioramenti [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) per supportare gli scenari paralleli utilizzando il `RxLocalParallel` contesto di calcolo. 

## <a name="supported-functions-and-data-types"></a>Tipi di dati e funzioni supportati

In questa sezione viene fornita una panoramica di Python e tipi di dati supportate in nuove funzioni di Python il **revoscalepy** module, a partire dalla versione di SQL Server 2017 CTP 2.0. 

Per un elenco aggiornato delle funzioni nelle librerie di Python alla data di rilascio, vedere i collegamenti seguenti:

+ [revoscalepy per Python](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

+ [microsoftml per Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

### <a name="data-types-data-sources-and-compute-contexts"></a>Tipi di dati, origini dati e contesti di calcolo

SQL Server e Python usare diversi tipi di dati in alcuni casi. Per un elenco dei mapping tra tipi di dati SQL e Python, vedere [estensione Python](../concepts/extension-python.md).

Origini dati supportate per machine learning con Python in SQL Server include le origini dati ODBC, database di SQL Server e file locali, inclusi i file XDF.

Si crea l'oggetto origine dati usando funzioni elencate nella tabella seguente. Dopo aver definito l'origine dati, si caricano o trasformare i dati tramite un'apposita [funzione ETL](#bkmk_etl).

> [!IMPORTANT]
> Numero di nomi di funzione è cambiati dalla versione iniziale di Python nella versione CTP 2.0.

**Dati di SQL Server**

+ Uso [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) per definire un'origine dati da una query o una tabella
+ Uso [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserver) per creare un contesto di calcolo di SQL Server
+ Uso [RxOdbcData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxodbcdata) per creare un'origine dati da una connessione ODBC

**revoscalepy** supporta anche il [origine dati XDF](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxxdfdata), usato per spostare dati tra memoria e altre origini dati.

> [!TIP]
> Se si ha familiarità con l'idea di origini dati o contesti di calcolo, è consigliabile iniziare leggendo sul funzionamento dell'elaborazione distribuita per machine learning in [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction).


### <a name="bkmk_algorithms"></a>Machine learning e funzioni di riepilogo

I seguenti algoritmi di machine learning e riepilogo funzioni RevoScaleR sono inclusi in SQL Server 2017, a partire da CTP 2.0.

| Funzione| Description|Note|
| ------ | ------ |------ |
|`rx_btrees` | Adattare gli alberi delle decisioni con Boosting a gradienti stocastica|`rx_btrees_ex` Nella versione CTP 2.0|
|`rx_dforest` | Adattare la classificazione e regressione foreste delle decisioni|`rx_dforest_ex` Nella versione CTP 2.0|
|`rx_dtree` | Alberi di classificazione e regressione appropriati |`rx_dtree_ex` Nella versione CTP 2.0|
|`rx_lin_mod` | Creare un modello lineare|`rx_lin_mod_ex` Nella versione CTP 2.0|
|`rx_logit` | Creare un modello di regressione logistica|`rx_logit_ex` Nella versione CTP 2.0|
|`rx_predict` | Generare stime tramite un modello con training|`rx_predict_ex` Nella versione CTP 2.0|
|`rx_summary` | Generare un riepilogo del modello||

Nuovi algoritmi di machine learning vengono anche forniti dalla versione di Python [MicrosoftML](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package):

| Funzione| Description|
| ------ | ------ |
|`rx_fast_forest` |Creare un modello di foresta delle decisioni|
|`rx_fast_linear` | Regressione lineare con stochastic dual ascent di coordinate|
|`rx_fast_trees` | Creare un modello di albero con Boosting |
|`rx_logistic_regression` | Creare un modello di regressione logistica|
|`rx_neural_network` | Creare un modello di rete neurale personalizzabile |
|`rx_oneclass_svm` | Crea un modello SVM su un set di dati sbilanciati, per l'uso nel rilevamento delle anomalie|

> [!TIP]
> Molti di questi algoritmi sono già forniti come moduli in Azure Machine Learning.

MicrosoftML per Python include anche un'ampia gamma di trasformazioni e le funzioni di supporto, ad esempio:

+ `rx_predict` Genera stime da un modello con training e può essere usato per l'assegnazione dei punteggi in tempo reale
+ funzioni di definizione delle funzionalità di immagine
+ funzioni per l'estrazione di elaborazione e del sentiment del testo

Per informazioni dettagliate, vedere [Introduzione a MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> La community di Python Usa convenzioni di codifica che potrebbero essere diverse da che cosa che già usi, tra cui tutte le lettere minuscole e caratteri di sottolineatura anziché convenzione camel per i nomi dei parametri. Inoltre, forse si è notato che la **revoscalepy** libreria è sempre minuscola. Giusto! Un'altra convenzione di Python.
> 
> Consultare i suggerimenti sulla documentazione di riferimento di Python per Microsoft R: [Guida per la funzione Python][Python funzione help](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="examples"></a>Esempi

È possibile eseguire il codice che include **revoscalepy** funzioni in locale o in un contesto di calcolo remoto. È anche possibile eseguire Python all'interno di SQL Server consiste nell'incorporare codice Python in una stored procedure.

Quando si esegue localmente, in genere eseguire uno script di Python dalla riga di comando o da un ambiente di sviluppo Python e specificare un contesto di calcolo di SQL Server utilizzando uno dei **revoscalepy** funzioni. È possibile usare il contesto di calcolo remoto per tutto il codice o per le singole funzioni. Ad esempio, è possibile eseguire l'offload di training del modello per il server di usare i dati più recenti e di evitare lo spostamento dei dati.

Se si desidera inserire uno script completo di Python all'interno di stored procedure [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), si consiglia di riscrivere il codice come una singola funzione che è chiaramente definito gli input e output. Input e output deve essere **pandas** frame di dati. Quando questa operazione, è possibile chiamare la stored procedure da qualsiasi client che supporta T-SQL, facilmente passare le query SQL come input e salvare i risultati in tabelle SQL. Per un esempio, vedere [Analitica di Python nel Database per sviluppatori SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-remote-compute-contexts"></a>Uso di contesti di calcolo remoti

+ [Creare un modello usando revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)

  In questo esempio viene illustrato come eseguire Python con un'istanza di SQL Server come contesto di calcolo.

### <a name="using-a-stored-procedure"></a>Utilizzando una stored procedure

+ [Eseguire Python con T-SQL](../tutorials/run-python-using-t-sql.md)

  In questo esempio viene illustrato il meccanismo di base della chiamata al metodo di script Python che è incorporato in una stored procedure.

### <a name="using-revoscalepy-with-microsoftml"></a>Con revoscalepy MicrosoftML

Le funzioni di Python per MicrosoftML sono integrate con i contesti di calcolo e le origini dati forniti in revoscalepy. Pertanto, è possibile usare un algoritmo di MicrosoftML per definire ed eseguire il training di un modello in Python e usare le funzioni revoscalepy per eseguire il codice Python in locale o in un contesto di calcolo di SQl Server.

Importare solo i moduli nel codice Python e quindi fare riferimento a singole funzioni che è necessario.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

### <a name="requirements"></a>Requisiti

Per eseguire codice Python in SQL Server, è necessario avere installato SQL Server 2017 con la funzionalità **servizi di Machine Learning**e abilitato il linguaggio Python. Le versioni precedenti di SQL Server non supportano l'integrazione di Python.

> [!NOTE]
> Le distribuzioni open source di Python non supportano contesti di calcolo di SQL Server. Tuttavia, se si desidera pubblicare e utilizzare le applicazioni Python da Windows, è possibile installare Microsoft Machine Learning Server senza installazione di SQL Server. Per altre informazioni, vedere [installare SQL Server 2017 Machine Learning Server (Standalone)](../install/sql-machine-learning-standalone-windows-install.md).

## <a name="get-more-help"></a>Ottenere ulteriori informazioni

Documentazione completa per queste API sarà disponibile durante il rilascio del prodotto. Nel frattempo, è consigliabile che si fanno riferimento alla funzione corrispondente nelle librerie RevoScaleR o MicrosoftML.

+ [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
+ [MicrosoftML](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)

È possibile ottenere la Guida per qualsiasi funzione Python importando il modulo e chiamando quindi `help()`. Ad esempio, l'esecuzione `help(revoscalepy)` dal tuo ambiente IDE Python restituisce un elenco di tutte le funzioni nel modulo revoscalepy, con le relative firme.

Se si usa Python Tools per Visual Studio, è possibile usare IntelliSense per ottenere la sintassi e l'argomento della Guida. Per altre informazioni, vedere [supporto di Python in Visual Studio](http://docs.microsoft.com/visualstudio/python/installation)e scaricare l'estensione che corrisponde alla versione di Visual Studio. È possibile usare Python con Visual Studio 2015 e 2017 o versioni precedenti.

## <a name="see-also"></a>Vedere anche

[Esercitazioni di Python](../tutorials/sql-server-python-tutorials.md)
