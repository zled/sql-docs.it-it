---
title: Configurare gli strumenti client Python per l'uso con SQL Server Machine Learning | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ace5ea536c020d2713f1aa07bd1b26c41065a587
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203803"
---
# <a name="set-up-python-client-tools-for-use-with-sql-server-machine-learning"></a>Configurare gli strumenti client per l'uso con SQL Server Machine Learning Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come configurare un ambiente di Python in un computer Windows per supportare l'esecuzione del codice Python in SQL Server. Sono inclusi gli scenari seguenti:

+ Testare e sviluppare le soluzioni in una workstation remota Python e inviare codice a SQL Server per l'esecuzione in un contesto di calcolo di SQL Server. 

    In genere si desidera installare un ambiente di sviluppo Python complete. 
    
    Ambiente Python locale deve essere compatibile con l'ambiente di Python sull'istanza di SQL Server ed è necessario installare librerie che supportano i contesti di calcolo remoto.

+ Sviluppare e testare il codice utilizzando gli strumenti Python dedicati e quindi il codice di eseguire la migrazione a SQL Server per l'esecuzione in una stored procedure.

    Utilizzare dell'IDE Python completa per lo sviluppo di server. Tuttavia, prima di distribuire il codice, il testing in un ambiente che emula l'ambiente di SQL Server.

+ Eseguire codice Python principalmente in una stored procedure in SQL Server e non si sviluppano codice Python. Si prevede che il codice è stato testato e debug prima eseguirne il wrapping in una stored procedure. Tuttavia, in alcuni casi potrebbe essere necessario eseguire il codice all'esterno di SQL Server, per determinare l'origine di un problema.

    Non si desidera installare gli strumenti Python nel server e utilizzeranno solo gli strumenti predefiniti installati con la distribuzione. È possibile decidere di configurare un ambiente di Python che utilizza la libreria di istanza, per verificare che funzioni nel codice di fuori di una stored procedure.

## <a name="requirements"></a>Requisiti

Indipendentemente da quali strumenti si utilizza per sviluppare il codice Python, i requisiti seguenti si applicano ogni volta che si esegue codice Python in SQL Server o utilizzare i dati di SQL Server:

+ Per utilizzare Python, è necessario SQL Server 2017 o versione successiva. È necessario installare anche la funzionalità che supporta servizi di Machine Learning (In-Database) e abilitare esplicitamente la funzionalità. Per altre informazioni, vedere [configurare SQL Server 2017](../r/set-up-sql-server-r-services-in-database.md).

    Se è stata installata una versione preliminare di SQL Server 2017, si potrebbero verificare errori se si prova a eseguire i comandi di Python da questa utilità della riga di comando. È consigliabile che si [aggiornamento alla versione più recente](#bkmk_update) se possibile. 

+ È necessario assicurarsi che l'account utilizzato per eseguire il codice disponga dell'autorizzazione per connettersi al database ed eseguire codice Python. L'autorizzazione speciale `EXECUTE ANY EXTERNAL SCRIPT` è obbligatorio per tutti gli account che utilizzano script R o Python. 

+ È necessario assicurarsi che l'account dispone di autorizzazioni di database che potrebbero essere necessarie per leggere i dati o creare nuovi oggetti. 

+ Se il codice richiede i pacchetti che non sono installati per impostazione predefinita con SQL Server, accordarsi con l'amministratore del database per includere i pacchetti installati nell'ambiente Python utilizzato dall'istanza. SQL Server è un ambiente protetto e sono presenti restrizioni in cui i pacchetti possono essere installati. 

    Installazione ad hoc dei pacchetti come parte del codice è sconsigliato, anche se si dispone di diritti. Inoltre, considerare sempre attentamente le implicazioni di sicurezza prima di installare nuovi pacchetti nella raccolta di server.

> [!NOTE]
> Se si prevede di usare Python con Machine Learning Server, che supporta contesti di calcolo aggiuntive, ad esempio Linux o Spark cluster, vedere i seguenti articoli:
> 
> + [Come installare localmente interprete e pacchetti Python personalizzati in Windows](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)
> + [Collegare gli strumenti Python e IDE per l'interprete Python installato con il Server di Machine Learning](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)

## <a name="default-tools-included-with-standard-install"></a>Strumenti predefiniti inclusi con l'installazione standard

Un'installazione predefinita di SQL Server 2017 con Machine Learning Services (In-database) e Python aggiunge le risorse e gli strumenti Python standard seguenti:

+ Dati di esempio di Python
+ Distribuzione anaconda 4.2 
+ Pythonw.exe e Python eseguibili python.exe

Per impostazione predefinita, installazione è in questa cartella: `~\Program Files\Microsoft SQL Server\<instance_name>\PYTHON_SERVICES`. 

## <a name="open-python-from-the-command-line"></a>Aprire Python dalla riga di comando 

Per utilizzare il runtime di Python che viene installato con l'istanza, è possibile avviare Python eseguibile dal percorso di installazione. Istruzioni di base sono disponibili sul [Python per domande frequenti su Windows](https://docs.python.org/3/faq/windows.html).

> [!IMPORTANT]
> In genere, per evitare conflitti di risorse, è consigliabile che si **non** eseguire Python dalla libreria istanza nel server, se si ritiene che è possibile che l'istanza di SQL Server è in esecuzione codice Python. Tuttavia, potrebbe essere utile se si sta provando a eseguire il debug di un problema che si verifica solo durante l'esecuzione in SQL Server e si desidera visualizzare messaggi di errore più dettagliati o assicurarsi che siano installati tutti i pacchetti richiesti utilizzando gli strumenti nella libreria di istanza.

1. Passare alla cartella in cui è installata la libreria di istanza. Ad esempio, in un'installazione predefinita, la cartella è `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

2. Individuare Python.exe. 

3. Mouse e scegliere **Esegui come amministratore** per aprire una finestra della riga di comando interattiva.

## <a name="bkmk_update"></a> Aggiornare i componenti di Python

È possibile aggiornare i componenti di Python scaricando e installando una versione più recente, utilizzando lo script descritto qui: [client di installare Python in Windows](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter#install-on-windows)
> 
> Il programma di installazione scaricato dallo script viene [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054&clcid=1033). Se occorre una versione diversa, vedere [installazione dei componenti di machine learning senza accesso a internet](http://bing.com)

## <a name="set-up-a-python-development-environment"></a>Configurare un ambiente di sviluppo Python

Se si esegue semplicemente il debug degli script dalla riga di comando, è possibile ottenere con gli strumenti Python standard installati con i servizi di Machine Learning o utilizzare un editor di testo. Tuttavia, se sono sviluppa nuove soluzioni o si lavora da un client remoto, è consigliabile utilizzo dell'IDE Python complete. Opzioni comuni sono:

+ [Visual Studio 2017 Community Edition](https://www.visualstudio.com/vs/features/python/) con Python
+ [Strumenti per Visual Studio](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Python nel codice di Visual Studio](https://code.visualstudio.com/docs/languages/python)
+ Strumenti di terze diffusi, ad esempio PyCharm Spyder ed Eclipse

È consigliabile Visual Studio perché supporta i progetti di database, nonché i progetti di machine learning. Per informazioni sulla configurazione di un ambiente di Python, vedere [gli ambienti di gestione di Python in Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)

## <a name="install-revoscalepy"></a>Installare revoscalepy

Anche se è installato correttamente servizi di Machine Learning, è possibile che venga visualizzato un errore durante il tentativo di caricare **revoscalepy** funzioni dalla riga di comando Python. Questi passaggi viene descritto come installare un aggiornamento per abilitare l'utilizzo di **revoscalepy**.

1. Scaricare lo script della shell di installazione dal https://aka.ms/mls93-py (oppure usare https://aka.ms/mls-py per il 9.2. versione). Lo script installa Anaconda 4.2.0, che include Python 3.5.2, insieme a tutti i pacchetti elencati in precedenza.

2. Aprire una nuova finestra di PowerShell con autorizzazioni elevate (come amministratore).

3. Aprire la cartella in cui è stato scaricato il programma di installazione ed eseguire lo script:

```ps1
cd {{download-directory}}
.\Install-PyForMLS.ps1
```

È anche possibile eseguire il `-InstallFolder` argomento della riga di comando e specificare il nuovo percorso come parte del comando. Esempio: 

```ps1
.\Install-PyForMLS.ps1 -InstallFolder "<installation_path>")
```

Se si verifica un errore, potrebbe essere necessario sospendere i criteri di esecuzione per un file specifico, la durata della sessione, come segue: 

```ps1
powershell -ExecutionPolicy Bypass -File "C:\<installation_path>\Install-PyForMLS.ps1"
```

È anche possibile sospendere i criteri di esecuzione per la durata della sessione. Con questa istruzione, i criteri di esecuzione sono impostato su `Unrestricted` per tutta la durata della sessione, non modificare la configurazione e la modifica di scrittura su disco.

```ps1
Set-ExecutionPolicy Bypass -Scope Process
```

## <a name="verify-that-python-and-revoscalepy-are-working"></a>Verificare che funzionino Python e revoscalepy

Dopo aver installato tutti gli strumenti e librerie, è consigliabile connettersi al server e verificare che è possibile creare un contesto di calcolo, o che Python possa comunicare con SQL Server.

### <a name="verify-that-revoscalepy-works-from-the-python-command-line"></a>Verificare il che funzionamento di tale revoscalepy dalla riga di comando di Python

Per verificare che il **revoscalepy** modulo può essere caricato, eseguire il seguente codice di esempio da un prompt dei comandi interattivo di Python. Il codice genera un riepilogo dei dati utilizzando i dati di esempio di Python e [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary). 

```Python
import os
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions
sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)
ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay+DayOfWeek", ds)
print(summary)
```

In modo da poter determinare quale istanza di Python viene chiamato, viene visualizzato il percorso di dati di esempio.

### <a name="verify-that-python-can-be-called-from-sql-server"></a>Verificare che sia possibile chiamare Python da SQL Server

Per verificare che Python stia comunicando con SQL Server, aprire SQL Server Management Studio. (È possibile utilizzare un altro strumento simile, ad esempio [Studio operazioni SQL](https://docs.microsoft.com/sql/sql-operations-studio/what-is).) Aprire una nuova **Query** finestra ed eseguire qualsiasi Python semplice comando nel contesto di una stored procedure:

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'print(3+4)'
```

Può richiedere qualche minuto per avviare il runtime di Python per la prima volta, ma se non siano presenti errori, significa che la finestra di avvio di SQL Server è funzioni e Python può essere avviata da SQL Server.

Per verificare che **revoscalepy** è disponibile nella raccolta di istanza di SQL Server, eseguire lo script basato sulla [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary), con alcune lievi modifiche per generare risultati compatibile con SQL Server. 

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'
import os
from pandas import DataFrame
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions

sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay + DayOfWeek", ds)
print(summary)
dfsummary = summary.summary_data_frame
OutputDataSet = dfsummary
'
WITH RESULT SETS  ((ColName nvarchar(25) , ColMean float, ColStdDev  float, ColMin  float,   ColMax  float, Col_ValidObs  float, Col_MissingObs int))
```

Poiché rx_summary restituisce un oggetto di tipo `class revoscalepy.functions.RxSummary.RxSummaryResults`, che contiene più elementi, per gestire i risultati in SQL Server, è possibile estrarre solo il frame di dati in un formato tabulare.

### <a name="verify-python-execution-in-sql-server-as-remote-compute-context"></a>Verificare l'esecuzione di Python in SQL Server come contesto di calcolo remoto

Se è stato installato **revoscalepy** nell'ambiente di sviluppo Python locale, è consigliabile essere in grado di connettersi a un'istanza di SQL Server 2017 in cui è stato abilitato Python ed eseguire un esempio di codice simili tramite il server come il calcolo contesto. 


```Python
import os
from revoscalepy import rx_summary, RxOptions, RxXdfData, RxSqlServerData, RxInSqlServer

# define connection string and compute context
sql_conn_string="Driver=SQL Server;Server=;Database=TestDB;Trusted_Connection=True"
sqlcc = RxInSqlServer(
    connection_string = sql_conn_string,
    num_tasks = 1,
    auto_cleanup = False,
    console_output = True,
    execution_timeout_seconds = 0,
    wait = True
    )
rx_set_compute_context(sqlcc)

# get sample data and path
sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

# generate summary
ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay+DayOfWeek", ds)
print(summary)
```

In questo esempio, viene restituito l'oggetto di riepilogo per la console, anziché la restituzione ben formati dati tabulari in SQL Server. 

Inoltre, poiché [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) è stato richiamato, i dati di esempio viene caricati dalla cartella degli esempi nel computer SQL Server e non dalla cartella di esempi locale.
