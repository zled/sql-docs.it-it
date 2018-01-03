---
title: Installare pacchetti R aggiuntivi su SQL Server | Documenti Microsoft
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "16"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 996b69b08973805648da329a328e712d5de45660
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="install-additional-r-packages-on-sql-server"></a>Installare pacchetti R aggiuntivi su SQL Server

In questo articolo viene descritto come installare i nuovi pacchetti di R a un'istanza di SQL Server in cui è abilitato l'apprendimento.

> [!IMPORTANT]
> Il processo per l'aggiunta di nuovi pacchetti varia a seconda della versione di SQL Server è in esecuzione e gli strumenti in uso. 

**Si applica a:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] e  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]
[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

## <a name="overview-of-package-installation-process"></a>Panoramica del processo di installazione del pacchetto

1.  Determinare se è presente una versione di Windows del pacchetto: [ottenere la versione corretta del pacchetto e il formato](#packageVersion)

2.  Se il server non ha accesso a internet, scaricare i file binari in anticipo: [i file zip di Download](#bkmk_zipPreparation)

    Assicurarsi di verificare le dipendenze di pacchetto e ottenere tutti i pacchetti correlati che potrebbero essere necessari durante l'installazione. Per preparare una raccolta di pacchetti e le relative dipendenze, si consiglia di [miniCRAN pacchetto](#bkmk_packageDependencies).

    Se si verificano errori di download o l'installazione, provare a un sito mirror diversi.

3.  Come installare il pacchetto varia a seconda se il server abbia accesso a internet e della versione di SQL Server. Di seguito sono riportate le procedure consigliate:

    **Installazione del pacchetto per SQL Server 2016**
    
    1. L'esperto di dati fornisce i pacchetti necessari per un progetto o un team. Utilizzare [miniCRAN](create-a-local-package-repository-using-minicran.md) per preparare le raccolte di pacchetti con le relative dipendenze.

    2. L'amministratore del database consente di installare i pacchetti alla libreria di istanza utilizzando gli strumenti di R.

    **Installazione del pacchetto per SQL Server 2017**

    1. L'amministratore del database consente di gestione dei pacchetti nell'istanza e consente di aggiungere utenti ai nuovi ruoli di gestione di pacchetto.

    2. L'esperto di dati fornisce i pacchetti necessari per un progetto o un team. Utilizzare [miniCRAN](create-a-local-package-repository-using-minicran.md) per preparare le raccolte di pacchetti con le relative dipendenze.

    3. Il pacchetto viene caricato per l'istanza di SQL Server, tramite l'istruzione CREATE libreria esterna.
    
    4. Dopo che il pacchetto è stato aggiunto all'istanza, qualsiasi utente con le autorizzazioni appropriate può installare i pacchetti per il database in cui vengono eseguiti gli script R chiamando codice R da `sp_execute_external_script`.
    
    5. Gli utenti con le autorizzazioni appropriate possono inoltre installare o trovare i pacchetti da un client remoto di R, usando una nuova funzione RevoScaleR per la gestione dei pacchetti.

## <a name="install-new-packages"></a>Installare i nuovi pacchetti

In questa sezione illustrano procedure dettagliate per scenari di installazione del pacchetto della chiave. Scegliere il metodo migliore, a seconda:

- La versione di SQL Server in uso

- Se sono l'unico proprietario dell'istanza o sta tentando di gestire i pacchetti per più persone che utilizzano i ruoli del database.

- Se si installa un pacchetto o più pacchetti con dipendenze

**Usare Gestione dei pacchetti di SQL Server**

Se l'istanza supporta funzionalità di gestione pacchetti, è possibile utilizzare T-SQL o strumenti R convenzionali.

-  Pacchetto di caricamento una R a SQL Server in cui accedere a gestione dei pacchetti e basata su ruoli pacchetto è abilitato. Quindi, un utente installa il pacchetto utilizzando T-SQL.

    [Installare pacchetti utilizzando Creazione libreria esterna](#bkmk_sqlInstall)

- Per aggiungere nuovi pacchetti in un server, utilizzare un client remoto di R. Richiede SQL Server 2017. Gestione dei pacchetti deve sono state abilitate nel server. 

    [Usare R per installare i pacchetti in un server quando è abilitata la gestione di pacchetti](#bkmk_rAddPackage)

- Preparare una libreria di pacchetto per l'utilizzo con una libreria esterna creare che contiene più pacchetti con le relative dipendenze.

    [Installare più pacchetti da un repository miniCRAN](#bkmk_minicran)

**Utilizzare gli strumenti di R convenzionali**

Se si utilizza una versione precedente di SQL Server R services, seguire queste istruzioni per installare i pacchetti con strumenti di R convenzionali. Facoltativamente, è possibile utilizzare miniCRAN per preparare una raccolta di pacchetti per l'installazione.

-  Installa un pacchetto R in libreria istanza predefinita utilizzando gli strumenti di R. Richiede l'accesso amministrativo.

    [Installare i pacchetti nella libreria di istanza utilizzando gli strumenti di R](#bkmk_rInstall)

- Creare un insieme condiviso di pacchetti per supportare agevolare l'installazione di più pacchetti e le relative dipendenze.

    [Creare un repository di pacchetti tramite miniCRAN](create-a-local-package-repository-using-minicran.md)

### <a name="bkmk_sqlInstall"></a>Installare i pacchetti utilizzando gli strumenti di SQL Server

1. Verificare che la funzionalità di gestione in SQL Server 2017 libreria esterna sia stata abilitata nell'istanza.

    [Come abilitare o disabilitare la gestione dei pacchetti](r-package-how-to-enable-or-disable.md)

2. Connettersi al server utilizzando un account che disponga delle autorizzazioni per installare i nuovi pacchetti, utilizzando uno dei ruoli del database supportato descritti in questo argomento: [gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md)

3.  Copiare il file compresso contenente il pacchetto R che si desidera installare in una cartella sul computer del server, ad esempio, il **utenti** o **documenti** cartella. È possibile aggiungere un pacchetto da un'unità di rete o da una cartella nel computer client. Se è stata usata miniCRAN per creare un repository di pacchetti, copiare il repository di pacchetti nella sua interezza in qualsiasi cartella locale nel server: ovvero, non su un'unità di rete.

    Se si non ha accesso a qualsiasi cartella nel server, è possibile passare il contenuto del pacchetto in formato binario. Vedere [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) per un esempio.

4.  Dal database in cui si desidera utilizzare il pacchetto, eseguire il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione.

    In questo esempio si presuppone che l'account disponga dell'autorizzazione per caricare nuovi pacchetti sul server e installarli per **condivisa** ambito nel database.

    L'istruzione seguente aggiunge una versione di rilascio di [zoo](https://cran.r-project.org/web/packages/zoo/index.html) pacchetto nel contesto del database corrente, da una condivisione di file locale.

    ```SQL
    CREATE EXTERNAL LIBRARY zoo
    FROM (CONTENT = 'C:\Temp\RPackages\zoo_1.8-0.zip')
    WITH (LANGUAGE = 'R');
    ```

    Se ci si connette utilizzando un account che sia un proprietario del database (membro del ruolo dbo), il pacchetto viene resa disponibile in **condivisa** ambito: ovvero, può essere installato da qualsiasi utente che è un membro del `rpkgs-users` ruolo.

    Se si carica il pacchetto utilizzando un account che può accedere solo **privata** ambito, il pacchetto può essere installato solo dall'utente.

4.  Per installare il pacchetto nella libreria R predefinito utilizzata dall'istanza, eseguire R `library()` comando all'interno di sp_execute_external_script stored procedure.

    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    # load the binaries in zoo
    library(zoo)'
    ```

    Se ha esito positivo, il **messaggi** finestra deve segnalare un messaggio come "pacchetto"zoo"correttamente decompressi e somme MD5 archiviato". Se un pacchetto richiesto è già installato, il processo di installazione collega quindi carica il pacchetto richiesto.

    > [!NOTE]
    > Se un pacchetto richiesto non è disponibile, viene restituito un errore: "Nessun pacchetto chiamato \<required_package\>". 
    > 
    > Per evitare errori, si consiglia di verificare in anticipo le dipendenze del pacchetto oppure utilizzare miniCRAN per raccogliere tutti i pacchetti richiesti in un singolo file compresso prima di eseguire `CREATE EXTERNAL LIBRARY`.

### <a name="bkmk_rAddPackage"></a>Usare R per installare i pacchetti in un server quando è abilitata la gestione di pacchetti

Se è già stato abilitato nell'istanza di gestione dei pacchetti, è possibile installare i nuovi pacchetti di R da un client remoto di R, utilizzando le funzioni RevoScaleR per la gestione dei pacchetti.

1. Prima di iniziare, verificare che siano soddisfatte queste condizioni:

    + Utilizzare la versione più recente di Microsoft R Client, che include gli aggiornamenti per RevoScale.
    + Gestione dei pacchetti è stata abilitata nell'istanza e sul database.
    + Si è autorizzati a uno dei ruoli di gestione del database.

2. Elencare i pacchetti che si desidera installare in una variabile di stringa.

    ```R
    packageList <- c("e1071")
    ```
    
3. Definire una stringa di connessione per l'istanza e il database in cui è abilitata la gestione dei pacchetti e utilizzare la stringa di connessione per creare un contesto di calcolo di SQL Server.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

4. Chiamare `rxInstallPackages` e passare il contesto di calcolo e la variabile di stringa che contiene i nomi dei pacchetti.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Se sono necessari i pacchetti dipendenti, anche questi vengono scaricati.
    
    In questo esempio, poiché il proprietario del pacchetto e l'ambito non è stato specificato, il pacchetto viene installato utilizzando le credenziali dell'utente che effettua la connessione e i pacchetti vengono installati utilizzando l'ambito predefinito per tale utente.

### <a name="bkmk_rInstall"></a>Installare i pacchetti nella libreria di istanza utilizzando gli strumenti di R

È possibile utilizzare strumenti R per installare nuovi pacchetti di SQL Server 2016 e SQL Server 2017. Tuttavia, è necessario essere un amministratore per eseguire questa operazione.

1.  Se il server non ha accesso a internet, è possibile scaricare i pacchetti di anticipo.

    È consigliabile utilizzare un repository di pacchetti per preparare le raccolte di pacchetti non in linea. Per ulteriori informazioni, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md).

2.  Passare alla cartella sul server in cui sono installate le librerie di R per l'istanza.

    > [!IMPORTANT] 
    > Assicurarsi di installare i pacchetti per la libreria predefinita associata con l'istanza corrente. Non installare mai pacchetti in una directory dell'utente. Per istruzioni su come individuare la libreria predefinita, vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md).

    Per ogni istanza in cui si esegue un pacchetto, installare una copia separata del pacchetto. Pacchetti non possono essere condivisa tra più istanze.

4.  Aprire un prompt dei comandi di R come amministratore.

    Ad esempio, se si utilizza il prompt dei comandi di Windows, passare alla directory in cui si trovano i file RTerm.Exe o RGui.exe. 

    **Istanza predefinita**

    SQL Server 2017:`C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016:`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

    **Istanza denominata**

    SQL Server 2017:`C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016:`C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

5.  Eseguire il comando di R `install.packages` per installare il pacchetto.

    La sintassi dipende se si desidera ottenere il pacchetto da Internet o da un file compresso locale. 

    **Installare il pacchetto tramite una connessione internet**

    Ad esempio, l'istruzione seguente installa il pacchetto di e1071 più diffusi. Le virgolette doppie sono sempre necessari per il nome del pacchetto.

    ```R
    install.packages("e1071", lib = lib.SQL)
    ```

    Quando viene richiesto un sito mirror, è possibile selezionare qualsiasi sito a cui è utile per il percorso.

    Se il pacchetto di destinazione dipende da pacchetti aggiuntivi, il programma di installazione di R automaticamente le dipendenze vengono scaricate e li installa automaticamente.

    **Installa pacchetto manualmente o in un computer senza accesso a Internet**

    Se il pacchetto che si intende installare ha dipendenze, ottenere in anticipo i pacchetti necessari e aggiungerli alla cartella con gli altri file di pacchetto compressi. Vedere il [suggerimenti per l'installazione](#bkmk_tips) sezione per informazioni sulla preparazione dei pacchetti.

    Nel prompt dei comandi di R, digitare il comando seguente per specificare il percorso e il nome del pacchetto da installare:

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Questo comando consente di estrarre un singolo pacchetto R dal file compresso locale, presupponendo che la copia è stato salvato nella directory `C:\Temp\Downloaded packages`, quindi installa il pacchetto (con le relative dipendenze) nella libreria R sul computer locale.

### <a name="bkmk_minicran"></a>Installare più pacchetti da un repository miniCRAN

Il processo generale di installazione dei pacchetti da un repository miniCRAN è simile all'installazione di un pacchetto da un unico file ZIP. Tuttavia, invece di caricare un singolo pacchetto in formato compresso, il repository miniCRAN contiene il pacchetto di destinazione, nonché tutti i pacchetti necessari correlati.

1.  Preparare il repository miniCRAN e quindi copiare il file compresso in una cartella locale nel server.

2.  Se si sta utilizzando T-SQL, un amministratore esegue l'istruzione T-SQL `CREATE EXTERNAL LIBRARY` per caricare la raccolta di pacchetto compresso nel database.

    Ad esempio, l'istruzione seguente fa riferimento a un repository miniCRAN contenente il pacchetto randomForest e le relative dipendenze.

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Downloads\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

3. Per installare i pacchetti per l'utilizzo con SQL Server, eseguire il comando seguente come parte del codice R in una stored procedure.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    # install randomForest and its dependencies
    library(randomForest)'
    ```

    Se ha esito positivo, il **messaggi** finestra deve segnalare un messaggio, ad esempio "package 'randomForest' correttamente decompressi e somme MD5 archiviato" e "Completato concatenate esecuzione".

## <a name="package-installation-tips"></a>Suggerimenti per l'installazione del pacchetto

In questa sezione fornisce diversi suggerimenti e codice di esempio relativi all'installazione del pacchetto R in SQL Server. 

###  <a name="packageVersion"></a>Ottenere la versione corretta del pacchetto e il formato

Sono presenti più origini per i pacchetti R, le più note sono CRAN e Bioconductor. Il sito ufficiale per il linguaggio R (<https://www.r-project.org/>) elenca molte di queste risorse. Molti pacchetti vengono pubblicati in GitHub, dove è possibile ottenere il codice sorgente. Tuttavia, si potrebbero avere ottenuto il pacchetti R sviluppati da qualcuno nella propria azienda.

Indipendentemente dall'origine, è necessario assicurarsi che il pacchetto da installare è in formato binario per la piattaforma Windows. In caso contrario, il pacchetto scaricato non è possibile eseguire nell'ambiente di SQL Server.

Prima di scaricare, controllare anche se il pacchetto è compatibile con la versione di R in esecuzione in SQL Server.

### <a name="bkmk_zipPreparation"></a>Download del pacchetto come file compresso

Per l'installazione in un server senza accesso a internet, scaricare una copia del pacchetto nel formato di un file compresso per l'installazione offline. Non decomprimere il pacchetto.

Ad esempio, la procedura seguente descrive adesso per ottenere la versione corretta del [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) pacchetto da Bioconductor, supponendo che il computer abbia accesso a internet.

1.  Nell'elenco **Archivi dei pacchetti** , individuare la versione **binaria di Windows** .

2.  Fare doppio clic sul collegamento per il. File ZIP e selezionare **destinazione Salva come**.

3.  Passare alla cartella locale in cui vengono archiviati, pacchetti compressi e fare clic su **salvare**.

Questo processo crea una copia locale del pacchetto. È quindi possibile installare il pacchetto o copiare il pacchetto compresso in un server che non dispone dell'accesso a internet.

Per ulteriori informazioni sui contenuti del formato di file zip e come creare un pacchetto R, si consiglia di questa esercitazione, che è possibile scaricare in formato PDF dal sito del progetto R: [la creazione di pacchetti R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf).

### <a name="bkmk_packageDependencies"></a>Ottenere le dipendenze dei pacchetti

Pacchetti R spesso dipendono da altri più pacchetti, alcuni dei quali potrebbero non essere disponibili nella libreria R predefinito utilizzata dall'istanza. In alternativa, a volte un pacchetto richiede una versione diversa di un pacchetto dipendente che è già installato.

Se è necessario installare più pacchetti o per assicurarsi che tutti gli utenti dell'organizzazione Ottiene il tipo di pacchetto corretto e la versione, è consigliabile utilizzare il pacchetto miniCRAN per creare un repository locale che può essere condivisa tra più utenti o computer. Per ulteriori informazioni, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="permissions"></a>Autorizzazioni

Nel caso di un utente esperto di R, potrebbe essere abituati a pacchetti di installazione dalla riga di comando senza autorizzazioni speciali o senza scaricarli in anticipo. Tuttavia, la maggior parte dei server non dispone di una connessione internet. Inoltre, l'accesso a condivisioni file o archiviazione potrebbe essere limitata.

In questa sezione viene descritto il livello di autorizzazioni necessarie per l'installazione di pacchetti in SQL Server 2016 e SQl Server 2017 diverso. L'installazione può essere eseguita utilizzando gli strumenti di R o SQL Server, ma il processo e le autorizzazioni sono leggermente diverse.

-   SQL Server 2016

    In questa versione, solo un amministratore nel computer è possibile installare pacchetti nella posizione desiderata. Utilizzare gli strumenti standard di R per installare i pacchetti, ma è necessario eseguire come amministratore e utilizzare gli strumenti di R associati all'istanza.

-   SQL Server 2017

    Questa versione sono disponibili nuove funzionalità che consentono a un amministratore del database di delegare l'installazione del pacchetto agli utenti. L'amministratore di database è necessario abilitare la funzionalità di gestione pacchetti in ogni istanza. Dopo questa funzionalità è abilitata, l'amministratore di database è possibile utilizzare i ruoli del database per consentire a singoli utenti per installare i pacchetti in base alle esigenze, o per condividere i pacchetti in base al database.

    Per ulteriori informazioni, vedere [gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md).


> [!IMPORTANT]
> 
> Si è abituati gli utenti esperti di R per l'installazione di pacchetti in una raccolta di utenti e quindi facendo riferimento al pacchetto in tale cartella come parte della soluzione di R, specificando un percorso di file. Tuttavia, ciò non è supportata in SQL Server. Per ulteriori informazioni e soluzioni alternative, vedere [illustrato come utilizzare pacchetti nelle librerie utente](packages-installed-in-user-libraries.md).

### <a name="comparing-package-management-methods"></a>Il confronto di metodi di gestione pacchetti

In questa sezione Confronta i metodi di installazione del pacchetto disponibili e sono elencate alcune considerazioni e suggerimenti che consentono di determinare una strategia di gestione e installazione di pacchetto appropriata.

#### <a name="using-sql-server-package-management-features"></a>Utilizzo delle funzionalità di gestione di pacchetti di SQL Server

Se si Abilita gestione dei pacchetti, si installa un pacchetto per un database specifico. Se è necessario utilizzare un pacchetto in tutti i database in cui è abilitato lo script R, è necessario installarlo in ogni database.

Tuttavia, poiché SQL Server gestisce le informazioni sull'utente che ha il diritto di utilizzare i pacchetti, è più semplice copiare le informazioni sugli utenti e i pacchetti tra i database. È inoltre facile ricompilare un set di pacchetti di lavoro per una o più utenti, quando si ripristina un database o quando si sposta tra le istanze.

Utilizzo di T-SQL e le funzionalità di gestione di pacchetti in SQL Server 2017 è il metodo preferito ogni volta che si dispone di più utenti di database di installazione o l'esecuzione di pacchetti R.

Questa funzionalità è disponibile a partire da SQL Server 2017.

#### <a name="using-r-tools-to-install-packages-for-the-sql-server-instance"></a>Utilizzo di strumenti R per installare i pacchetti per l'istanza di SQL Server

Se si utilizza questo metodo, i pacchetti installati per l'istanza sono disponibili in qualsiasi database. Tuttavia, poiché i pacchetti vengono installati direttamente al file system, devono invece essere gestite all'esterno di SQL Server. Pacchetti non possono essere eseguito il backup o il ripristino. Inoltre, l'amministratore del database necessario sapere come utilizzare gli strumenti di R.

Tuttavia, questa soluzione è quella più semplice se si è l'unico proprietario del database.

#### <a name="managing-multiple-packages-and-multiple-versions-of-the-same-package"></a>Gestione di più pacchetti e più versioni dello stesso pacchetto

Se è necessario eseguire l'installazione offline di pacchetti R, impostazione di un repository locale tramite [miniCRAN](https://mran.revolutionanalytics.com/package/miniCRAN/) consente di condividere i pacchetti e gestire le versioni disponibili per l'utilizzo dell'organizzazione.

#### <a name="establish-a-single-mirror-site-as-standard"></a>Creare un sito mirror singolo come standard

Per evitare di selezionare un sito mirror ogni volta che si aggiunge un nuovo pacchetto, è possibile configurare l'ambiente di sviluppo di R in modo che usi sempre lo stesso repository. A tale scopo, modificare il file di impostazioni globale R, **. Rprofile**e aggiungere la riga seguente:

`options(repos=structure(c(CRAN="<mirror site URL>")))`

Mirror CRAN correnti sono elencati nella [questo sito](https://cran.r-project.org/mirrors.html).

Per informazioni dettagliate sulle preferenze e altri file caricati all'avvio del runtime di R, eseguire questo comando in una console di R:`?Startup`

#### <a name="know-which-library-you-are-using-for-installation"></a>Conoscere la libreria che si utilizza per l'installazione

Se in precedenza, è stata modificata l'ambiente R nel computer, prima di installare qualsiasi elemento, sospendere qualche istante e assicurarsi che la variabile di ambiente R `.libPath` Usa un unico percorso.

Questo percorso deve puntare alla cartella R_SERVICES per l'istanza. Per ulteriori informazioni, vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md).

#### <a name="side-by-side-installation-with-r-server"></a>Installazione side-by-side con R Server

Se è stato installato Microsoft Machine Learning Server (Standalone) oltre a servizi di SQL Server Machine Learning, il computer deve disporre di installazioni distinte di R per ogni entrambi, i duplicati di tutti gli strumenti di R e librerie.

> [!IMPORTANT]
> 
> I pacchetti installati nella raccolta R_SERVER sono utilizzati solo da Microsoft R Server e SQL Server non sono accessibile.
> 
> Assicurarsi di utilizzare il `R_SERVICES` libreria quando si installano i pacchetti che si desidera utilizzare in SQL Server.
