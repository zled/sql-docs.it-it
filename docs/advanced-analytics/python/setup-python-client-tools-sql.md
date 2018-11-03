---
title: Configurare un client Python per l'uso con SQL Server Machine Learning | Microsoft Docs
description: Configurare un ambiente locale di Python per le connessioni remote a servizi di SQL Server Machine Learning con Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b328d6c44dd8f75e3d74a3abe74f3324f31e1409
ms.sourcegitcommit: 12779bddd056a203d466d83c4a510a97348fe9d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216625"
---
# <a name="set-up-a-python-client-for-use-with-sql-server-machine-learning"></a>Configurare un client Python per l'uso con SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Integrazione di Python è disponibile a partire da SQL Server 2017 o versioni successive quando si include l'opzione di Python in un [installazione di Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md). 

In questo articolo, informazioni su come configurare una workstation di sviluppo client di Python in modo che sia possibile connettersi a un Server SQL remoto abilitata per l'integrazione di Python e apprendimento automatico. Questo esercizio Usa i notebook di Jupyter per eseguire il codice Python. Dopo aver completato i passaggi descritti in questo articolo, si avranno le stesse librerie di Python come quelli in SQL Server. Inoltre, si saprà come trasferire i calcoli da una sessione di Python locale a una sessione remota di Python in SQL Server.

> [!Tip]
> Per una dimostrazione video degli esercizi in questo articolo, vedere [eseguire R e Python in modalità remota in Server SQL da notebook di Jupyter](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/).

> [!Note]
> Un'alternativa all'installazione delle sole librerie client usa un server autonomo. È possibile che alcuni clienti preferiscono per altro lavoro scenario end-to-end usare autonoma server come un rich client. Se si dispone di un [server autonomo](../install/sql-machine-learning-standalone-windows-install.md) come specificato durante l'installazione di SQL Server, si dispone di un server di Python che è completamente disaccoppiato da un'istanza di motore di database di SQL Server. Un server standalon include la distribuzione di base open source di Anaconda e le librerie specifiche di Microsoft. È possibile trovare l'eseguibile di Python in questa posizione: `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`. Come convalida dell'installazione e rich client, aprire una [notebook di Jupyter](#python-tools) per eseguire i comandi usano il Python.exe nel server.

## <a name="1---install-python-packages"></a>1: installare pacchetti Python

Workstation locale deve avere le stesse versioni di pacchetto di Python come quelli in SQL Server, incluse la distribuzione di base e i pacchetti di specifiche di Microsoft [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) e [microsftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Il [gestione di modelli di Azure ml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk) pacchetto viene installato anche, ma si applica alle attività di operazionalizzazione associata a un contesto di Machine Learning Server autonomo (non-istanza). Per analitica nel database in un'istanza di SQL Server, operazionalizzazione avviene tramite le stored procedure.

1. Scaricare lo script di installazione per installare Anaconda versione 4.2.0 con Python 3.5.2 e i tre elencate in precedenza pacchetti Microsoft.

  + [https://aka.ms/mls-py](https://aka.ms/mls-py) Se SQL Server 2017 non è associato (caso comune). Se non si è certi, scegliere lo script.

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py) Se l'istanza di SQL Server remoto [associato a Machine Learning Server 9.3](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

2. Aprire una finestra di PowerShell con autorizzazioni di amministratore con privilegi elevati (fare doppio clic su **Esegui come amministratore**).

3. Passare alla cartella in cui è stato scaricato il programma di installazione ed eseguire lo script. Aggiungere il `-InstallFolder` argomento della riga di comando per specificare un percorso della cartella per le librerie. Esempio: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

Se si omette la cartella di installazione, il valore predefinito è c:\Programmi\Microsoft Files\Microsoft\PyForMLS.

Installazione richiede alcuni minuti. È possibile monitorare lo stato di avanzamento nella finestra di PowerShell. Al termine dell'installazione, si dispone di un set completo di pacchetti. 

> [!Tip] 
> È consigliabile la [Python per Windows domande frequenti su](https://docs.python.org/3/faq/windows.html) per informazioni generali purppose sull'esecuzione di programmi di Python in Windows.

## <a name="2---locate-executables"></a>2 - individuare i file eseguibili

Ancora in PowerShell, passare alla cartella di installazione per verificare il percorso del Python.exe, script e altri pacchetti. 

1. Immettere `cd \` per passare all'unità radice e quindi immettere il percorso specificato per `-InstallFolder` nel passaggio precedente. Se si omette questo parametro durante l'installazione, il valore predefinito è `cd C:\Program Files\Microsoft\PyForMLS`.

2. Immettere `dir *.exe` per elencare i file eseguibili. Si noterà **python.exe**, **pythonw.exe**, e **anaconda.exe disinstallare**.

  ![Elenco di file eseguibili di Python](media/powershell-python-exe.png)
   
Nei sistemi con più versioni di Python, ricordarsi di usare questa particolare Python.exe se si desidera caricare **revoscalepy** e altri pacchetti Microsoft.

> [!Note] 
> Lo script di installazione non modifica la variabile di ambiente PATH nel computer, il che significa che il nuovo interprete python e i moduli che appena installato non sono automaticamente disponibili ad altri strumenti che è possibile. Per informazioni su come l'interprete Python e le librerie di collegamento agli strumenti, vedere [installare un IDE](#install-ide).

<a name="python-tool"></a>

## <a name="3---open-jupyter-notebooks"></a>3 - aprire Jupyter notebook

Anaconda include notebook di Jupyter. Come passaggio successivo, creare un notebook ed eseguire codice Python che contiene le librerie che appena installato.

1. Al prompt di Powershell, passare alla cartella scripts da aprire notebook di Jupyter:

   ```powershell
   .\Scripts\jupyter-notebook
   ```

  Un blocco appunti dovrebbe aprire nel browser predefinito in `http://localhost:8889/tree`.

2. Fare clic su **New** e quindi fare clic su **Python 3**.

  ![notebook di jupyter con Python 3 nuova selezione](media/jupyter-notebook-new-p3.png)

3. Immettere `import revoscalepy` ed eseguire il comando a uno carico delle librerie specifiche di Microsoft.

4. Immettere una serie più complessa di istruzioni. Questo esempio genera le statistiche di riepilogo usando [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) su un set di dati locale. Altre funzioni di ottenere la posizione dei dati di esempio e creare un oggetto origine dati per un file con estensione xdf locale.

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

Lo screenshot seguente mostra l'input e una parte dell'output, tagliata per brevità.

  ![notebook di jupyter che mostra revoscalepy input e output](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4 - ottenere le autorizzazioni di SQL

Per connettersi a un'istanza di SQL Server per eseguire gli script e caricare i dati, è necessario un account di accesso valido nel server di database. È possibile usare un account di accesso SQL o un'autenticazione integrata di Windows. È consigliabile in genere si utilizza l'autenticazione integrata di Windows, ma utilizzando l'account di accesso SQL è più semplice per alcuni scenari, in particolare quando lo script contiene le stringhe di connessione ai dati esterni.

Come minimo, l'account usato per eseguire il codice deve disporre dell'autorizzazione di lettura da database si lavora con più di un'autorizzazione speciale EXECUTE ANY EXTERNAL SCRIPT. La maggior parte degli sviluppatori, inoltre, richiedono le autorizzazioni per creare le stored procedure e scrivere dati in tabelle contenenti dati di training o assegnare un punteggio dei dati. 

Chiedere all'amministratore del database per configurare le autorizzazioni seguenti per l'account, nel database in cui si usano Python:

+ **EXECUTE ANY EXTERNAL SCRIPT** per l'esecuzione di Python nel server.
+ **db_datareader** privilegi per eseguire le query usate per il training del modello.
+ **db_datawriter** per scrivere dati con punteggi o dati di training.
+ **db_owner** per creare oggetti quali stored procedure, tabelle, le funzioni. 
  È anche necessario **db_owner** per creare i database di esempio e test. 

Se il codice richiede i pacchetti non installati per impostazione predefinita con SQL Server, disporre con l'amministratore del database per i pacchetti installati con l'istanza. SQL Server è un ambiente protetto ed esistono restrizioni in cui i pacchetti possono essere installati. Installazione ad hoc dei pacchetti come parte del codice non è consigliabile, anche se si dispone di diritti. Inoltre, considerare sempre con attenzione le implicazioni di sicurezza prima di installare nuovi pacchetti nella raccolta di server.

## <a name="5---test-remote-connection"></a>5: test della connessione remota

Prima di tentare questo passaggio successivo, assicurarsi di avere le autorizzazioni per l'istanza di SQL Server e una stringa di connessione per il [database di esempio Iris](../tutorials/demo-data-iris-in-sql.md). Se il database non esiste e disporre di autorizzazioni sufficienti, è possibile [creare un database con queste istruzioni inline](#create-iris-remotely).

Sostituire la stringa di connessione con i valori validi. Il codice di esempio Usa `"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"` ma il codice deve specificare un server remoto, eventualmente con un nome di istanza e un'opzione delle credenziali che viene eseguito il mapping all'account di accesso di database utente.

### <a name="define-a-function"></a>Definire una funzione

Il codice seguente definisce una funzione che verrà inviata a SQL Server in un passaggio successivo. Quando viene eseguito, Usa i dati e le librerie (revoscalepy, pandas, matplotlib) nel server remoto per creare grafici a dispersione del set di dati iris. Restituisce il bytestream del PNG al notebook di Jupyter per eseguire il rendering nel browser.

```python
def send_this_func_to_sql():
    from revoscalepy import RxSqlServerData, rx_import
    from pandas.tools.plotting import scatter_matrix
    import matplotlib.pyplot as plt
    import io
    
    # remember the scope of the variables in this func are within our SQL Server Python Runtime
    connection_string = "Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"
    
    # specify a query and load into pandas dataframe df
    sql_query = RxSqlServerData(connection_string=connection_string, sql_query = "select * from iris_data")
    df = rx_import(sql_query)
    
    scatter_matrix(df)
    
    # return bytestream of image created by scatter_matrix
    buf = io.BytesIO()
    plt.savefig(buf, format="png")
    buf.seek(0)
    
    return buf.getvalue()
```

### <a name="send-the-function-to-sql-server"></a>La funzione di invio a SQL Server

In questo esempio, creare il contesto di calcolo remoto e quindi inviare l'esecuzione della funzione a SQL Server con [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec). Il **rx_exec** funzione è utile in quanto accetta un contesto di calcolo come argomento. Qualsiasi funzione che si desidera eseguire in modalità remota deve avere un argomento di contesto di calcolo. Alcune funzioni, ad esempio [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) supportano direttamente in questo argomento. Per le operazioni che non, è possibile usare **rx_exec** per inviare il codice in un contesto di calcolo remoto.

In questo esempio, non i dati non elaborati dovevano essere trasferito da SQL Server per il Notebook di Jupyter. Tutti i calcoli avvengono all'interno del database di Iris e il client viene restituito solo il file di immagine.

```python
from IPython import display
import matplotlib.pyplot as plt 
from revoscalepy import RxInSqlServer, rx_exec

# create a remote compute context with connection to SQL Server
sql_compute_context = RxInSqlServer(connection_string=connection_string.format(new_db_name))

# use rx_exec to send the function execution to SQL Server
image = rx_exec(send_this_func_to_sql, compute_context=sql_compute_context)[0]

# only an image was returned to my jupyter client. All data remained secure and was manipulated in my db.
display.Image(data=image)
```

Lo screenshot seguente mostra l'output di tracciato di input e a dispersione.

  ![notebook di jupyter che Mostra output di grafico a dispersione](media/jupyter-notebook-scatterplot.png)

## <a name="6---link-ide-to-pythonexe"></a>6 - collegamento IDE Python.exe

Se si esegue semplicemente il debug degli script dalla riga di comando, è possibile ottenere con strumenti Python standard. Tuttavia, se si siano sviluppando nuove soluzioni, potrebbe essere necessaria un ambiente IDE Python completo. Opzioni comuni sono:

+ [Visual Studio 2017 Community Edition](https://www.visualstudio.com/vs/features/python/) con Python
+ [Visual Studio tools for AI](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python)
+ Strumenti di terze parti più diffusi, ad esempio PyCharm Spyder ed Eclipse

È consigliabile Visual Studio, perché supporta progetti di database, nonché i progetti di machine learning. Per informazioni sulla configurazione di un ambiente di Python, vedere [gestione di ambienti Python in Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

Poiché gli sviluppatori lavorano frequentemente con più versioni di Python, non il programma di installazione aggiunge al percorso di Python. Per utilizzare il file eseguibile di Python e librerie installate dal programma di installazione, IDE per il collegamento **Python.exe** nel percorso che offre anche **revoscalepy** e **microsoftml**. 

Per un progetto Python in Visual Studio, un ambiente personalizzato sarebbe specificare i valori seguenti, presupponendo un'installazione predefinita.

| Impostazione di configurazione | Valore |
|-----------------------|-------|
| **Prefisso percorso** | C:\Programmi\Microsoft Files\Microsoft\PyForMLS |
| **Cesta k interpretu** | C:\Programmi\Microsoft Files\Microsoft\PyForMLS\python.exe |
| **Interprete con finestra** | C:\Programmi\Microsoft Files\Microsoft\PyForMLS\pythonw.exe |

<a name="create-iris-remotely"></a>

## <a name="optional-create-the-iris-database-remotely"></a>Facoltativo: Creare il database di Iris in modalità remota

Se si dispone delle autorizzazioni per creare un database nel server remoto, è possibile eseguire il codice seguente per creare il database di esempio Iris usato per gli esempi in questo articolo.

### <a name="1---create-the-irissql-database"></a>1 - creare il database irissql

```Python
import pyodbc

# creating a new db to load Iris sample in
new_db_name = "irissql"
connection_string = "Driver=SQL Server;Server=localhost;Database={0};Trusted_Connection=Yes;" 
                        # you can also swap Trusted_Connection for UID={your username};PWD={your password}
cnxn = pyodbc.connect(connection_string.format("master"), autocommit=True)
cnxn.cursor().execute("IF EXISTS(SELECT * FROM sys.databases WHERE [name] = '{0}') DROP DATABASE {0}".format(new_db_name))
cnxn.cursor().execute("CREATE DATABASE " + new_db_name)
cnxn.close()

print("Database created")
```

### <a name="2---import-iris-sample-from-sklearn"></a>2 - importare esempio Iris da SkLearn

```Python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3 - usare Revoscalepy APIs per creare una tabella e caricare i dati Iris

```Python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

<a name="install-ide"></a>

## <a name="next-steps"></a>Passaggi successivi

Ora che si dispone di strumenti e una connessione attiva a SQL Server, eseguire un'esercitazione per ottenere informazioni dettagliate sul funzioni revoscalepy e il passaggio di contesti di calcolo.

> [!div class="nextstepaction"]
> [Creare un modello usando revoscalepy e un contesto di calcolo remoto](../tutorials/use-python-revoscalepy-to-create-model.md)