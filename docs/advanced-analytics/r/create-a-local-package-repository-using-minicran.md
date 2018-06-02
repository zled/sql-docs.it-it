---
title: Creare un repository di pacchetti R locale utilizzando miniCRAN (SQL Server Machine Learning) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1f7ba3b4acde90d9e416eb092ac80cb0dfcbba8a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585643"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Creare un repository di pacchetti R locale utilizzando miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) pacchetto, creato da [Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html), identifica e scaricare i pacchetti e le dipendenze in un'unica cartella, è possibile copiare in altri computer per l'installazione di pacchetti R offline.

Come input, specificare uno o più pacchetti. **miniCRAN** legge l'albero delle dipendenze per questi pacchetti in modo ricorsivo e Scarica solo i pacchetti elencati e le relative dipendenze da CRAN o repository simili.

Come output **miniCRAN** viene creato un repository internamente coerente costituito da pacchetti selezionati e le dipendenze richieste. È quindi possibile spostare questo repository locale nel server di e continuare a installare i pacchetti senza una connessione internet.

> [!NOTE]
> Gli utenti esperti di R esaminare spesso per l'elenco dei pacchetti dipendenti nel file di descrizione per il pacchetto scaricato. Tuttavia, i pacchetti elencati **importazioni** potrebbero avere delle dipendenze di secondo livello. Per questo motivo, è consigliabile **miniCRAN** per assemblare l'insieme completo di pacchetti richiesti.

## <a name="why-create-a-local-repository"></a>Informazioni sulla creazione di un repository locale

L'obiettivo di creazione di un repository di pacchetti locali consiste nello specificare un singolo percorso che un amministratore del server o ad altri utenti nell'organizzazione possono utilizzare per installare i nuovi pacchetti di R in un server, in particolare quelle che non dispone dell'accesso a internet. Dopo aver creato il repository, è possibile modificarla in aggiungendo nuovi pacchetti o l'aggiornamento della versione dei pacchetti esistenti.

Repository di pacchetto sono utili in questi scenari:

- **Sicurezza**: R molti utenti sono abituati a download e installazione di nuovi pacchetti R quando è necessario, da CRAN o uno dei relativi siti di mirror. Tuttavia, per motivi di sicurezza, il server di produzione in esecuzione [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] in genere non dispongono di connettività internet.

- **Più facile installazione offline**: installare il pacchetto a un server non in linea richiede che è anche di scaricare tutte le dipendenze di pacchetto, tramite miniCRAN rende più semplice ottenere tutte le dipendenze nel formato corretto.

    Tramite miniCRAN, è possibile evitare errori di dipendenza del pacchetto durante la preparazione di pacchetti per l'installazione con il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione.

- **Gestione della versione migliorata**: In un ambiente multiutente, esistono buone ragioni per evitare l'installazione senza restrizioni di più versioni del pacchetto nel server. Usare un repository locale per fornire un set coerenza di pacchetti per l'utilizzo da analisti. 

> [!TIP]
> È anche possibile utilizzare miniCRAN per preparare i pacchetti da utilizzare in Azure Machine Learning. Per ulteriori informazioni, vedere il blog: [utilizzando miniCRAN in Azure Machine Learning, da Michele Usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="install-minicran"></a>Installare miniCRAN

Il **miniCRAN** pacchetto stesso dipende dal 18 altri pacchetti CRAN, tra cui è il **RCurl** pacchetto, che presenta una dipendenza di sistema sul **esposti all'interno di curl** pacchetto. Analogamente, creare un pacchetto **XML** presenta una dipendenza **esposti all'interno di libxml2**. Per risolvere le dipendenze, è consigliabile compilare inizialmente il repository locale in un computer con accesso a internet. 

Eseguire i comandi seguenti in un computer con una base R, strumenti di R e connessione a internet. Si presuppone che si tratta *non* computer SQL Server. Installano i seguenti comandi di **miniCRAN** pacchetto e la **igraph** pacchetto. Questo esempio viene verificata se il pacchetto è già installato, ma è possibile ignorare se le istruzioni e installare i pacchetti direttamente.

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>Impostare il server mirror CRAN e snapshot MRAN

Specificare un sito mirror da utilizzare nel recupero dei pacchetti. Nell'area che contiene i pacchetti che necessari, ad esempio, è possibile utilizzare il sito MRAN o qualsiasi altro sito. Se si verifica un errore di download, provare un altro sito mirror.

```R
CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>Creare una cartella locale

Creare una cartella locale, ad esempio `C:\mylocalrepo` in cui archiviare i pacchetti raccolti. Se si ripete questa spesso, è probabilmente deve utilizzare un nome più descrittivo, ad esempio "miniCRANZooPackages" o "miniCRANMyRPackagev2".

Specificare la cartella come il repository locale. Sintassi di R utilizza una barra rovesciata per nomi di percorso, ovvero opposto dalle convenzioni Windows.

```R
local_repo <- "C:/mylocalrepo"
```

## <a name="add-packages-to-the-local-repo"></a>Aggiungere pacchetti per il repository locale

Dopo aver **miniCRAN** sia installato e caricato, creare un elenco che specifica i pacchetti aggiuntivi che si desidera scaricare.

Eseguire **non** aggiungere dipendenze a questo elenco iniziale. Il **igraph** utilizzato dal pacchetto **miniCRAN** genera l'elenco delle dipendenze. Per ulteriori informazioni su come usare il grafico di dipendenze generato, vedere [utilizzando miniCRAN per identificare le dipendenze del pacchetto](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

1. Aggiungere i pacchetti di destinazione, "in zoo" e "previsione" a una variabile.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. Facoltativamente, tracciare il grafico delle dipendenze, ma può essere informativo.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Creare il repository locale. Assicurarsi di modificare la versione di R, se necessario per la versione installata nell'istanza del Server SQL. Versione 3.2.2 è installata in SQL Server 2016, versione 3.3 è installata in SQL Server 2017. Se è stato eseguito un aggiornamento del componente, la versione potrebbe essere più recente. Per altre informazioni, vedere [Python e R ottenere informazioni sul pacchetto](determine-which-packages-are-installed-on-sql-server.md).

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   Tali informazioni, il pacchetto miniCRAN crea la struttura di cartelle che si desidera copiare i pacchetti di [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] in un secondo momento.

A questo punto è una cartella contenente i pacchetti necessari e tutti i pacchetti aggiuntivi che sono stati necessari. Il percorso dovrebbe essere simile a quello nell'esempio: C:\mylocalrepo\bin\windows\contrib\3.3 e pertanto deve contenere una raccolta di pacchetti compressi. Non decomprimere i pacchetti o rinominare i file.

Facoltativamente, eseguire il codice seguente per elencare i pacchetti contenuti nel repository locale miniCRAN.

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>Aggiungere pacchetti alla libreria di istanza

Dopo aver creato un repository locale con i pacchetti che è necessario, spostare il repository di pacchetti nel computer di SQL Server. La procedura seguente viene descritto come installare i pacchetti utilizzando gli strumenti di R.

1. Copiare la cartella contenente il repository miniCRAN, nella sua interezza, al server in cui si prevede di installare i pacchetti. La cartella contiene in genere questa struttura: miniCRAN radice > bin > windows > pensionistici > versione > tutti i pacchetti. Negli esempi seguenti si presuppone una cartella nell'unità radice: 

2. Aprire uno strumento di R associato all'istanza (ad esempio, è possibile utilizzare Rgui.exe). Fare doppio clic su **Esegui come amministratore** per consentire allo strumento di apportare aggiornamenti al sistema.

    - Per SQL Server 2017, è il percorso del file per RGUI `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`.

    - Per SQL Server 2016, percorso del file he per RGUI è `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Ottenere il percorso per la libreria di istanza e aggiungerlo all'elenco di percorsi di libreria. In SQL Server 2017, il percorso è simile all'esempio seguente.

    ```R
    outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
    ```

4. Specificare il nuovo percorso nel server in cui è stato copiato il **miniCRAN** repository, come `server_repo`.

    In questo esempio si presuppone che copiato il repository in una cartella temporanea sul server.

    ```R
    inputlib <- "C:/temp/mylocalrepo"
    ```

5. Poiché utilizza una nuova area di lavoro R nel server, fornire anche l'elenco di pacchetti da installare.

    ```R
    mypackages <- c("zoo", "forecast")
    ```

6. Installare i pacchetti, indicando il percorso della copia locale del repository miniCRAN.

    ```R
    install.packages(mypackages, repos = file.path("file://", normalizePath(inputlib, winslash = "/")), lib = outputlib, type = "win.binary", dependencies = TRUE);
    ```

7. Dalla raccolta di istanza, è possibile visualizzare i pacchetti installati tramite un comando simile al seguente:

    ```R
    installed.packages()
    ```

## <a name="see-also"></a>Vedere anche

+ [Ottenere informazioni sui pacchetti](determine-which-packages-are-installed-on-sql-server.md)
+ [Esercitazioni di R](../tutorials/sql-server-r-tutorials.md)
+ [Guide pratiche](sql-server-machine-learning-tasks.md)


