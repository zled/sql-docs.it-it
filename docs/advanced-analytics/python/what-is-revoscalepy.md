---
title: Introduzione a pacchetto di Python revoscalepy in SQL Server Machine Learning | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 450aa7cc002da9b42379330141f34ee33eedbde6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203183"
---
# <a name="introducing-revoscalepy-in-sql-server-machine-learning"></a>Introduzione a revoscalepy in SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** è una nuova libreria Python fornito da Microsoft per supportare l'elaborazione distribuita, di calcolo remoto contesti e gli algoritmi ad alte prestazioni per gli sviluppatori di Python.

È basato sul **RevoScaleR** pacchetto R, che è stato fornito in Microsoft R Server e SQL Server R Services e mira a fornire la stessa funzionalità:

+ Supporta più contesti di calcolo, locali e remoti
+ Fornisce funzioni equivalenti a quelli in RevoScaleR per la visualizzazione e la trasformazione dei dati
+ Fornisce le versioni di Python RevoScaleR algoritmi di machine learning per l'elaborazione distribuita o parallela
+ Migliorare le prestazioni, incluso l'utilizzo delle librerie matematiche Intel

I pacchetti di MicrosoftML vengono anche forniti per R e Python. Per altre informazioni, vedere [utilizzando MicrosoftML in SQL Server](../using-the-microsoftml-package.md)

## <a name="versions-and-supported-platforms"></a>Versioni e piattaforme supportate

Il **revoscalepy** modulo è disponibile solo quando si installa uno dei prodotti Microsoft seguenti:

+ Machine Learning Services, in SQL Server 2017
+ Microsoft Machine Learning Server 9.2.0 o versione successiva

Per ottenere la versione più recente di revoscalepy, installare l'aggiornamento cumulativo 1 per SQL Server 2017. Include numerosi miglioramenti Python, tra cui:

+ Una nuova funzione di Python, `rx_create_col_info`, che ottiene informazioni sullo schema da un'origine dati di SQL Server, ad esempio [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) per 
+ Miglioramenti apportati a [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) per supportare scenari paralleli tramite il `RxLocalParallel` contesto di calcolo. 

## <a name="supported-functions-and-data-types"></a>Tipi di dati e funzioni supportati

In questa sezione viene fornita una panoramica di Python e tipi di dati supportate in nuove funzioni di Python di **revoscalepy** modulo, a partire dalla versione di SQL Server 2017 CTP 2.0. 

Per un elenco aggiornato delle funzioni nelle librerie di Python alla data di rilascio, vedere i collegamenti:

+ [revoscalepy per Python](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

+ [Microsoftml per Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

### <a name="data-types-data-sources-and-compute-contexts"></a>Tipi di dati, origini dati e i contesti di calcolo

SQL Server e Python utilizzano diversi tipi di dati in alcuni casi. Per un elenco di mapping tra tipi di dati SQL e Python, vedere [Python librerie e tipi di dati](python-libraries-and-data-types.md).

Origini dati supportate per machine learning con Python in SQL Server include le origini dati ODBC, il database di SQL Server e file locali, inclusi i file con estensione XDF.

Crei l'oggetto origine dati mediante le funzioni elencate nella tabella seguente. Dopo aver definito l'origine dati, il caricamento o trasformare i dati tramite un'apposita [funzione ETL](#bkmk_etl).

> [!IMPORTANT]
> Numero di nomi di funzione è cambiati dalla versione iniziale di Python nella versione CTP 2.0.

**Dati di SQL Server**

+ Utilizzare [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) per definire un'origine dati da una query o una tabella
+ Utilizzare [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserver) per creare un contesto di calcolo di SQL Server
+ Utilizzare [RxOdbcData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxodbcdata) per creare un'origine dati da una connessione ODBC

**revoscalepy** supporta anche il [origine dati con estensione XDF](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxxdfdata), utilizzata per lo spostamento dei dati tra memoria e altre origini dati.

> [!TIP]
> Se si ha familiarità con il concetto di origini dati o contesti di calcolo, è consigliabile iniziare leggendo sul funzionamento di elaborazione distribuita per machine learning in [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction).


### <a name="bkmk_algorithms"></a>Machine learning e funzioni di riepilogo

I seguenti algoritmi di machine learning e funzioni di riepilogo da RevoScaleR sono inclusi in SQL Server 2017, a partire dalla versione CTP 2.0.

| Funzione| Description|Note|
| ------ | ------ |------ |
|`rx_btrees` | Gli alberi delle decisioni con Boosting di Adatta sfumatura stocastica|`rx_btrees_ex` Nella versione CTP 2.0|
|`rx_dforest` | Adatta una classificazione e regressione foreste delle decisioni|`rx_dforest_ex` Nella versione CTP 2.0|
|`rx_dtree` | Alberi di classificazione e regressione appropriati |`rx_dtree_ex` Nella versione CTP 2.0|
|`rx_lin_mod` | Creare un modello lineare|`rx_lin_mod_ex` Nella versione CTP 2.0|
|`rx_logit` | Creare un modello di regressione logistica|`rx_logit_ex` Nella versione CTP 2.0|
|`rx_predict` | Generare stime da un modello con training|`rx_predict_ex` Nella versione CTP 2.0|
|`rx_summary` | Generare un riepilogo del modello||

Nuovi algoritmi di machine learning vengono anche forniti dalla versione di Python [MicrosoftML](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package):

| Funzione| Description|
| ------ | ------ |
|`rx_fast_forest` |Creare un modello di foresta delle decisioni|
|`rx_fast_linear` | Regressione lineare con stocastico ascent coordinate doppio|
|`rx_fast_trees` | Creare un modello di struttura ad albero con Boosting |
|`rx_logistic_regression` | Creare un modello di regressione logistica|
|`rx_neural_network` | Creare un modello di rete neurale personalizzabile |
|`rx_oneclass_svm` | Crea un modello SVM un set di dati sbilanciati, per utilizzare il rilevamento delle anomalie|

> [!TIP]
> Molti di questi algoritmi sono già forniti come moduli in Azure Machine Learning.

MicrosoftML per Python include anche un'ampia gamma di trasformazioni e le funzioni di supporto, ad esempio:

+ `rx_predict` Genera stime da un modello con training e può essere utilizzato per l'assegnazione dei punteggi in tempo reale
+ funzioni featurization immagine
+ funzioni per l'estrazione di elaborazione e la valutazione di testo

Per informazioni dettagliate, vedere [introduzione MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> La community di Python utilizza le convenzioni di codifica che potrebbero essere diverse rispetto a ciò che si è abituati, incluse tutte le lettere minuscole e caratteri di sottolineatura anziché sulla convenzione camel per i nomi dei parametri. Inoltre, forse si notato che il **revoscalepy** libreria è sempre in minuscola. Giusto! Un'altra convenzione Python.
> 
> Consultare i suggerimenti sulla documentazione di riferimento di Python per Microsoft R: [help funzione Python][Python funzione della Guida](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="examples"></a>Esempi

È possibile eseguire il codice che include **revoscalepy** funzioni localmente o in un contesto di calcolo remoto. È anche possibile eseguire Python all'interno di SQL Server consiste nell'incorporare codice Python in una stored procedure.

Quando si esegue in locale, in genere eseguire script Python dalla riga di comando o da un ambiente di sviluppo Python e specificare un contesto di calcolo di SQL Server utilizzando uno del **revoscalepy** funzioni. È possibile utilizzare il contesto di calcolo remoto per tutto il codice o per le singole funzioni. È ad esempio eseguire l'offload di training del modello per il server di utilizzare i dati più recenti e di evitare lo spostamento dei dati.

Se si desidera inserire uno script Python completo all'interno della stored procedure, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), è consigliabile riscrivere il codice come una singola funzione che ha definito chiaramente input e output. Input e output devono essere **pandas** frame di dati. In tal caso, è possibile chiamare la stored procedure da qualsiasi client che supporta T-SQL, facilmente passare query SQL come input e salvare i risultati in tabelle SQL. Per un esempio, vedere [Analitica Python nel Database per gli sviluppatori SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-remote-compute-contexts"></a>Utilizzo di contesti di calcolo remoto

+ [Creare un modello utilizzando revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)

  In questo esempio viene illustrato come eseguire Python utilizzando un'istanza di SQL Server come contesto di calcolo.

### <a name="using-a-stored-procedure"></a>Utilizzo di una stored procedure

+ [Eseguire Python con T-SQL](../tutorials/run-python-using-t-sql.md)

  In questo esempio viene illustrato il meccanismo di base della chiamata di script Python incorporato in una stored procedure.

### <a name="using-revoscalepy-with-microsoftml"></a>Con revoscalepy MicrosoftML

Le funzioni di Python per MicrosoftML sono integrate con le origini di dati che sono state fornite nel revoscalepy e i contesti di calcolo. Pertanto, è possibile utilizzare un algoritmo MicrosoftML per definire ed eseguire il training di un modello di Python e utilizzare le funzioni revoscalepy per eseguire il codice Python localmente o in un contesto di calcolo di SQl Server.

Importa i moduli di codice Python e quindi fare riferimento le singole funzioni che è necessario.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

### <a name="requirements"></a>Requisiti

Per eseguire codice Python in SQL Server, è necessario avere installato SQL Server 2017 con la funzionalità di **Machine Learning Services**e abilitato il linguaggio Python. Le versioni precedenti di SQL Server non supportano l'integrazione di Python.

> [!NOTE]
> Contesti di calcolo di SQL Server non supportano distribuzioni Apri origine di Python. Tuttavia, se si desidera pubblicare e utilizzare le applicazioni di Python da Windows, è possibile installare Server di Microsoft Machine Learning senza installazione di SQL Server. Per altre informazioni, vedere [installazione di SQL Server 2017 Machine Learning Server (Standalone)](../install/sql-machine-learning-standalone-windows-install.md).

## <a name="get-more-help"></a>Ulteriori informazioni

La documentazione completa per queste API saranno disponibile quando viene rilasciato il prodotto. Nel frattempo, è consigliabile che la funzione corrispondente nelle librerie RevoScaleR o MicrosoftML si fa riferimento.

+ [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
+ [MicrosoftML](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)

È possibile ottenere informazioni su qualsiasi funzione Python l'importazione del modulo, e quindi chiamando `help()`. Ad esempio, in esecuzione `help(revoscalepy)` dell'IDE Python restituisce un elenco di tutte le funzioni nel modulo revoscalepy, con le rispettive firme.

Se si usa Python Tools per Visual Studio, è possibile utilizzare IntelliSense per la sintassi e l'argomento della Guida. Per ulteriori informazioni, vedere [Python supporto in Visual Studio](http://docs.microsoft.com/visualstudio/python/installation)e scaricare l'estensione che corrisponde alla versione di Visual Studio. È possibile utilizzare Python con Visual Studio 2015 e 2017, o versioni precedenti.

## <a name="see-also"></a>Vedere anche

[Esercitazioni di Python](../tutorials/sql-server-python-tutorials.md)
