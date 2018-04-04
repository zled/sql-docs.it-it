---
title: Creare un repository di pacchetti locali tramite miniCRAN | Documenti Microsoft
titleSuffix: SQL Server
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 6dfaa01607bb25e1afe41301e655025a8d2b059f
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="create-a-local-package-repository-using-minicran"></a>Creare un repository di pacchetti locali tramite miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Il [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) pacchetto è stato creato da Andre de Vries per supportare questi scenari comuni: 

+ Analisi delle dipendenze di pacchetto per un singolo pacchetto o un set di pacchetti
+ Preparazione di un set di pacchetti R per l'installazione in un server senza accesso a internet.

L'utente specifica un set di pacchetti desiderati e legge l'albero delle dipendenze per questi pacchetti, in modo ricorsivo miniCRAN e Scarica solo i pacchetti elencati e le relative dipendenze da CRAN o repository simili.

Come output, miniCRAN crea un repository internamente coerenza, costituito da pacchetti selezionati e tutte le dipendenze necessarie. È quindi possibile spostare questo repository locale nel server di e continuare a installare i pacchetti senza utilizzare internet.

Gli utenti esperti di R esaminare spesso per l'elenco dei pacchetti dipendenti nel file di descrizione per il pacchetto scaricato. Tuttavia, i pacchetti elencati **importazioni** potrebbero avere delle dipendenze di secondo livello. Per questo motivo, è consigliabile l'utilizzo del **miniCRAN** metodo.

## <a name="what-is-a-package-repository"></a>Che cos'è un repository di pacchetti

L'obiettivo di creazione di un repository di pacchetti locali è fornire un singolo percorso che un amministratore del server o ad altri utenti nell'organizzazione consente di installare i nuovi pacchetti di R in un server che non dispone dell'accesso a internet. Dopo aver creato il repository, è possibile modificarla in aggiungendo nuovi pacchetti o l'aggiornamento della versione dei pacchetti esistenti.

Il [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) dal pacchetto per R è stato scritto dal [Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html) per renderne più semplice creare un coerente gestiti set di pacchetti R per un'organizzazione. 

Repository di pacchetto sono utili in questi scenari:

- **Sicurezza**: R molti utenti sono abituati a download e installazione di nuovi pacchetti R quando è necessario, da CRAN o uno dei relativi siti di mirror. Tuttavia, per motivi di sicurezza, il server di produzione in esecuzione [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] in genere non dispongono di connettività internet.

- **Più facile installazione offline**: installare il pacchetto a un server non in linea richiede che è anche di scaricare tutte le dipendenze di pacchetto, tramite miniCRAN rende più semplice ottenere tutte le dipendenze nel formato corretto.

    Tramite miniCRAN, è possibile evitare errori di dipendenza del pacchetto durante la preparazione di pacchetti per l'installazione con il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione.

- **Gestione della versione migliorata**: In un ambiente multiutente, esistono buone ragioni per evitare l'installazione senza restrizioni di più versioni del pacchetto nel server. Usare un repository locale per fornire un set coerenza di pacchetti per l'utilizzo da analisti. 

> [!TIP]
> È anche possibile utilizzare miniCRAN per preparare i pacchetti da utilizzare in Azure Machine Learning. Per ulteriori informazioni, vedere il blog: [utilizzando miniCRAN in Azure Machine Learning, da Michele Usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="prepare-packages-using-minicran"></a>Preparare i pacchetti utilizzando miniCRAN

Il **miniCRAN** pacchetto stesso dipende dal 18 altri pacchetti CRAN, tra cui è il **RCurl** pacchetto, che presenta una dipendenza di sistema sul **esposti all'interno di curl** pacchetto. Analogamente, creare un pacchetto **XML** presenta una dipendenza **esposti all'interno di libxml2**. 

Per questi motivi, è consigliabile compilare inizialmente il repository locale in un computer con accesso completo a Internet, in modo che è possibile soddisfare facilmente tutte le dipendenze. 

Dopo aver creato il repository, è possibile spostare il repository in un percorso diverso.

### <a name="step-1-install-the-minicran-package"></a>Passaggio 1. Installare il pacchetto miniCRAN

Iniziare creando un **miniCRAN** repository da utilizzare come origine. In un computer con accesso a internet, è necessario creare questo repository.

1. Installare il **miniCRAN** pacchetto e la **igraph** pacchetto. Questo esempio viene verificata se il pacchetto è già installato, ma è possibile ignorare se le istruzioni e installare i pacchetti direttamente.

    ```R
    if(!require("miniCRAN")) install.packages("miniCRAN") 
    if(!require("igraph")) install.packages("igraph") 
    library("miniCRAN")
    ```

### <a name="step-2-define-a-package-source-a-cran-mirror-or-an-mran-snapshot"></a>Passaggio 2. Definire un'origine del pacchetto: un mirror CRAN o uno snapshot MRAN

1. Specificare un sito mirror da utilizzare nel recupero dei pacchetti. Nell'area che contiene i pacchetti che necessari, ad esempio, è possibile utilizzare il sito MRAN o qualsiasi altro sito. Se si verifica un errore di download, provare un altro sito mirror.

    ```R
    CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
    CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
    ```

2. Digitare il nome di una cartella locale in cui archiviare i pacchetti raccolti. 

    Assicurarsi di creare la cartella in anticipo. Viene generato un errore se il `local_repo` cartella non esiste quando si esegue il codice R in un secondo momento.

    La cartella deve disporre di un nome descrittivo. Qui è stata utilizzata la "miniCRAN", ma se si ripete questa spesso, è probabilmente deve utilizzare un nome più descrittivo, ad esempio "miniCRANZooPackages" o "miniCRANMyRPackagev2".

    ```R
    local_repo <- "~/miniCRAN"
    ```

    L'operatore di espansione tilde restituisce una variabile di ambiente, con risultati equivalente a `Sys.getenv("R_USER")`.

### <a name="step-3-add-packages-to-the-repository"></a>Passaggio 3. Aggiungere pacchetti al repository

1. Dopo aver **miniCRAN** è installato, creare un elenco che specifica i pacchetti aggiuntivi che si desidera scaricare.

    Eseguire **non** aggiungere dipendenze a questo elenco iniziale. Il **igraph** utilizzato dal pacchetto **miniCRAN** genera l'elenco delle dipendenze. Per ulteriori informazioni su come usare il grafico di dipendenze generato, vedere [utilizzando miniCRAN per identificare le dipendenze del pacchetto](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

    Il seguente script di R aggiunge i pacchetti di destinazione, "zoo" e "previsione" a una variabile.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```
2. Non è necessario che tracciare il grafico delle dipendenze, ma può essere informativo.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Creare il repository locale. Assicurarsi di modificare la versione di R, se necessario

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

    Tali informazioni, il pacchetto miniCRAN crea la struttura di cartelle che si desidera copiare i pacchetti di [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] in un secondo momento.

4. A questo punto è una cartella contenente i pacchetti necessari e tutti i pacchetti aggiuntivi che sono stati necessari.

    È possibile eseguire il codice seguente per elencare i pacchetti contenuti nel repository miniCRAN.

    ```R
    pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
    head(pdb);
    pdb$Package;
    pdb[, c("Package", "Version", "License")]
    ```

### <a name="step-4-use-the-repository-to-add-r-packages-to-the-instance-library"></a>Passaggio 4. Utilizzare il repository per aggiungere pacchetti R per la libreria di istanza

Dopo avere creato il repository e avere aggiunto i pacchetti che necessari, è necessario spostare il repository di pacchetti nel computer server e verificare che i pacchetti R installati nella libreria corretta per l'utilizzo di SQL Server.

La procedura seguente viene descritto come installare i pacchetti utilizzando gli strumenti di R.

1. Copiare la cartella contenente il repository miniCRAN, nella sua interezza, al server in cui si prevede di installare i pacchetti. La cartella contiene in genere questa struttura: radice miniCRAN > -> bin -> windows -> pensionistici -> versione non -> tutti i pacchetti.

2. Aprire un prompt dei comandi di R usando lo strumento di R associato all'istanza.

    - Per SQL Server 2017, la cartella predefinita è `C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library`.

    - Per SQL Server 2016, la cartella predefinita è `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library`.

    - Per un'istanza denominata, il percorso predefinito sarà simile al seguente: `<instance_path>.RTEST/R_SERVICES/library`.

    -  Se SQL Server è stato installato in un'unità diversa o se sono state apportate altre modifiche al percorso di installazione, assicurarsi di applicare anche tali modifiche.

3. Ottenere il percorso per la libreria di istanza e aggiungerlo all'elenco di percorsi di libreria.

    ```R
    .libPaths()[1];
    lib <- .libPaths()[1]
    ```

    In SQL Server, questo comando deve restituire il percorso della libreria associato all'istanza, ad esempio: "c: o programma file/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/libreria"

4. Specificare il nuovo percorso nel server in cui è stato copiato il **miniCRAN** repository, come `server_repo`.

    In questo esempio si presuppone che copiato il repository in una cartella temporanea sul server.

    ```R
    source_repo <- "C:\\temp\\miniCRAN"
    ```

5. Poiché utilizza una nuova area di lavoro R nel server, fornire anche l'elenco di pacchetti da installare.

    ```R
    tspackages <- c("zoo", "forecast")
    ```

6. Installare i pacchetti, indicando il percorso della copia locale del repository miniCRAN.

    ```R
    install.packages(tspackages, repos = file.path("file://", normalizePath;(source_repo, winslash = "/")), lib = lib, type = "win.binary", dependencies = TRUE);
    ```

7. Dalla raccolta di istanza, è possibile visualizzare i pacchetti installati tramite un comando simile al seguente:

    ```R
    installed.packages()
    ```

> [!NOTE] 
> Per utilizzare il pacchetto in SQL Server, è necessario installare i pacchetti in libreria predefinita utilizzata dall'istanza. 

## <a name="manually-install-a-single-package-from-a-zipped-file"></a>Installare manualmente un singolo pacchetto da un file compresso

Se si sta installando un singolo pacchetto che non è presenti dipendenze, o non è possibile utilizzare **miniCRAN**, è possibile scaricare manualmente il pacchetto è necessario. A tale scopo è necessario che sei un amministratore o unico proprietario di un server.

Dopo aver scaricato i pacchetti, installare i pacchetti R dal percorso del file compresso.

1. Scaricare il pacchetto come file compresso e salvarlo in una cartella locale

2. Copiare la cartella per il [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] computer.

3. Installare i pacchetti nella libreria di istanza di SQL Server utilizzando i comandi di R convenzionali. Se non sono state incluse le dipendenze di pacchetto che non sono già installati, l'installazione potrebbe non riuscire. 

È inoltre possibile caricare i singoli pacchetti in un'istanza di SQL Server 2017, utilizzando il [istruzione Crea raccolta esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql). Questo processo è inoltre necessario accesso amministrativo.
