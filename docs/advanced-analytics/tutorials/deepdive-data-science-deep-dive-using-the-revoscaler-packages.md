---
title: 'Approfondimento di analisi scientifica dei dati: usare i pacchetti RevoScaleR con SQL Server | Documenti Microsoft'
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: a8fe18a578391beaae79259440779b0a76336ee2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="data-science-deep-dive-using-the-revoscaler-packages-with-sql-server"></a>Approfondimento di analisi scientifica dei dati: usare i pacchetti RevoScaleR con SQL Server

In questa esercitazione viene illustrato come utilizzare i pacchetti R avanzati disponibili in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] per lavorare con dati di SQL Server e creare soluzioni R scalabili, utilizzando il server come un contesto di calcolo per analitica dati ad alte prestazioni.

Informazioni su come creare un contesto di calcolo remoto, spostare i dati tra i contesti di calcolo locali e remoti ed eseguire il codice R in un Server SQL remoto. Inoltre illustrato come analizzare e tracciare i dati in locale e nel server remoto e come creare e distribuire i modelli.

> [!NOTE]
> 
> In questa esercitazione funziona in modo specifico con dati di SQL Server in Windows e utilizza i contesti di calcolo nel database. Se si desidera usare il linguaggio R in altri contesti, ad esempio Teradata, Linux o Hadoop, vedere queste esercitazioni Microsoft R Server: 
> + [Utilizzare Server R con sparklyr](https://docs.microsoft.com/machine-learning-server/r/tutorial-sparklyr-revoscaler)
> + [Explore R and ScaleR in 25 Functions](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler) (Esplorare R e ScaleR in 25 funzioni)
> + [Introduzione a ScaleR in Hadoop MapReduce](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-hadoop)

## <a name="overview"></a>Panoramica

Per la potenza flessibilità e l'elaborazione del pacchetto RevoScaleR, in questa esercitazione è spostare dati e spazio di swapping contesti di calcolo di frequente. Per illustrare, ecco alcune delle attività in questa esercitazione:

+ I dati vengono inizialmente ottenuti dai file CSV o XDF. Importare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando le funzioni nel pacchetto RevoScaleR.
+ Modello di training e assegnazione dei punteggi viene eseguito utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contesto di calcolo. 
+ Utilizzare le funzioni RevoScaleR per creare nuovi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle per salvare i risultati del punteggio.
+ Creare grafici sia nel server e contesto di calcolo locale.
+ Eseguire il training di un modello di dati presenti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, l'esecuzione di R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.
+ Estrarre un subset di dati e salvarlo come file con estensione XDF per il riutilizzo di analisi nella workstation locale.
+ Ottenere i nuovi dati per il punteggio, aprendo una connessione ODBC per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database. Il punteggio viene eseguito nella workstation locale.
+ Creare una funzione R personalizzata ed eseguirlo nel server il contesto di calcolo per eseguire una simulazione.

### <a name="article-list-and-time-required"></a>Elenco di articolo e il tempo necessario

In questa esercitazione richiede circa 75 minuti per completare, senza includere il programma di installazione.

1. [Utilizzo dei dati di SQL Server mediante R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
2. [Creare oggetti dati di SQL Server usando RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
3. [Eseguire query e modificare i dati SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
4. [Definire e usare i contesti di calcolo](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
5. [Creare ed eseguire gli script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
6. [Visualizzare i dati di SQL Server con R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
7. [Creare modelli R](../../advanced-analytics/tutorials/deepdive-create-models.md)
8. [Punteggio nuovi dati](../../advanced-analytics/tutorials/deepdive-score-new-data.md)
9. [Trasformare i dati con R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)
10. [Caricare i dati in memoria usando rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
11. [Creare nuove tabelle di SQL Server utilizzando rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
12. [Eseguire un'analisi in blocchi tramite rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
13. [Analizzare i dati in un contesto di calcolo locale](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)
14. [Spostare i dati da SQL Server tramite il file con estensione XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
15. [Creare una simulazione semplice](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

### <a name="target-audience"></a>Destinatari

Questa esercitazione è destinata per gli esperti di dati o per gli utenti che una certa familiarità con R e attività di analisi scientifica dei dati, ad esempio i riepiloghi e creazione del modello.  Tuttavia, tutto il codice viene fornito, e quindi anche se si ha familiarità con R, è possibile eseguire il codice e seguire la procedura, supponendo che sia gli ambienti di client e i server necessari.

È inoltre necessario avere familiarità con [!INCLUDE[tsql](../../includes/tsql-md.md)] sintassi e per sapere come accedere a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database utilizzando gli strumenti come i seguenti:

+ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 
+ Strumenti di database in Visual Studio 
+ La versione gratuita [mssql estensione per il codice di Visual Studio](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).
  
> [!TIP]
> Salvare l'area di lavoro R tra le lezioni in modo da individuare facilmente il punto in cui è stata interrotta l'esercitazione.

### <a name="prerequisites"></a>Prerequisites

- **SQL Server con il supporto per R**
  
    Installare SQL Server 2016 e abilitare R Services (in-Database). In alternativa, installare SQL Server 2017 e abilitare i servizi di Machine Learning e scegliere il linguaggio R.
  
-  **Autorizzazioni per il database**
  
    Per eseguire le query usate per il training del modello, sono necessari i privilegi **db_datareader** per il database in cui sono archiviati i dati. Per eseguire R, l'utente deve disporre dell'autorizzazione, EXECUTE ANY EXTERNAL SCRIPT.

-   **Computer di sviluppo dell'analisi scientifica dei dati**
  
    È necessario installare i provider correlati e i pacchetti RevoScaleR nel computer utilizzato come ambiente di sviluppo R. Il modo più semplice per eseguire questa operazione consiste nell'installare Microsoft R Client, Microsoft R Server (Standalone) o Machine Learning Server (Standalone). 
      
    > [!NOTE] 
    > Altre versioni di Revolution R Enterprise o Revolution R Open non sono supportate.
    > 
    > Impossibile utilizzare una distribuzione open source di R in questa esercitazione, poiché solo le funzioni RevoScaleR è possono usare contesti di calcolo remoto.
  
-   **Pacchetti R aggiuntivi**
  
    In questa esercitazione, installare i pacchetti seguenti: **dplyr**, **ggplot2**, **ggthemes**, **reshape2**, e **e1071** . Le istruzioni sono incluse nell'esercitazione.
  
    Tutti i pacchetti devono essere installati in due posizioni: nel computer utilizzato per lo sviluppo di soluzioni R e nel computer SQL Server in cui vengono eseguiti gli script R. Se non si dispone dell'autorizzazione per installare i pacchetti nel computer del server, chiedere all'amministratore. 
    
    **Non installare i pacchetti in una libreria utente.** Nella libreria di pacchetti R che viene utilizzata dall'istanza di SQL Server, è necessario installare i pacchetti.

Per ulteriori informazioni, vedere [prerequisiti per le procedure dettagliate di analisi scientifica dei dati](../../advanced-analytics/tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md).

## <a name="next-step"></a>Passaggio successivo

[Utilizzo dei dati di SQL Server mediante R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)

