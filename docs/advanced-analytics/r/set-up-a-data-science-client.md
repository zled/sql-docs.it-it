---
title: Configurare un client di analisi scientifica dei dati per lo sviluppo di R in SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dd0b420630846382b9d7cf456352bb606a4f0040
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Configurare un client di analisi scientifica dei dati per lo sviluppo di R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dopo aver configurato un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per supportare l'apprendimento, è necessario impostare un ambiente di sviluppo che è in grado di connettersi al server per l'esecuzione in modalità remota e la distribuzione.

Questo articolo descrive alcuni scenari tipici del client, inclusa la configurazione dell'edizione gratuita Community di Visual Studio per eseguire codice R in SQL Server.

## <a name="install-r-libraries-on-the-client"></a>Installare le librerie di R nel client

L'ambiente client deve includere Microsoft R Open, oltre ai pacchetti RevoScaleR aggiuntivi che supportano l'esecuzione distribuita di R in SQL Server. Distribuzioni standard di R non dispone di pacchetti che supportano i contesti di calcolo remoto o l'esecuzione parallela delle attività di R.

Per ottenere queste librerie, installare uno dei seguenti:
  
+ [Microsoft R Client](http://aka.ms/rclient/download)

+ Microsoft R Server (per SQL Server 2016)

    - Per installare dal programma di installazione di SQL Server, vedere [installazione di SQL Server 2016 R Server (Standalone)](../install/sql-r-standalone-windows-install.md)

    - Per usare il programma di installazione separato basati su Windows, vedere [installare Machine Learning per Windows ReportServer](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)

+ Machine Learning Server (per SQL Server 2017)

    - Per installare dal programma di installazione di SQL Server, vedere [installazione di SQL Server 2017 Machine Learning Server (Standalone)](../install/sql-machine-learning-standalone-windows-install.md)

    - Per usare il programma di installazione separato basati su Windows, vedere [installare R Server 9.1 per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="r-tools"></a>Strumenti di R

Quando si installa R con SQL Server, si ottengono gli stessi strumenti R che vengono installati con qualsiasi **base** installazione di R, ad esempio RGui, Rterm e così via. Tecnicamente, si disporrebbe tutti gli strumenti che necessari per sviluppare e testare il codice R.

Sono inclusi i seguenti strumenti standard di R in un *installazione di base* di R e pertanto vengono installati per impostazione predefinita.

+ **RTerm**: un terminale della riga di comando per l'esecuzione di script R

+ **RGui.exe**: semplice editor interattivo per R. Gli argomenti della riga di comando sono gli stessi di RGui.exe e RTerm.

+ **RScript**: strumento da riga di comando per l'esecuzione di script R in modalità batch.

Per individuare questi strumenti, determinare la raccolta di R che è stata installata quando si configura SQL Server o della macchina autonoma funzionalità di apprendimento. Ad esempio, in un'installazione predefinita, gli strumenti di R si trovano in queste cartelle:

+ SQL Server 2016 R Services: `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Microsoft R Server autonomo: `~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ SQL Server 2017 apprendimento servizi: `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ Machine Learning Server (Standalone): `~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

Se assistenza con gli strumenti di R, aprire **RGui**, fare clic su **Guida**e selezionare una delle opzioni

## <a name="microsoft-r-client"></a>Microsoft R Client

Microsoft R è un download gratuito che consente di accedere ai pacchetti RevoScaleR per il processo di sviluppo. Installando il Client R, è possibile creare soluzioni R che possono essere eseguite in tutti i contesti di calcolo supportati, tra cui analitica nel database di SQL Server e R distribuite in Hadoop, Spark o Linux con Server di Machine Learning.

Se è già stato installato un ambiente di sviluppo R diverso, ad esempio RStudio, assicurarsi di riconfigurare l'ambiente per usare le librerie e file eseguibili forniti dal Client di Microsoft R. In questo modo è possibile utilizzare tutte le funzionalità del pacchetto RevoScaleR, anche se le prestazioni sarà limitata.

Per altre informazioni, vedere [che cos'è Microsoft R Client?](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

## <a name="install-a-development-environment"></a>Installare un ambiente di sviluppo

Se si dispone già di un ambiente di sviluppo R preferito, è consigliabile una delle operazioni seguenti:

+ R Tools for Visual Studio

    Compatibile con Visual Studio 2015.

    Per ulteriori informazioni, vedere [come installare gli strumenti R per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).
 
    Per configurare RTVS usino le librerie client di Microsoft R, vedere [su Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017

    Anche l'edizione gratuita Community include dati scienza carico di lavoro, che installa i modelli di progetto per R, Python e F #.

    Scaricare Visual Studio da [questo sito](https://www.visualstudio.com/vs/). 

+ RStudio

    Se si preferisce usare RStudio, sono necessari alcuni passaggi aggiuntivi per usare le librerie RevoScaleR:

    - Installare il Client di Microsoft R per ottenere i pacchetti necessari e le librerie.
    - Aggiornare il percorso di R per utilizzare il runtime di Microsoft R.

    Per ulteriori informazioni, vedere [Client R - configurare l'IDE](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client#step-2-configure-your-ide).

## <a name="configure-your-ide"></a>Configurare l'IDE

+ R Tools for Visual Studio

    Vedere [questo sito](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r) per alcuni esempi di come compilare ed eseguire il debug R progetti utilizzando strumenti R per Visual Studio. 

+ Visual Studio 2017

    Se si installa Microsoft R Client o Server R **prima** si installa Visual Studio, le librerie di R Server vengono automaticamente rilevate e utilizzate per il percorso della libreria. Se non è installato, le librerie di RevoScaleR dal **strumenti R** dal menu **installa R Client**.

## <a name="run-r-in-sql-server"></a>Eseguire R in SQL Server

Questo esempio viene utilizzato Visual Studio 2017 Community Edition, con il carico di lavoro dell'analisi scientifica dei dati installato.

1. Dal **File** dal menu **New** e quindi selezionare **progetto**.

2. -L'icona della mano riquadro contiene un elenco di modelli preinstallati. Fare clic su **R**e selezionare **R progetto**. Nel **nome** digitare `dbtest` e fare clic su **OK**.

3. Visual Studio crea una nuova cartella di progetto e un file di script predefinito, `Script.R`. 

4. Tipo `.libPaths()` nella prima riga dello script di file e quindi premere CTRL + INVIO.

5. Il percorso della libreria R corrente deve essere visualizzato nel **R interattivo** finestra. 

6. Fare clic su di **strumenti R** dal menu **Windows** per visualizzare un elenco di altre finestre specifiche di R che è possibile visualizzare nell'area di lavoro.
 
    + Visualizzare la Guida premendo CTRL + 3 per i pacchetti nella raccolta corrente.
    + Visualizzare le variabili di R nel **Explorer variabile**, premendo CTRL + 8.

7. Creare una stringa di connessione a un'istanza di SQL Server e utilizzare la stringa di connessione nel costruttore RxInSqlServer per creare un oggetto origine dati di SQL Server. 

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

8. Impostare il contesto di calcolo per il server e quindi eseguire il codice R semplice ai dati.

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    Risultati vengono restituiti nel **R interattivo** finestra.
    
    Se si desidera assicurarsi che il codice è in esecuzione nell'istanza di SQL Server, è possibile utilizzare Profiler per creare una traccia.