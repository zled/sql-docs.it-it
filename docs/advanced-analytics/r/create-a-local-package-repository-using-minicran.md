---
title: Creare un repository di pacchetti locale usando miniCRAN | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e8af93b3e132290eef4b43da568b9381ff8e5a04
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-local-package-repository-using-minicran"></a>Creare un repository di pacchetti locale usando miniCRAN
Questo argomento descrive come creare un repository di pacchetti R locale usando il pacchetto R **miniCRAN**. 

Poiché le istanze di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] si trovano in genere in un server senza connettività Internet, il metodo standard per installare i pacchetti (il comando R `install.packages()`) potrebbe non funzionare, perché il programma di installazione dei pacchetti non riesce ad accedere a CRAN o ad altri siti mirror.

Sono disponibili due opzioni per l'installazione dei pacchetti da una condivisione o un repository locale:

+ Usare il pacchetto miniCRAN per creare un repository locale dei pacchetti necessari, quindi eseguire l'installazione da questo repository. Questo argomento descrive il metodo basato su miniCRAN.

+ Scaricare i pacchetti necessari e le dipendenze come file ZIP, salvarli in una cartella locale e quindi copiare tale cartella nel computer [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Per altre informazioni sul metodo di copia manuale, vedere [Install Additional Packages on SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md) (Installare pacchetti aggiuntivi in SQL Server).


## <a name="step-1-install-minicran-and-download-packages"></a>Passaggio 1. Installare miniCRAN e scaricare i pacchetti 


1. Installare il pacchetto miniCRAN in un computer con accesso a Internet.

   ~~~~
   # Install miniCRAN and igraph

   if(!require("miniCRAN")) install.packages("miniCRAN")
   if(!require("igraph")) install.packages("igraph")
   library(miniCRAN)

   # Define the package source: a CRAN mirror, or an MRAN snapshot
   CRAN_mirror <- c(CRAN = "https://mran.microsoft.com/snapshot/2016-04-01")

   # Define the local download location
   local_repo <- "~/miniCRAN"
   ~~~~

2. Scaricare o installare i pacchetti necessari in questo computer usando lo script R seguente. che creerà la struttura di cartelle necessaria per copiare i pacchetti in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] in un secondo momento.

   ~~~~
   # List the packages to get. Do not specify dependencies.
   pkgs_needed <- c("ggplot2", "ggdendro")
   # Plot the dependency graph 
   plot(makeDepGraph(pkgs_needed)) 
   
   # Create the local repo 
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror) 
   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.2") 

   # List local packages 
   pdb <- as.data.frame( 
     pkgAvail(local_repo, type = "win.binary", Rversion = "3.2"),  
     stringsAsFactors = FALSE) 
   head(pdb) 
   pdb$Package 
   pdb[, c("Package", "Version", "License")] 
   ~~~~


## <a name="step-2-copy-the-minicran-repository-to-the-sql-server-computer"></a>Passaggio 2. Copiare il repository miniCRAN nel computer SQL Server 

Copiare il repository miniCRAN nella libreria R_SERVICES nell'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

+ Per SQL Server 2016, la cartella predefinita è `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library1`.
+ Per SQL Server 2017, la cartella predefinita è `C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library1`.

Se R Services è stato installato usando un'istanza denominata, assicurarsi di includere il nome dell'istanza nel percorso per essere certi che le librerie vengano installate nell'istanza corretta. Se ad esempio l'istanza denominata è RTEST02, il percorso predefinito per l'istanza denominata sarà: `C:\Program Files\Microsoft SQL Server\MSSQL13.RTEST02\R_SERVICES\library`.

Se SQL Server è stato installato in un'unità diversa o se sono state apportate altre modifiche al percorso di installazione, assicurarsi di applicare anche tali modifiche.

## <a name="step-3-install-the-packages-on-sql-server-using-the-minicran-repository"></a>Passaggio 3. Installare i pacchetti in SQL Server usando il repository miniCRAN

Nel computer [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] aprire una riga di comando R o RGUI come amministratore. 
  
> [!TIP]
> Poiché nel computer potrebbero essere presenti più librerie R, per assicurarsi che i pacchetti vengano installati nell'istanza corretta, usare la copia di RGUI o RTerm installata con l'istanza specifica in cui si vogliono installare i pacchetti.
  
Quando viene richiesto di specificare un repository, selezionare la cartella contenente i file appena copiati, ovvero il repository miniCRAN locale.

   ~~~~
   # Run this R code as administrator on the SQL Server computer 
   pkgs_needed <- c("ggplot2", "ggdendro") 
   local_repo  <- "~/miniCRAN" 

   # OPTIONAL: If you are not running R from the instance library as recommended, you must specify the path
   #   .libPaths()[1] 
   # "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library " 
   # lib <- .libPaths()[1]
   
   install.packages(pkgs_needed,  
                    repos = file.path("file://", normalizePath(local_repo, winslash = "/")), 
                    lib = lib, 
                    type = "win.binary", 
                    dependencies = TRUE 
                    ) 
   installed.packages() 
   ~~~~

Verificare che i pacchetti siano stati installati.
   ~~~~
   installed.packages()
   ~~~~



## <a name="acknowledgements"></a>Riconoscimenti

La fonte delle presenti informazioni è questo articolo di Andre de Vries, che ha anche sviluppato il pacchetto miniCRAN. Per informazioni dettagliate e una procedura dettagliata completa, vedere [How to install R packages on an off-line SQL Server 2016 instance](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html) (Come installare pacchetti R in un'istanza di SQL Server 2016 offline).

