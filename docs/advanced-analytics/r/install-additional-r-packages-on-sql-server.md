---
title: Installare pacchetti R aggiuntivi su SQL Server | Documenti Microsoft
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "16"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 2821983b39dcd4c301ea4b49713de0cdd3550a65
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="install-additional-r-packages-on-sql-server"></a>Installare pacchetti R aggiuntivi su SQL Server

In questo articolo viene descritto come installare i nuovi pacchetti di R a un'istanza di SQL Server in cui è abilitato l'apprendimento.

**Si applica a:** 
+ [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]  [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]
+ [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

## <a name="prerequisites"></a>Prerequisites

+ Determinare se è presente una versione di Windows del pacchetto: [ottenere la versione corretta del pacchetto e il formato](#packageVersion)

+ Se il server non ha accesso a internet, è necessario scaricare i file binari di Windows in anticipo: [i file zip di Download](#bkmk_zipPreparation)

+ Identificare le dipendenze del pacchetto. 

    - Se il server ha accesso a internet, non è necessario preoccuparsi di dipendenze; tutti i pacchetti necessari possono essere installati automaticamente.

    - Se il server non **non** hanno accesso a internet, è necessario identificare tutte le dipendenze e scaricare i pacchetti richiesti in anticipo, in formato compresso. Un modo semplice per eseguire questa operazione consiste nell'utilizzare [miniCRAN](create-a-local-package-repository-using-minicran.md) per preparare una raccolta di pacchetti con tutte le dipendenze. Questo repository quindi può essere copiato nel computer server.

+ Verificare la compatibilità di pacchetto. Il pacchetto deve essere compatibile con la versione di R in esecuzione in SQL Server.

    Controllare inoltre se il pacchetto (o tutti i pacchetti che richiede) include funzionalità che verranno bloccate da SQL Server o da criteri. Ad esempio, alcuni pacchetti sono un adattamento per un ambiente protezione avanzato di SQL Server insufficiente. Tali pacchetti potrebbero includere pacchetti che accedono alla rete, che utilizzano Java o altri Framework non è in genere utilizzata in un ambiente di SQL Server o i pacchetti che richiedono l'accesso con privilegi elevati di file system.

+ Autorizzazioni

    È necessario l'accesso amministrativo al computer che esegue SQL Server.

    Inoltre, per eseguire in SQL Server, pacchetti devono essere installati della libreria predefinita associata con l'istanza corrente. Per istruzioni su come individuare la libreria predefinita, vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md).
    
    Nel caso di un utente esperto di R, potrebbe essere abituati a pacchetti di installazione dalla riga di comando senza autorizzazioni speciali o senza scaricarli in anticipo. Tuttavia, questo metodo non funziona in SQL Server. In molti casi, SQL Server i computer non sono una connessione internet. Inoltre, l'accesso a file server o archiviazione esterna può essere limitato. Pacchetti installati in una raccolta di utente non sono accessibile runnign processi R in SQL Server. 

    Se non si dispone di accesso amministrativo al computer SQL Server, è possibile trovare un amministratore del database per l'installazione del pacchetto.

+ Per ogni istanza in cui è necessario utilizzare il pacchetto di installazione separatamente.

     Pacchetti non possono essere condivisa tra più istanze. È possibile utilizzare la stessa origine di file compresso per installare il pacchetto per separare le istanze, ma una copia separata del pacchetto viene aggiunto alla libreria ogni istanza.

## <a name="install-packages"></a>Installare i pacchetti

Questa sezione fornisce i passaggi di installazione del pacchetto per gli scenari seguenti:

+ [Installare i nuovi pacchetti in un server con accesso a Internet](#bkmk_rInstall)
+ [Eseguire un'installazione offline di pacchetti in un server con **non** l'accesso a internet](#bkmk_offlineInstall)
+ [Installare i pacchetti in un contesto di calcolo di SQL Server con RevoScaleR](#bkmk_rAddPackage)
+ [Installare i pacchetti utilizzando l'istruzione CREATE libreria esterna](#bkmk_createlibrary) (2017 solo di SQL Server e altre limitazioni si applicano)

### <a name="bkmk_rInstall"></a>Installazione online utilizzando gli strumenti di R

È possibile utilizzare gli strumenti standard di R per installare i nuovi pacchetti in un'istanza di SQL Server 2016 o SQL Server 2017. Tuttavia, è necessario essere un amministratore per eseguire questa operazione.

1.  Passare alla cartella sul server in cui sono installate le librerie di R per l'istanza.

    > [!IMPORTANT] 
    > Assicurarsi di installare i pacchetti per la libreria predefinita associata con l'istanza corrente. Non installare mai pacchetti in una directory dell'utente.

    Se non si dispone delle autorizzazioni necessarie, contattare l'amministratore del database e fornire un elenco dei pacchetti che è necessario.

2.  Aprire un prompt dei comandi di R come amministratore.

    Ad esempio, se si utilizza il prompt dei comandi di Windows, passare alla directory in cui si trovano RTerm.Exe o RGui.exe. 

    **Istanza predefinita**

    SQL Server 2017:`C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016:`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

    **Istanza denominata**

    SQL Server 2017:`C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016:`C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

    Se è stata utilizzata l'associazione per l'aggiornamento di machine learning componenti, il percorso potrebbe essere modificato. Verificare sempre il percorso dell'istanza prima di installare i nuovi pacchetti. 

3.  Eseguire il comando di R `install.packages` per installare il pacchetto. Ad esempio, l'istruzione seguente installa il pacchetto di e1071 più diffusi. 

    ```R
    install.packages("e1071", lib = lib.SQL)
    ```

    Le virgolette doppie sono necessari per il nome del pacchetto.

4. Quando viene richiesto un sito mirror, è possibile selezionare qualsiasi sito a cui è utile per il percorso.

5. Se il pacchetto di destinazione dipende da pacchetti aggiuntivi, il programma di installazione di R automaticamente le dipendenze vengono scaricate e li installa automaticamente.

> [!IMPORTANT]
> Per ogni istanza in cui è necessario utilizzare il pacchetto di installazione separatamente. Pacchetti non possono essere condivisa tra più istanze.

### <a name = "bkmk_offlineInstall"></a>Installazione offline utilizzando gli strumenti di R 

Se il pacchetto che si prevede di installare dipendenze, preparare **tutti** necessari pacchetti anticipatamente.  Vedere il [suggerimenti per l'installazione](#bkmk_tips) sezione per informazioni sulla preparazione dei pacchetti.

> [!IMPORTANT]
>  Quando si installa i pacchetti in un server che non dispone di alcun accesso a internet, è importante analizzare le dipendenze complete in anticipo e assicurarsi che sia stato scaricato tutti i pacchetti richiesti **prima** iniziare l'installazione. È consigliabile [miniCRAN](https://mran.microsoft.com/package/miniCRAN) per questo processo. Il pacchetto R accetta un elenco di pacchetti da installare, consente di analizzare le dipendenze e ottiene tutti i file compressi automaticamente. miniCRAN crea quindi un singolo archivio che è possibile copiare nel computer server.
> 
> Per informazioni dettagliate, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md)

1. Copiare il pacchetto o il repository in formato compresso in una condivisione locale, o un altro percorso che il server può accedere.

2.  Individuare la cartella nel server in cui sono installate le librerie di R per l'istanza.

    Ad esempio, se si utilizza il prompt dei comandi di Windows, passare alla directory in cui si trovano RTerm.Exe o RGui.exe.

    **Istanza predefinita**

    SQL Server 2017:`C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016:`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

    **Istanza denominata**

    SQL Server 2017:`C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016:`C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

3. Aprire un prompt dei comandi di R come amministratore.

4.  Eseguire il comando di R `install.packages` e specificare il pacchetto o nome di repository e il percorso del file ZIP.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Questo comando consente di estrarre il pacchetto R `mynewpackage` dal file compresso locale, presupponendo che la copia è stato salvato nella directory `C:\Temp\Downloaded packages`, quindi installa il pacchetto nel computer locale. Se il pacchetto contiene tutte le dipendenze, il programma di installazione verifica i pacchetti esistenti nella libreria. Se è stato creato un repository che include le dipendenze, il programma di installazione installa anche i pacchetti requireed.

    Se tutti i pacchetti necessari non sono presenti nella libreria di istanza e non possono essere disponibile nei file compressi, l'installazione del pacchetto di destinazione non riesce.

### <a name="bkmk_rAddPackage"></a>Installare pacchetti R in un server da un client remoto di R

Nelle versioni recenti di [R Server o Server di Machine Learning](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server), RevoScaleR include funzioni che supportano l'installazione di nuovi pacchetti di R in un contesto di calcolo di SQL Server. 

1. Prima di iniziare, verificare che siano soddisfatte queste condizioni:

    + Il client ha RevoScale 9.0.1 o versione successiva.
    + Una versione equivalente di RevoScaleR installata nell'istanza di SQL Server.
    + Il [funzionalità di gestione pacchetti](..\r\r-package-how-to-enable-or-disable.md) è stata abilitata nell'istanza.
    + Si è un membro di un ruolo del database che consente di installare i pacchetti in un oggetto condiviso o prvate contesto, l'istanza specificata e ddatabase.

2. Dalla riga di comando R, definire una stringa di connessione per l'istanza e il database e utilizzare la stringa di connessione con il [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) costruttore per creare un contesto di calcolo di SQL Server.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Creare un elenco dei pacchetti che si desidera installare e salvare l'elenco in una variabile di stringa.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Chiamare [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) e passare il contesto di calcolo e la variabile di stringa che contiene i nomi dei pacchetti.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Se sono necessari i pacchetti dipendenti, essi vengono installati anche, presupponendo che sia disponibile una connessione internet.
    
    In questo esempio, poiché il proprietario e l'ambito non è stato specificato, i pacchetti vengono installati utilizzando le credenziali dell'utente che effettua la connessione, nell'ambito predefinito per tale utente.

### <a name="bkmk_createlibrary"></a>Usare un repository miniCRAN e creare libreria esterna per installare i pacchetti 

SQL Server 2017 fornisce nuove funzionalità per l'installazione e la gestione dei pacchetti R utilizzando T-SQL. Tuttavia, questo processo richiede che un pacchetto siano disponibili come locale compresso file, anziché il download da internet. L'istruzione ha esito negativo se tutti i pacchetti non vengono preparati in anticipo.

Creazione libreria esterna è supportata nei seguenti casi:

+ Si installa un singolo pacchetto senza dipendenze
+ Si intende installare più pacchetti o pacchetti con dipendenze e aver preparato tutti i pacchetti in anticipo. 

**Passaggi**

1.  Preparare il pacchetto in formato compresso, oppure creare un repository miniCRAN contenente il pacchetto e le relative dipendenze.  

2. Copiare il file compresso o un repository in una cartella locale nel server.

     > [!IMPORTANT]
     > Il file che è necessario specificare come origine deve contenere il pacchetto di destinazione, nonché tutti i pacchetti necessari correlati.

3. Come amministratore, eseguire l'istruzione T-SQL `CREATE EXTERNAL LIBRARY` per caricare la raccolta di pacchetto compresso nel database.

    Ad esempio, l'istruzione seguente fa riferimento a un repository miniCRAN contenente il pacchetto randomForest e le relative dipendenze. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Downloads\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    Non è possibile utilizzare un nome arbitrario nell'istruzione CREATE; il nome della libreria esterna deve avere lo stesso nome che si prevede di utilizzare durante il caricamento o la chiamata del pacchetto.

4. Installare i pacchetti per l'utilizzo con SQL Server, eseguendo il codice all'interno di una stored procedure.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    # install randomForest and its dependencies
    library(randomForest)'
    ```

    Se ha esito positivo, il **messaggi** finestra deve segnalare un messaggio, ad esempio "package 'randomForest' correttamente decompressi e somme MD5 archiviato" e "Completato concatenate esecuzione".

    Se l'installazione non riesce, tutti i pacchetti errore di installazione e i tentativi successivi di pacchetto di installazione potrebbero anche non riuscire, a questo messaggio: 

    "Errore in rxSqlPkgInstallPackages... Non è riuscito a installare pacchetti: esaminare i log per ulteriori informazioni"

## <a name="package-installation-tips-and-frequently-asked-questions-faq"></a>Suggerimenti per l'installazione del pacchetto e domande frequenti (FAQ)

In questa sezione fornisce diversi suggerimenti e domande comuni relative all'installazione di pacchetti R in SQL Server.

###  <a name="packageVersion"></a>Ottenere la versione corretta del pacchetto e il formato

Sono presenti più origini per i pacchetti R, le più note sono CRAN e Bioconductor. Il sito ufficiale per il linguaggio R (<https://www.r-project.org/>) elenca molte di queste risorse. Molti pacchetti vengono pubblicati in GitHub, dove è possibile ottenere il codice sorgente. Tuttavia, si potrebbero avere ottenuto il pacchetti R sviluppati da qualcuno nella propria azienda.

Indipendentemente dall'origine, è necessario assicurarsi che il pacchetto da installare è in formato binario per la piattaforma Windows. In caso contrario, il pacchetto scaricato non è possibile eseguire nell'ambiente di SQL Server.

### <a name="bkmk_zipPreparation"></a>Scaricare il pacchetto come file compresso

Per l'installazione in un server senza accesso a internet, è necessario scaricare una copia del pacchetto nel formato di un file compresso per l'installazione offline. Non decomprimere il pacchetto.

Ad esempio, la procedura seguente descrive adesso per ottenere la versione corretta del [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) pacchetto da Bioconductor, supponendo che il computer abbia accesso a internet.

1.  Nell'elenco **Archivi dei pacchetti** , individuare la versione **binaria di Windows** .

2.  Fare doppio clic sul collegamento per il. File ZIP e selezionare **destinazione Salva come**.

3.  Passare alla cartella locale in cui vengono archiviati, pacchetti compressi e fare clic su **salvare**.

    Questo processo crea una copia locale del pacchetto. Se si verifica un errore di download, provare a un sito mirror diversi.

4. Dopo aver scaricato l'archivio pacchetti, è possibile installare il pacchetto o copiare il pacchetto compresso in un server che non dispone dell'accesso a internet.

> [!TIP]
> Se per errore, si installa il pacchetto anziché essere scaricato i file binari, una copia del file compresso scaricato viene salvata anche nel computer. Controllare i messaggi di stato mentre il pacchetto viene installato per determinare il percorso del file. È possibile copiare il file compresso per il server che non dispone dell'accesso a internet.
> Se si scarica pacchetto utilizzando questo metodo, non sono incluse le dipendenze del pacchetto. 

Per ulteriori informazioni sui contenuti del formato di file zip e come creare un pacchetto R, si consiglia di questa esercitazione, che è possibile scaricare in formato PDF dal sito del progetto R: [la creazione di pacchetti R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf).

### <a name="bkmk_packageDependencies"></a>Ottenere le dipendenze dei pacchetti

Pacchetti R spesso dipendono da altri più pacchetti, alcuni dei quali potrebbero non essere disponibili nella libreria R predefinito utilizzata dall'istanza. A volte un pacchetto richiede una versione diversa di un pacchetto dipendente che è già installato.

Se è necessario installare più pacchetti o per assicurarsi che tutti gli utenti dell'organizzazione Ottiene il tipo di pacchetto corretto e la versione, è consigliabile utilizzare il [miniCRAN](https://mran.microsoft.com/package/miniCRAN) pacchetto per creare un repository locale che può essere condivisa tra più utenti o computer. Per ulteriori informazioni, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="permissions"></a>Autorizzazioni

In questa sezione viene descritto il livello di autorizzazioni necessarie per l'installazione di pacchetti in SQL Server 2016 e SQL Server 2017 diverso. L'installazione può essere eseguita utilizzando gli strumenti di R o SQL Server, ma il processo e le autorizzazioni sono leggermente diverse.

-   SQL Server 2016

    In questa versione, solo un amministratore nel computer è possibile installare pacchetti nella posizione desiderata. Utilizzare gli strumenti standard di R per installare i pacchetti, ma è necessario eseguire come amministratore e utilizzare gli strumenti di R associati all'istanza.

-   SQL Server 2017

    Se si dispone di accesso amministrativo, è possibile installare un'istanza a livello di pacchetti tramite gli strumenti di R.

    Se dispone di un database, è possibile installare pacchetti R da un client remoto, se si definisce una connessione e connettersi all'istanza utilizzando RxInSqlServer.
    
    Questa versione include nuove funzionalità per supportare l'amministrazione dei pacchetti R o Python dagli amministratori di database nelle versioni future. Per utilizzare questa funzione, un amministratore di database deve prima abilitare le funzionalità di gestione di pacchetti in ogni istanza. Dopo questa funzionalità è abilitata, singoli utenti possono installare i pacchetti a un database specifico, a seconda del ruolo di database. Per ulteriori informazioni, vedere [abilitare o disabilitare la gestione dei pacchetti R per SQL Server](../r/r-package-how-to-enable-or-disable.md).

> [!IMPORTANT]
> 
> Si è abituati gli utenti esperti di R per l'installazione di pacchetti in una raccolta di utenti e quindi facendo riferimento al pacchetto in tale cartella come parte della soluzione di R, specificando un percorso di file. Tuttavia, ciò non è supportata in SQL Server. Per ulteriori informazioni e soluzioni alternative, vedere [illustrato come utilizzare pacchetti nelle librerie utente](packages-installed-in-user-libraries.md).

### <a name="establish-a-single-mirror-site-as-standard"></a>Creare un sito mirror singolo come standard

Per evitare di selezionare un sito mirror ogni volta che si aggiunge un nuovo pacchetto, è possibile configurare l'ambiente di sviluppo di R in modo che usi sempre lo stesso repository. A tale scopo, modificare il file di impostazioni globale R, **. Rprofile**e aggiungere la riga seguente:

`options(repos=structure(c(CRAN="<mirror site URL>")))`

Mirror CRAN correnti sono elencati nella [questo sito](https://cran.r-project.org/mirrors.html).

Per informazioni dettagliate sulle preferenze e altri file caricati all'avvio del runtime di R, eseguire questo comando in una console di R:`?Startup`

### <a name="know-which-library-you-are-using-for-installation"></a>Conoscere la libreria che si utilizza per l'installazione

Se in precedenza, è stata modificata l'ambiente R nel computer, prima di installare qualsiasi elemento, sospendere qualche istante e assicurarsi che la variabile di ambiente R `.libPath` Usa un unico percorso.

Questo percorso deve puntare alla cartella R_SERVICES per l'istanza. Per ulteriori informazioni, vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md).

### <a name="side-by-side-installation-with-r-server"></a>Installazione side-by-side con R Server

Se è stato installato Microsoft Machine Learning Server (Standalone) oltre a servizi di SQL Server Machine Learning, il computer deve disporre di installazioni distinte di R per ogni, con i duplicati di tutti gli strumenti di R e librerie.

> [!IMPORTANT]
> 
> I pacchetti installati nella raccolta R_SERVER sono utilizzati solo da Microsoft R Server e SQL Server non sono accessibile.
> 
> Assicurarsi di utilizzare il `R_SERVICES` libreria quando si installano i pacchetti che si desidera utilizzare in SQL Server.

### <a name="how-to-determine-which-packages-are-already-installed"></a>Come determinare quali pacchetti sono già installati?

 Vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md)