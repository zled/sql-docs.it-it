---
title: Configurare gli strumenti client Python per l'uso con SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6f6823870060992586756dffa93aac6937d27d65
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "40401301"
---
# <a name="set-up-python-client-tools-for-use-with-sql-server-machine-learning"></a>Configurare Python gli strumenti client per l'uso con SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Integrazione di Python è disponibile a partire da SQL Server 2017 o versioni successive, quando si aggiunge che il supporto di Python di Machine Learning Services (In-Database). Per altre informazioni, vedere [installare SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md).

In questo articolo, informazioni su come configurare le workstation di sviluppo in modo che sia possibile connettersi a un Server SQL remoto abilitato per Python.

### <a name="evaluation-and-independent-development"></a>Valutazione e sviluppo indipendente
 
Se hai la developer edition e un piano per lavorare localmente a script Python di cui si prevede di spostare in SQL Server, è possibile passare direttamente al [installare un IDE](#install-ide) e scegliere lo strumento di librerie Python locale usate da SQL Server.

> [!Tip]
> Per una demo e video della procedura dettagliata, vedere [eseguire R e Python in modalità remota in Server SQL da notebook di Jupyter o qualsiasi IDE](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/) o questo [video YouTube](https://youtu.be/D5erljpJDjE).

## <a name="1---install-python-packages"></a>1: installare pacchetti Python

Workstation locale deve avere le stesse versioni di pacchetto di Python come quelli in SQL Server: revoscalepy e microsftml. I pacchetti Python aggiuntivi sono disponibili, ma vengono utilizzati più comunemente con altri scenari in un contesto di Machine Learning Server autonomo (non-istanza). 

1. Scaricare lo script della shell di installazione dal [ https://aka.ms/mls93-py ](https://aka.ms/mls93-py) (oppure usare [ https://aka.ms/mls-py ](https://aka.ms/mls-py) per il 9.2. rilascio). Lo script installa Anaconda versione 4.2.0, che include Python 3.5.2, insieme a tutti i pacchetti elencati in precedenza.

  I componenti Python vengono forniti mediante [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054&clcid=1033). Se occorre una versione diversa, vedere [download CAB](../install/sql-ml-cab-downloads.md)

2. Finestra di PowerShell aperta con autorizzazioni di amministratore con privilegi elevati (fare doppio clic su **Esegui come amministratore**).

3. Passare alla cartella in cui è stato scaricato il programma di installazione ed eseguire lo script. Aggiungere il `-InstallFolder` argomento della riga di comando per specificare un percorso della cartella per le librerie. Esempio: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls")
   ```

   Installazione richiede alcuni minuti. È possibile monitorare lo stato di avanzamento nella finestra di PowerShell. Al termine dell'installazione, si dispone di un set completo di pacchetti. Ad esempio, se è stato specificato `C:\mspythonlibs` come nome della cartella, si trovano i pacchetti in `C:\mspythonlibs\Lib\site-packages`. In caso contrario, la cartella predefinita è `C:\Program Files\Microsoft\PyForMLS1`.

Lo script di installazione non modifica la variabile di ambiente PATH nel computer in modo che il nuovo interprete python e i moduli che appena installato non sono automaticamente disponibili per gli strumenti. Per informazioni su come l'interprete Python e le librerie di collegamento agli strumenti, vedere [5: installare un IDE](#install-ide).

<a name="python-tool"></a>
 
## <a name="2---open-a-python-prompt"></a>2 - aprire un prompt dei comandi di Python

Integrazione di Python in Microsoft include gli strumenti predefiniti e i dati oltre alle librerie ai prodotti specifici, ad esempio microsoftml e revoscalepy. Gli elementi seguenti sono disponibili nelle istanze di client e server quando il programma di installazione è stata completata:

+ Dati di esempio Python
+ Distribuzione anaconda 4.2 
+ Pythonw.exe e python.exe eseguibili Python

> [!Tip] 
> È consigliabile la [Python per Windows domande frequenti su](https://docs.python.org/3/faq/windows.html) per informazioni generali purppose sull'esecuzione di programmi di Python in Windows.

### <a name="on-client-workstations"></a>Nelle workstation client

Per usare l'eseguibile di Python installato dallo script di configurazione:

1. Passare a `C:\Program Files\Microsoft\PyForMLS\python.exe` o qualsiasi percorso scelto per il percorso di installazione.

2. Fare doppio clic su **Python.exe** e selezionare **Esegui come amministratore** per aprire una finestra della riga di comando interattiva.

### <a name="on-sql-server"></a>In SQL Server

Il programma di installazione di SQL Server aggiunge gli strumenti standard di Python e le risorse a un'istanza del server. Se si utilizza l'edizione developer e si vuole controllare la versione di Python o eseguire comandi ad hoc:

1. Passare a `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

2. Fare doppio clic su **Python.exe** e selezionare **Esegui come amministratore** per aprire una finestra della riga di comando interattiva.

> [!Note]
> In generale, per evitare conflitti di risorse, è consigliabile che si **non li** eseguire Python dalla libreria di istanza nel server, se si ritiene che è possibile che l'istanza di SQL Server è in esecuzione codice Python. Tuttavia, potrebbe essere utile se si sta tentando di eseguire il debug di un problema che si verifica solo durante l'esecuzione in SQL Server e si desidera visualizzare messaggi di errore più dettagliati o assicurarsi che siano installati tutti i pacchetti necessari usando gli strumenti della libreria di istanza.

## <a name="3---permissions"></a>3 - permissions

Per connettersi a un'istanza di SQL Server per eseguire gli script e caricare i dati, è necessario un account di accesso valido nel server di database. È possibile usare un account di accesso SQL o un'autenticazione integrata di Windows. È consigliabile in genere si utilizza l'autenticazione integrata di Windows, ma utilizzando l'account di accesso SQL è più semplice per alcuni scenari.

Come minimo, l'account usato per eseguire il codice deve disporre dell'autorizzazione di lettura da database si lavora con più di un'autorizzazione speciale EXECUTE ANY EXTERNAL SCRIPT. La maggior parte degli sviluppatori anche richiedono le autorizzazioni per creare nuovi oggetti sotto forma di stored procedure che contiene lo script e scrivono dati nelle tabelle contenenti dati di training o assegnare un punteggio dei dati. 

Chiedere all'amministratore del database per configurare le autorizzazioni seguenti per l'account, nel database in cui si usano Python:

+ **EXECUTE ANY EXTERNAL SCRIPT** per l'esecuzione di Python nel server.
+ **db_datareader** privilegi per eseguire le query usate per il training del modello.
+ **db_datawriter** per scrivere dati con punteggi o dati di training.
+ **db_owner** per creare oggetti quali stored procedure, tabelle, le funzioni. 
  È anche necessario **db_owner** per creare i database di esempio e test. 

Se il codice richiede i pacchetti non installati per impostazione predefinita con SQL Server, disporre con l'amministratore del database per i pacchetti installati con l'istanza. SQL Server è un ambiente protetto ed esistono restrizioni in cui i pacchetti possono essere installati. Installazione ad hoc dei pacchetti come parte del codice non è consigliabile, anche se si dispone di diritti. Inoltre, considerare sempre con attenzione le implicazioni di sicurezza prima di installare nuovi pacchetti nella raccolta di server.

## <a name="4---test-connections"></a>4 - test delle connessioni

Dopo aver installato tutti gli strumenti e librerie, è necessario connettersi al server e verificare che è possibile creare un contesto di calcolo, o che Python possa comunicare con SQL Server.

### <a name="verify-that-revoscalepy-works-from-the-python-command-line"></a>Verificare che revoscalepy funzioni dalla riga di comando di Python

Per verificare che il **revoscalepy** modulo può essere caricato, eseguire il seguente codice di esempio da un prompt dei comandi interattiva di Python. Il codice genera un riepilogo dei dati con i dati di esempio Python e [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary). 

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

Il percorso dei dati di esempio viene stampato, in modo che sia possibile determinare quale istanza di Python viene chiamato.

### <a name="verify-that-python-can-be-called-from-a-local-sql-server"></a>Verificare che sia possibile chiamare Python da un Server SQL locale

In un ambiente di sviluppo locale, verificare che Python stia comunicando con quella locale [istanza di SQL Server configurata per la creazione di script esterni](../install/sql-machine-learning-services-windows-install.md). Usare SQL Server Management Studio per aprire una nuova **Query** finestra ed eseguire qualsiasi Python semplice comando nel contesto di una stored procedure:

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'print(3+4)'
```

Può richiedere un po' di tempo per avviare il runtime di Python per la prima volta, ma se non sono presenti errori, si sa che la finestra di avvio di SQL Server sia funzionante e Python possono essere avviati da SQL Server.

Per verificare che **revoscalepy** è disponibile nella raccolta di istanza di SQL Server, eseguire lo script basato sulla [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary), con alcune lievi modifiche per generare i risultati compatibili con SQL Server. 

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

Poiché rx_summary restituisce un oggetto di tipo `class revoscalepy.functions.RxSummary.RxSummaryResults`, che contiene più elementi, per gestire i risultati in SQL Server, è possibile estrarre semplicemente il frame di dati in un formato tabulare.

### <a name="verify-python-execution-in-sql-server-as-remote-compute-context"></a>Verificare l'esecuzione di Python in SQL Server come contesto di calcolo remoto

Se è installato **revoscalepy** nell'ambiente di sviluppo Python locale, è consigliabile essere in grado di connettersi a un'istanza remota di SQL Server 2017 in Python è stato attivato ed eseguire un esempio di codice simile usando il server come il contesto di calcolo. 

Per questa esecuzione dello script, specificare un nome server valido e un database esistente. Questo particolare script non usa il database, ma richiede la stringa di connessione.

```Python
import os
from revoscalepy import rx_summary, RxOptions, RxXdfData, RxSqlServerData, RxInSqlServer

# define connection string and compute context
sql_conn_string="Driver=SQL Server;Server=<server-name>;Database=TestDB;Trusted_Connection=True"
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

In questo esempio, viene restituito l'oggetto di riepilogo per la console, anziché restituire dati tabulari in formato corretto a SQL Server. 

Inoltre, poiché [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) è stato richiamato, i dati di esempio vengono caricati dalla cartella samples nel computer SQL Server e non dalla cartella samples locale.


<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5: installare un IDE

Se si esegue semplicemente il debug degli script dalla riga di comando, è possibile ottenere con strumenti Python standard. Tuttavia, se lo sviluppo di nuove soluzioni, o lavori da un client remoto, è consigliabile usare un IDE Python completo. Opzioni comuni sono:

+ [Visual Studio 2017 Community Edition](https://www.visualstudio.com/vs/features/python/) con Python
+ [Visual Studio tools for AI](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python)
+ Strumenti di terze parti più diffusi, ad esempio PyCharm Spyder ed Eclipse

È consigliabile Visual Studio, perché supporta progetti di database, nonché i progetti di machine learning. Per informazioni sulla configurazione di un ambiente di Python, vedere [gestione di ambienti Python in Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

Poiché gli sviluppatori lavorano frequentemente con più versioni di Python, non il programma di installazione aggiunge al percorso di Python. Per utilizzare il file eseguibile di Python e librerie installate dal programma di installazione, IDE per il collegamento **Python.exe** nel percorso che offre anche microsoftml e revoscalepy. Ad esempio, per un progetto Python in Visual Studio, un ambiente personalizzato specificherà `C:\Program Files\Microsoft\PyForMLS`, `C:\Program Files\Microsoft\PyForMLS\python.exe` e `C:\Program Files\Microsoft\PyForMLS\pythonw.exe` per **percorso di prefisso**, **cesta k interpretu**e  **Interprete con finestra**, rispettivamente.

Per altro materiale sussidiario, vedere [IDE e strumenti Python collegamento](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). L'articolo è scritto per Microsoft Machine Learning Server in modo che i percorsi di Python sono diversi, ma illustra come inserire collegamenti alle librerie di Python da vari strumenti.

## <a name="next-steps"></a>Passaggi successivi

Ora che si dispone di strumenti e una connessione attiva a SQL Server, eseguire un'esercitazione per ottenere informazioni dettagliate sul funzioni revoscalepy e il passaggio di contesti di calcolo.

> [!div class="nextstepaction"]
> [Creare un modello usando revoscalepy e un contesto di calcolo remoto](../tutorials/use-python-revoscalepy-to-create-model.md)