---
title: Esercitazione su RevoScaleR funziona con SQL Server Machine Learning | Microsoft Docs
description: In questa esercitazione, informazioni su come chiamare funzioni RevoScaleR in SQL Server Machine Learning con R supportata abilitata.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ee810c998f8aecf17c3496540c65471e0b29e102
ms.sourcegitcommit: a083e9d59e2014a06cda9138b7e17c17ecab90e0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2018
ms.locfileid: "44343086"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Esercitazione: Funzioni RevoScaleR usano R con dati di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR è un pacchetto di Microsoft R che fornisce l'elaborazione parallela e distribuita per l'analisi scientifica dei dati e i carichi di lavoro di apprendimento automatico. Per lo sviluppo di R in SQL Server, RevoScaleR è uno dei pacchetti predefinita di core, con funzioni per l'impostazione di un contesto di calcolo, la gestione dei pacchetti, cosa più importante: utilizzo di dati end-to-end, dall'importazione per analisi e visualizzazione. Algoritmi di Machine Learning in SQL Server hanno una dipendenza da origini dati di RevoScaleR. Data l'importanza di RevoScaleR, informazioni su quando e come chiamare le funzioni è una competenza essenziale. 

In questa esercitazione si apprenderà come creare un contesto di calcolo remoto, spostare dati tra contesti di calcolo locali e remoti e di eseguire codice R in un Server SQL remoto. Verrà anche illustrato come analizzare e tracciare i dati in locale e nel server remoto e come creare e distribuire modelli.

+ I dati vengono inizialmente ottenuti dai file CSV o XDF. Importare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le funzioni nel pacchetto RevoScaleR.
+ Modello di training e di assegnazione dei punteggi viene eseguito utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contesto di calcolo. 
+ Usare funzioni RevoScaleR per creare un nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle per salvare i risultati della valutazione.
+ Creare tracciati sia nel server e contesto di calcolo locale.
+ Eseguire il training sui dati in un modello [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, esecuzione di R nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.
+ Estrarre un subset di dati e salvarlo come file XDF per usarlo nell'analisi nella workstation locale.
+ Ottenere i nuovi dati per la classificazione, aprendo una connessione ODBC per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database. Assegnazione dei punteggi viene eseguito nella workstation locale.
+ Creare una funzione R personalizzata ed eseguirlo nel server di contesto di calcolo per eseguire una simulazione.

## <a name="target-audience"></a>Destinatari

Questa esercitazione è destinata ai data Scientist o per le persone che hanno già una certa familiarità con R e con attività di analisi scientifica dei dati, ad esempio i riepiloghi e la creazione di modelli. Tuttavia, tutto il codice viene fornito, pertanto anche se si ha familiarità con R, è possibile eseguire il codice e seguire la procedura, presupponendo che siano i necessari ambienti server e client.

È anche opportuno avere familiarità con [!INCLUDE[tsql](../../includes/tsql-md.md)] sintassi e sapere come accedere a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database usando strumenti come i seguenti:

+ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 
+ Strumenti di database in Visual Studio 
+ La versione gratuita [estensione mssql per Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).
  
> [!TIP]
> Salvare l'area di lavoro R tra le lezioni in modo da individuare facilmente il punto in cui è stata interrotta l'esercitazione.

## <a name="prerequisites"></a>Prerequisiti

- **SQL Server con il supporto per R**
  
    Installare [servizi di SQL Server 2017 Machine Learning](../install/sql-machine-learning-services-windows-install.md) con la funzionalità R o installare [SQL Server 2016 R Services (in-Database)](../install/sql-r-services-windows-install.md).

    Assicurarsi che la creazione di script esterni è abilitato, il servizio Launchpad sia in esecuzione e di disporre di autorizzazioni per accedere al servizio.
  
-  **Autorizzazioni per il database**
  
    Per eseguire le query usate per il training del modello, sono necessari i privilegi **db_datareader** per il database in cui sono archiviati i dati. Per eseguire R, l'utente deve disporre dell'autorizzazione, EXECUTE ANY EXTERNAL SCRIPT.

-   **Computer di sviluppo di analisi scientifica dei dati**
  
    Per spostarsi avanti e indietro tra contesti di calcolo locali e remoti, è necessario disporre di due sistemi. Locale è in genere una workstation di sviluppo con la potenza di sufficienti per carichi di lavoro di analisi scientifica dei dati. Remote in questo caso è SQL Server 2017 o SQL Server 2016 con abilitata la funzionalità di R. 
    
    Il passaggio di contesti di calcolo viene affermato su aventi la stessa versione RevoScaleR nei sistemi locali e remoti. In una workstation locale, è possibile ottenere i pacchetti RevoScaleR e i provider correlati mediante l'installazione o mediante uno dei seguenti: [macchina virtuale Data Science in Azure](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview), [(gratuito) con Microsoft R Client](https://docs.microsoft.com/en-us/machine-learning-server/r-client/what-is-microsoft-r-client), o [ Microsoft Machine Learning Server (Standalone)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-install). Per l'opzione di server autonomi, installare l'edizione per sviluppatori gratuiti, tramite i programmi di installazione di Linux o Windows. È anche possibile usare il programma di installazione di SQL Server per installare un server autonomo.
      
-   **Pacchetti R aggiuntivi**
  
    In questa esercitazione, si installa i pacchetti seguenti: **dplyr**, **ggplot2**, **ggthemes**, **reshape2**, e **e1071** . Le istruzioni sono incluse nell'esercitazione.
  
    Tutti i pacchetti devono essere installati in due posizioni: nella workstation usata per lo sviluppo di soluzioni R e nel computer SQL Server in cui vengono eseguiti gli script R. Se non si dispone dell'autorizzazione per installare i pacchetti nel computer del server, chiedere all'amministratore. 
    
    **Non installare i pacchetti in una libreria utente.** I pacchetti devono essere installati nella libreria di pacchetti R che viene utilizzata dall'istanza di SQL Server.

## <a name="r-development-tools"></a>Strumenti di sviluppo R

Gli sviluppatori di R in genere usano gli IDE per la scrittura e debug del codice R. Di seguito sono riportati alcuni suggerimenti:

- **R Tools per Visual Studio** (RTVS) è disponibile gratuitamente come plug-in che offre Intellisense, debug e il supporto per Microsoft R. È possibile usarlo con R Server e SQL Server Machine Learning Services. Per scaricarlo, vedere [R Tools per Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **RStudio** è uno degli ambienti più diffusi per lo sviluppo di R. Per altre informazioni, vedere [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

- Strumenti R di base (R.exe, RTerm.exe, RScripts.exe) inoltre vengono installati per impostazione predefinita quando si installa R in SQL Server o Client R. Se non si desidera installare un IDE, è possibile utilizzare gli strumenti predefiniti di R per eseguire il codice in questa esercitazione.

È importante ricordare che è necessario RevoScaleR nei computer locali e remoti. È possibile completare questa esercitazione usando un'installazione generica di RStudio o un altro ambiente in cui Manca le librerie di Microsoft R. Per altre informazioni, vedere [Configurare un client per l'analisi scientifica dei dati](../r/set-up-a-data-science-client.md).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Lezione 1: Creare database e autorizzazioni](deepdive-work-with-sql-server-data-using-r.md)

