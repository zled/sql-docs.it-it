---
title: Configurare un client di analisi scientifica dei dati per lo sviluppo di R in SQL Server | Microsoft Docs
description: Installare gli strumenti e librerie di R locale in una workstation di sviluppo per le connessioni remote a SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 309a78a2195f55a3ec39604b0c2bd385bb06a271
ms.sourcegitcommit: 9d0ff4f3e40db48fc01788684d34719065d159b6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44724315"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Configurare un client di data science per lo sviluppo di R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dopo aver configurato un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per supportare l'apprendimento automatico, è necessario configurare un ambiente di sviluppo R che è in grado di connettersi al server per l'esecuzione remota e la distribuzione.

### <a name="evaluation-and-independent-development"></a>Valutazione e sviluppo indipendente
 
Se hai l'edizione developer e si intende lavorare localmente a script R si prevede di spostare in SQL Server, è possibile passare direttamente al [installare un IDE](#install-ide) e scegliere lo strumento locale librerie R usate da SQL Server.

> [!Tip]
> Per una demo e video della procedura dettagliata, vedere [eseguire R e Python in modalità remota in Server SQL da notebook di Jupyter o qualsiasi IDE](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/) o questo [video YouTube](https://youtu.be/D5erljpJDjE).

## <a name="1---install-r-packages"></a>1: installare pacchetti R

R la funzionalità dei prodotti Microsoft è a più livelli. Inizia con la distribuzione di Microsoft open source base R, ma viene quindi esteso con i pacchetti specifici del prodotto, ad esempio [RevoScaleR](revoscaler-overview.md), che consentono contesti di calcolo remoti e l'esecuzione parallela delle attività di R.

Operazioni coordinate tra un client e server remoto richiedono entrambi i sistemi con gli stessi pacchetti. Per ottenere l'intera stirpe delle librerie in una workstation client, installare uno dei pacchetti software nella tabella seguente. 

| Provider di librerie | Utilizzo  |
|------------------|--------------------------------|
| [Microsoft R Client](http://aka.ms/rclient/download) |  Questo download gratuito fornisce RevoScaleR, MicrosoftML e altri pacchetti R, ma prevede un limite di due thread e i dati in memoria. Tuttavia, è possibile comunque creare soluzioni R che iniziano in locale,- and -shift esecuzione (detta *contesto di calcolo*) per accedere ai dati e la potenza di calcolo di un'istanza remota di SQL Server. Questo è l'approccio consigliato per l'integrazione client con un'istanza di SQL Server di produzione. Per altre informazioni su questo strumento, vedere [che cos'è Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).|
| Server autonomi | Sotto **funzionalità condivise**, il programma di installazione di SQL Server include le opzioni di installazione server autonomo per l'apprendimento di SQL Server 2016 R Services e SQL Server 2017. Questi sono i server completa, completamente separati da SQL Server, con la possibilità di connettersi a e utilizzare dati da più piattaforme di dati. Ma è possibile usare il software potenzialmente in una capacità di client per accedere a istanza di motore di database SQL Server che esegue attività R e Python. [SQL Server 2017 Machine Learning Server (Standalone)](../install/sql-machine-learning-standalone-windows-install.md) ha le stesse librerie come un'istanza di SQL Server 2017 machine learning. [SQL Server 2016 R Server (Standalone)](../install/sql-r-standalone-windows-install.md) ha le stesse librerie di SQL Server 2016 R Services. |


<a name="r-tool"></a>
 
## <a name="2---open-an-r-prompt"></a>2 - aprire un prompt dei comandi di R

Quando si installa R con SQL Server, si ottengono gli stessi strumenti R standard per le installazioni di base di R, ad esempio RGui e Rterm così via. Questi strumenti sono leggeri, utile per controllo delle informazioni del pacchetto e di libreria, l'esecuzione di comandi ad hoc o uno script o avanzando istruzione per le esercitazioni. È possibile utilizzare questi strumenti per ottenere informazioni sulla versione di R e verificare la connettività.

Per usare la versione di R installata con SQL Server o R Client, aprire un prompt di R dalla cartella del programma Client R o SQL Server. I passaggi seguenti sono per R Client e RGui.exe.

1. Per R Client, andare a `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64`.
2. Fare doppio clic su **RGui.exe** per avviare una sessione di R con un prompt dei comandi di R.

Quando si avvia una sessione di R da una cartella di programma Microsoft, diversi pacchetti, tra cui RevoScaleR, caricato automaticamente. Immettere **Search ()** al prompt di R per conferma.

   ![Informazioni sulla versione durante il caricamento di R](../install/media/rclient-rgui-r-prompt.png "aprire un prompt dei comandi di R")

### <a name="tool-list-and-location"></a>Elenco di strumenti e posizione

| Strumento | Description | 
|------|-------------|
| **RTerm**: | Un terminale della riga di comando per l'esecuzione di script R | 
| **RGui.exe** | Un semplice editor interattivo per R. Gli argomenti della riga di comando sono gli stessi per RGui.exe e RTerm. |
| **RScript** | Uno strumento da riga di comando per l'esecuzione di script R in modalità batch. |

Strumenti si trovano nella **bin** cartella per i Client R o R di base come SQL Server installato. I percorsi seguenti sono percorsi validi per gli strumenti, a seconda di quale versione del prodotto e la funzionalità è installata:

| Prodotto Microsoft | Percorso dello strumento di R |
|-------------------|-----------------|
| Microsoft R Client | `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64` |
| Microsoft Machine Learning (R) Server | `~\Program Files\Microsoft\R_SERVER\bin\x64`
| SQL Server 2016 R Services | `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`|
| Server autonomo SQL Server 2016 R | `~\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64` 
| SQL Server 2017 Machine Learning Services (R) | `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`|
| Server autonomi di Machine Learning (R) di SQL Server 2017 | `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` |

## <a name="3---permissions"></a>3 - permissions

Per connettersi a un'istanza di SQL Server per eseguire gli script e caricare i dati, è necessario un account di accesso valido nel server di database. È possibile usare un account di accesso SQL o un'autenticazione integrata di Windows. È consigliabile in genere si utilizza l'autenticazione integrata di Windows, ma utilizzando l'account di accesso SQL è più semplice per alcuni scenari.

Come minimo, l'account usato per eseguire il codice deve disporre dell'autorizzazione di lettura da database si lavora con più di un'autorizzazione speciale EXECUTE ANY EXTERNAL SCRIPT. La maggior parte degli sviluppatori anche richiedono le autorizzazioni per creare nuovi oggetti sotto forma di stored procedure che contiene lo script e scrivono dati nelle tabelle contenenti dati di training o assegnare un punteggio dei dati. 

Chiedere all'amministratore del database per configurare le autorizzazioni seguenti per l'account, nel database in cui si usa r:

+ **EXECUTE ANY EXTERNAL SCRIPT** eseguire R nel server.
+ **db_datareader** privilegi per eseguire le query usate per il training del modello.
+ **db_datawriter** per scrivere dati con punteggi o dati di training.
+ **db_owner** per creare oggetti quali stored procedure, tabelle, le funzioni. 
  È anche necessario **db_owner** per creare i database di esempio e test. 

Se il codice richiede i pacchetti non installati per impostazione predefinita con SQL Server, disporre con l'amministratore del database per i pacchetti installati con l'istanza. SQL Server è un ambiente protetto ed esistono restrizioni in cui i pacchetti possono essere installati. Installazione ad hoc dei pacchetti come parte del codice non è consigliabile, anche se si dispone di diritti. Inoltre, considerare sempre con attenzione le implicazioni di sicurezza prima di installare nuovi pacchetti nella raccolta di server.

> [!Tip]
> Se non si ha familiarità con SQL Server e l'uso in un ambiente di sviluppo locale, è possibile eseguire questa esercitazione per apprendere gli account di accesso e impostazione delle autorizzazioni: [approfondimento RevoScaleR](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

## <a name="4---test-connections"></a>4 - test delle connessioni

SQL Server deve essere abilitata per [le connessioni remote](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md) ed è necessario disporre delle autorizzazioni, tra cui un account di accesso e un database a cui connettersi. I passaggi seguenti presuppongono il database, demo [NYCTaxi_Sample](../tutorials/sqldev-download-the-sample-data.md) e l'autenticazione di Windows.

 Come passaggio di verifica, usare uno strumento incorporato e RevoScaleR per confermare la connettività al server remoto.

1. Avviarsi [apertura di uno strumento R](#r-tool) sulla workstation client. RevoScaleR carica automaticamente. Ad esempio, passare a `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` e fare doppio clic **RGui.exe** per avviarla.

2. Verificare che sia operativo RevoScaleR eseguendo questo comando, che restituisce statistiche summary in un set di dati dimostrativo. Assicurarsi di che specificare un nome server valido per l'istanza di motore di database di SQL Server.

```r
connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
testQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
cc <-RxInSqlServer(connectionString=connStr)
rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=testQuery, connectionString=connStr), computeContext=cc)
```
Questo script si connette a un database nel server remoto, fornisce una query, crea un contesto di calcolo `cc` istruzioni per l'esecuzione remota del codice, offre quindi la funzione RevoScaleR **rxSummary** per restituire una statistica riepilogo dei risultati della query.

<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5: installare un IDE

Per i progetti di sviluppo prolungato e grave, è necessario installare un ambiente di sviluppo integrato (IDE). Strumenti di SQL Server e gli strumenti R incorporati sono dotati di non per lo sviluppo R pesante. Dopo aver creato codice funzionante, è possibile distribuirlo come una stored procedure per l'esecuzione in SQL Server.

Si deve puntare all'IDE le librerie R locale: di base R, RevoScaleR e così via. Esecuzione di carichi di lavoro in un Server SQL remoto si verifica durante l'esecuzione di script, quando lo script richiama un contesto di calcolo remota in SQL Server, l'accesso ai dati e le operazioni su tale server.

### <a name="rstudio"></a>RStudio

Quando si usa [RStudio](https://www.rstudio.com/), è possibile configurare l'ambiente per usare le librerie di R e i file eseguibili che corrispondono a quelle in un Server SQL remoto.

1. Controllare le versioni dei pacchetti R installate in SQL Server. Per altre informazioni, vedere [informazioni sui pacchetti R di ottenere](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).

1. Installare Microsoft R Client o una delle opzioni server autonomo per l'aggiunta di RevoScaleR e altri pacchetti R, tra cui distribuzione base di R usata dall'istanza di SQL Server. Scegliere una versione allo stesso o un livello inferiore (i pacchetti sono compatibili con le versioni precedenti) che fornisce le stesse versioni di pacchetto a quelli nel server. Per informazioni sulla versione, vedere la versione di eseguire il mapping in questo articolo: [i componenti di eseguire l'aggiornamento di R e Python](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

1. In RStudio [aggiornare il percorso di R](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) in modo che punti all'ambiente R fornendo RevoScaleR, Microsoft R Open e altri pacchetti Microsoft. A seconda del modo in cui è stato acquistato RevoScaleR e altre librerie, è probabilmente uno dei percorsi seguenti:

  + C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library
  + C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library
  + C:\Programmi\Microsoft Files\Microsoft\R Client\R_SERVER\bin\x64

### <a name="r-tools-for-visual-studio-rtvs"></a>R Tools per Visual Studio (RTVS)

Se si ha già un IDE preferito per R, è consigliabile **R Tools per Visual Studio**.

+ [Scarica gli strumenti R per Visual Studio (RTVS)](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [Le istruzioni di installazione](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio) -RTVS è disponibile in diverse versioni di Visual Studio.
+ [Introduzione a R Tools per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Connettersi a SQL Server da RTVS

Questo esempio Usa Visual Studio 2017 Community Edition, con il carico di lavoro analisi scientifica dei dati installato.

1. Dal **File** dal menu **New** e quindi selezionare **progetto**.

2. Nel riquadro a sinistra contiene un elenco di modelli preinstallati. Fare clic su **R**e selezionare **progetto R**. Nel **Name** , digitare `dbtest` e fare clic su **OK**. 

  Visual Studio crea una nuova cartella di progetto e un file di script predefinito, `Script.R`. 

3. Tipo `.libPaths()` sulla prima riga dello script di file e quindi premere CTRL + INVIO.

  Il percorso della libreria R corrente deve essere visualizzato nei **R interattivo** finestra. 

4. Scegliere il **R Tools** dal menu **Windows** per visualizzare un elenco di altre finestre specifici di R che è possibile visualizzare nell'area di lavoro.
 
    + Visualizzare la Guida per i pacchetti nella libreria corrente, premere CTRL + 3.
    + Vedere le variabili R nel **Esplora variabili**, premendo CTRL + 8.

5. Creare una stringa di connessione a un'istanza di SQL Server e usare la stringa di connessione nel costruttore RxInSqlServer per creare un oggetto origine dati di SQL Server. 

    ```r
    connStr <- "Driver=SQL Server;Server=MyServer;Database=MyTestDB;Uid=;Pwd="
    sqlShareDir <- paste("C:\\AllShare\\", Sys.getenv("USERNAME"), sep = "")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    cc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    sampleDataQuery <- "SELECT TOP 100 * from [dbo].[MyTestTable]"
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, connectionString = connStr, rowsPerRead = 500)
    ```
    > [!TIP]
    > Per eseguire un batch, selezionare le righe che si desidera eseguire e premere CTRL + INVIO.

6. Impostare il contesto di calcolo per il server e quindi eseguire codice R semplice sui dati.

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    I risultati vengono restituiti nel **R interattivo** finestra.
    
    Se si desidera assicurarsi che il codice è in esecuzione nell'istanza di SQL Server, è possibile usare i Profiler per creare una traccia.

## <a name="next-steps"></a>Passaggi successivi

Due diverse esercitazioni includono gli esercizi in modo da consentire l'esercitazione cambiato il contesto di calcolo da locale a un'istanza remota di SQL Server.

+ [Esercitazione: Funzioni RevoScaleR usano R con dati di SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Procedura dettagliata end-to-end per l'analisi scientifica dei dati](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)