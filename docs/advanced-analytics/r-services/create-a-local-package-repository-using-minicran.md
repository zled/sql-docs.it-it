---
title: "Creare un Repository pacchetto locale utilizzando miniCRAN | Microsoft Docs"
ms.custom: ""
ms.date: "05/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 4
---
# Creare un Repository pacchetto locale utilizzando miniCRAN
Questo argomento viene descritto come creare un repository del pacchetto di R usando il pacchetto R **miniCRAN**. 

Poiché [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanze si trovano in genere in un server che non dispone di connettività Internet, il metodo standard per l'installazione di pacchetti R (il comando R `install.packages()`) potrebbe non funzionare, come il pacchetto di installazione non può accedere CRAN o ad altri siti di mirror.

Sono disponibili due opzioni per l'installazione di pacchetti da una condivisione locale o un repository:

+ Utilizzare il pacchetto miniCRAN per creare un repository dei pacchetti è necessario, quindi installare da questo repository. In questo argomento viene descritto il metodo miniCRAN.

+ Scaricare i pacchetti necessari e le relative dipendenze, come file zip e salvarli in una cartella locale e quindi copiare la cartella per il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer. Per ulteriori informazioni sul metodo di copia manuale, vedere [installare altri pacchetti in SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).


## Passaggio 1. Installare miniCRAN e scaricare i pacchetti 


1. Installare il pacchetto miniCRAN in un computer che ha accesso a Internet.

   ~~~~
   # Install miniCRAN ---------------------------------------------------

   if(!require("miniCRAN")) install.packages("miniCRAN")
   if(!require("igraph")) install.packages("igraph")
   library(miniCRAN)

   # Define the package source: a CRAN mirror, or an MRAN snapshot
   CRAN_mirror <- c(CRAN = "https://mran.microsoft.com/snapshot/2016-04-01")

   # Define the local download location
   local_repo <- "~/miniCRAN"
   ~~~~

2. Scaricare o installare i pacchetti che necessari per questo computer. Si creerà la struttura di cartelle che è necessario copiare i pacchetti di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] in un secondo momento.

   ~~~~
   # List the packages you need 
   # Do not specify dependencies
   pkgs_needed <- c("ggplot2", "ggdendro")
   ~~~~

3. Copiare il repository miniCRAN libreria R_SERVICES sul [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza.

## Passaggio 2. Installare i pacchetti nel computer SQL Server 

4. Nel [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer, eseguire il comando R  `install.packages()`. È possibile utilizzare uno degli strumenti installati con R [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], ad esempio Rgui.exe oppure è possibile eseguire il comando come parte di un [!INCLUDE[tsql_md](../../includes/tsql-md.md)] stored procedure.
5. Al prompt dei comandi per specificare un archivio, selezionare la cartella contenente i file che appena copiato; vale a dire il repository locale miniCRAN.

   ~~~~
   pkgs_needed <- c("ggplot2", "ggdendro")
   local_repo  <- "~/miniCRAN"
   
   .libPaths()[1]
   "C:/Program Files/Microsoft SQL Server/130/R_SERVER/library"

   lib <- .libPaths()[1]

   install.packages(pkgs_needed, 
                 repos = file.path("file://", normalizePath(local_repo, winslash = "/")),
                 lib = lib,
                 type = "win.binary",
                 dependencies = TRUE
                 )
   ~~~~

6. Verificare che siano stati installati i pacchetti eseguendo questo codice R.
   ~~~~
   installed.packages()
   ~~~~



## Riconoscimenti

L'origine di queste informazioni è in questo articolo da Andre de Vries, che ha sviluppato anche il pacchetto miniCRAN. Per informazioni dettagliate e una procedura dettagliata completa, vedere  [come installare R i pacchetti in un'istanza di SQL Server 2016 non in linea](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)