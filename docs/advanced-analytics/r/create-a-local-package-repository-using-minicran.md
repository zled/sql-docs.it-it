---
title: Creare un repository di pacchetti locali tramite miniCRAN | Documenti Microsoft
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: c7b9e1f9dfa77d8852ddbadde773a7809aabcaeb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="create-a-local-package-repository-using-minicran"></a>Creare un repository di pacchetti locali tramite miniCRAN

Esistono due modi che è possibile preparare i pacchetti R per l'installazione in un server senza accesso a internet.

-   [Utilizzare il pacchetto miniCRAN per creare un unico archivio locale](#bkmk_miniCRAN)

    Il [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) viene creato un repository internamente coerente costituito da pacchetti selezionati dal repository CRAN simile. L'utente specifica un set di pacchetti desiderati e legge l'albero delle dipendenze per questi pacchetti in modo ricorsivo miniCRAN e Scarica solo i pacchetti elencati e le relative dipendenze.

    È quindi possibile spostare questo repository locale nel server di e continuare a installare i pacchetti senza utilizzare internet.

-   [Scaricare e copiare i pacchetti uno manualmente](#bkmk_manual)

    È possibile trovare l'elenco dei pacchetti dipendenti nel file di descrizione per il pacchetto scaricato. 
    
    Tuttavia, i pacchetti elencati **importazioni** potrebbero avere delle dipendenze di secondo livello. Per questo motivo, è consigliabile l'utilizzo del **miniCRAN** metodo.

> [!TIP]
> Non tutti sanno che è possibile utilizzare miniCRAN per preparare i pacchetti da utilizzare in Azure Machine Learning. Per ulteriori informazioni, vedere il blog: [utilizzando miniCRAN in Azure Machine Learning, da Michele Usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="prepare-packages-using-minicran"></a>Preparare i pacchetti utilizzando miniCRAN

L'obiettivo di creazione di un repository di pacchetti locali è fornire un singolo percorso che un amministratore del server o ad altri utenti nell'organizzazione consente di installare i nuovi pacchetti di R in un server che non dispone dell'accesso a internet.

Il [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) dal pacchetto per R è stato scritto dal [Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html) per renderne più semplice creare un coerente gestiti set di pacchetti R per un'organizzazione. 

Esistono numerosi vantaggi nell'utilizzo miniCRAN per creare il repository:

-   **Sicurezza**: R molti utenti sono abituati a download e installazione di nuovi pacchetti R quando è necessario, da CRAN o uno dei relativi siti di mirror. Tuttavia, per motivi di sicurezza, il server di produzione in esecuzione [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] in genere non dispongono di connettività internet.

-   **Più facile installazione offline**: installare il pacchetto a un server non in linea richiede che è anche di scaricare tutte le dipendenze di pacchetto, tramite miniCRAN rende più semplice ottenere tutte le dipendenze nel formato corretto.

-   **Gestione della versione migliorata**: In un ambiente multiutente, esistono buone ragioni per evitare l'installazione senza restrizioni di più versioni del pacchetto nel server.

Dopo aver creato il repository, è possibile modificarla in aggiungendo nuovi pacchetti o l'aggiornamento della versione dei pacchetti esistenti.

> [!NOTE]
> Il pacchetto miniCRAN dipende dal 18 altri pacchetti CRAN, tra cui è il pacchetto RCurl, che presenta una dipendenza del sistema del pacchetto esposti all'interno di curl. Analogamente, XML del pacchetto ha una dipendenza su esposti all'interno di libxml2. È consigliabile pertanto che si compila il repository locale inizialmente in un computer con accesso completo a Internet, in modo che è possibile soddisfare facilmente tutte le dipendenze. Dopo aver creato, è possibile spostare il repository in un percorso diverso.

### <a name="step-1-install-the-minicran-package"></a>Passaggio 1. Installare il pacchetto miniCRAN

Iniziare creando un repository miniCRAN da utilizzare come origine. In un computer con accesso a internet, è necessario creare questo repository.

1.  Installare il pacchetto miniCRAN e obbligatorio **igraph** pacchetto.

    ```R
    if(!require("miniCRAN")) install.packages("miniCRAN") if(!require("igraph"))
    install.packages("igraph") library(miniCRAN)
    ```

### <a name="step-2-define-a-package-source-a-cran-mirror-or-an-mran-snapshot"></a>Passaggio 2. Definire un'origine del pacchetto: un mirror CRAN o uno snapshot MRAN

1. Specificare un sito mirror da utilizzare nel recupero dei pacchetti.

    ```R
    CRAN_mirror \<- c(CRAN = "https://mran.microsoft.com/snapshot/2017-08-01")
    ```

2.  Digitare il nome di una cartella locale in cui archiviare i pacchetti raccolti. 

    Assicurarsi di creare la cartella in anticipo. Viene generato un errore se il `local_repo` cartella non esiste quando si esegue il codice R in un secondo momento.

    La cartella deve disporre di un nome descrittivo. Ad esempio, evitare "miniCRAN" e invece del tipo di un elemento come "GeneticsPackages" o "TeamRPackages1.0.2".

    ```R
    local_repo <- "~/miniCRAN"
    ```

    L'operatore di espansione tilde restituisce una variabile di ambiente, con risultati equivalente a `Sys.getenv("R_USER")`.

### <a name="step-3-add-packages-to-the-repository"></a>Passaggio 3. Aggiungere pacchetti al repository

1.  Dopo aver installato miniCRAN, creare un elenco che specifica i pacchetti aggiuntivi che si desidera scaricare.

    Non aggiungere dipendenze a questo elenco iniziale. il **igraph** pacchetto utilizzato dal miniCRAN genera l'elenco delle dipendenze. Per ulteriori informazioni su come usare il grafico di dipendenze generato, vedere [utilizzando miniCRAN per identificare le dipendenze del pacchetto](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

    Lo script R seguente viene illustrato come ottenere i pacchetti di destinazione, "zoo" e "previsione".

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```
2. Non è necessario che tracciare il grafico delle dipendenze, ma può essere informativo.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Creare il repository locale. Assicurarsi di modificare la versione di R, se necessario

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror)
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3")
    ```

    Tali informazioni, il pacchetto miniCRAN crea la struttura di cartelle che si desidera copiare i pacchetti di [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] in un secondo momento.

4. A questo punto è una cartella contenente i pacchetti necessari e tutti i pacchetti aggiuntivi che sono stati necessari.

    È possibile eseguire il codice seguente per elencare i pacchetti contenuti nel repository miniCRAN.

    ```R
    pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE)
    head(pdb)
    pdb$Package
    pdb[, c("Package", "Version", "License")]
    ```

### <a name="step-4-use-the-repository-to-add-r-packages-to-the-instance-library"></a>Passaggio 4. Utilizzare il repository per aggiungere pacchetti R per la libreria di istanza

Dopo avere creato il repository e avere aggiunto i pacchetti che necessari, è necessario spostare il repository di pacchetti nel computer server e verificare che i pacchetti R installati nella libreria corretta per l'utilizzo di SQL Server.

A seconda della versione di SQL Server, esistono due opzioni per l'aggiunta di nuovi pacchetti nella libreria R associati all'istanza di SQL Server:

- Installare la libreria di istanza utilizzando gli strumenti di R e il repository miniCRAN.

- Carica pacchetti a un database di SQL Server e installarlo mediante l'istruzione CREATE libreria esterna. Questa opzione richiede SQL Server 2017. Vedere [installare pacchetti R aggiuntivi su SQL Server](install-additional-r-packages-on-sql-server.md).

La procedura seguente viene descritto come installare i pacchetti utilizzando gli strumenti di R.

1. Copiare la cartella contenente il repository miniCRAN, nella sua interezza, al server in cui si prevede di installare i pacchetti.

2. Aprire un prompt dei comandi di R usando lo strumento di R associato all'istanza.

    - Per SQL Server 2017, la cartella predefinita è `C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library`.

    - Per SQL Server 2016, la cartella predefinita è `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library`.

    - Per un'istanza denominata, il percorso predefinito sarà simile al seguente: `<instance_path>.RTEST/R_SERVICES/library`.

    -  Se SQL Server è stato installato in un'unità diversa o se sono state apportate altre modifiche al percorso di installazione, assicurarsi di applicare anche tali modifiche.

3.  Ottenere il percorso per la libreria di istanza e aggiungerlo all'elenco di percorsi di libreria.

    ```R
    .libPaths()[1]  
    lib \<- .libPaths()[1]
    ```

    In SQL Server, questo comando deve restituire il percorso della libreria associato all'istanza, ad esempio: "c: o programma file/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/libreria"

4.  Specificare il percorso nel server in cui è stato copiato il repository mininCRAN in `server_repo`.

    In questo esempio si presuppone che copiato il repository nella cartella utente nel server.

    ```R
    R server_repo <- "C:\\Users\\MyUserName\\miniCRAN"
    ```

5.  Poiché utilizza una nuova area di lavoro R nel server, fornire anche l'elenco di pacchetti da installare.

    ```R
    tspackages <- c("zoo", "forecast")
    ```

6.  Installare i pacchetti, indicando il percorso della copia locale del repository miniCRAN.

    ```R
    install.packages(tspackages, repos = file.path("file://", normalizePath(server_repo, winslash = "/")), lib = lib, type = "win.binary", dependencies = TRUE)
    ```

7.  Dalla raccolta di istanza, è possibile visualizzare i pacchetti installati tramite un comando simile al seguente:

    ```R
    installed.packages()
    ```

> [!NOTE] 
> In SQL Server, un amministratore del server installare pacchetti dal repository miniCRAN nella libreria predefinita utilizzata dall'istanza. 

## <a name="manually-download-single-packages"></a>Scaricare manualmente i pacchetti singoli

Se non si desidera utilizzare miniCRAN, è possibile scaricare manualmente i pacchetti che necessari e le relative dipendenze. A tale scopo è necessario che sei un amministratore o unico proprietario di un server.

Dopo aver scaricato i pacchetti, installare i pacchetti R dal percorso del file compresso.

1. Scaricare i file zip di pacchetti e salvarli in una cartella locale

2. Copiare la cartella per il [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] computer.

3. Installare i pacchetti nella libreria di istanza di SQL Server.

> [!NOTE]
> Quando si utilizzano strumenti R per installare i pacchetti, vengono installate per l'istanza nel suo complesso. 
> 
> Se si desidera installare il pacchetto in un database e condividere il pacchetto con gli utenti che utilizzano i ruoli del database, è necessario caricare la libreria utilizzando l'istruzione CREATE libreria esterna. Vedere [installare pacchetti R aggiuntivi in SQL Server](install-additional-r-packages-on-sql-server.md)
