---
title: 'Procedura approfondita di data science: Uso dei pacchetti RevoScaleR | Microsoft Docs'
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51f4a782ad941d8b9a66ba00cbf2b3540478361c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="data-science-deep-dive-using-the-revoscaler-packages"></a>Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR

In questa esercitazione viene illustrato come utilizzare i pacchetti R avanzati disponibili in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] per lavorare con dati di SQL Server e creare soluzioni R scalabili, utilizzando il server come un contesto di calcolo per analitica dati ad alte prestazioni.

Si apprenderà come creare un contesto di calcolo remoto, spostare i dati tra i contesti di calcolo locale e remoto ed eseguire codice R in un Server SQL remoto. Si apprenderà inoltre come analizzare e tracciare i dati in locale e nel server remoto e come creare e distribuire i modelli.

> [!NOTE]
> 
> In questa esercitazione funziona in modo specifico con dati di SQL Server in Windows e utilizza i contesti di calcolo nel database. Se si desidera usare il linguaggio R in altri contesti, ad esempio Teradata, Linux o Hadoop, vedere queste esercitazioni Microsoft R Server: 
> + [Utilizzare Server R con sparklyr](https://msdn.microsoft.com/microsoft-r/microsoft-r-get-started-spark-interop)
> + [Explore R and ScaleR in 25 Functions](https://msdn.microsoft.com/microsoft-r/microsoft-r-tutorial-r2revoscaler) (Esplorare R e ScaleR in 25 funzioni)
> + [Introduzione a ScaleR in Hadoop MapReduce](https://msdn.microsoft.com/microsoft-r/scaler-hadoop-getting-started)
> + [Guida introduttiva RevoScaleR Teradata recupero](https://msdn.microsoft.com/microsoft-r/scaler-teradata-getting-started)

## <a name="overview"></a>Panoramica

Per illustrare la flessibilità e le potenzialità di elaborazione dei pacchetti ScaleR, in questa esercitazione verranno spostati i dati e scambiati i contesti di calcolo di frequente.

+ I dati vengono inizialmente ottenuti dai file CSV o XDF. Verrà eseguita l'importazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le funzioni del pacchetto RevoScaleR.
+ Il training e l'assegnazione dei punteggi dei modelli verranno eseguiti nel contesto di calcolo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
    Verranno create nuove tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le funzioni **rx** per salvare i risultati dell'assegnazione dei punteggi.
+ Verranno creati tracciati sia nel contesto di calcolo del server che nel contesto di calcolo locale.
+ Per il training del modello, si useranno i dati già archiviati un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Tutti i calcoli verranno eseguiti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
+ Verrà estratto un subset di dati che verrà salvato come file XDF per usarlo nell'analisi nella workstation locale.
+ I nuovi dati usati durante il processo di valutazione vengono estratti dal database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando una connessione ODBC. Tutti i calcoli vengono eseguiti nella workstation locale.
+ Infine, verrà eseguita una simulazione in base a una funzione R personalizzata usando il contesto di calcolo del server.

### <a name="get-started-now"></a>Introduzione

In questa esercitazione richiede circa 75 minuti per completare, senza includere il programma di installazione.

1. [Lavorare con i dati di SQL Server con R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
2. [Creare oggetti dati di SQL Server usando RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
3. [Eseguire una query e modificare i dati SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
4. [Definire e utilizzare i contesti di calcolo](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
5. [Creare ed eseguire gli script R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
6. [Visualizzare i dati di SQL Server con R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
7. [Creare modelli R](../../advanced-analytics/tutorials/deepdive-create-models.md)
8. [Punteggio nuovi dati](../../advanced-analytics/tutorials/deepdive-score-new-data.md)
9. [Trasformare i dati usando R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)
10. [Caricare i dati in memoria usando rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
11. [Creare una nuova tabella di SQL Server utilizzando rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
12. [Eseguire l'analisi di suddivisione in blocchi utilizzando rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
13. [Analizzare i dati nel contesto di calcolo locale.](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)
14. [Spostare dati tra SQL Server e i File con estensione XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
15. [Creare una simulazione semplice](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

### <a name="target-audience"></a>Destinatari

Questa esercitazione è indirizzata agli analisti dei dati o a utenti che hanno già una certa familiarità con R e le attività di analisi dei dati, tra cui l'esplorazione, l'analisi statistica e la sintonizzazione dei modelli.  Tuttavia, tutto il codice viene fornito, pertanto anche se si ha familiarità con R, facilmente è possibile eseguire il codice e seguire la procedura, supponendo che sia gli ambienti di client e i server necessari.

È anche opportuno avere familiarità con la sintassi di [!INCLUDE[tsql](../../includes/tsql-md.md)] e sapere come accedere a un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o altri strumenti di database, ad esempio Visual Studio.
  
> [!TIP]
> Salvare l'area di lavoro R tra le lezioni in modo da individuare facilmente il punto in cui è stata interrotta l'esercitazione.

### <a name="prerequisites"></a>Prerequisiti

- **SQL Server con il supporto per R**
  
    Installare SQL Server 2016 e abilitare R Services (in-Database). In alternativa, installare SQL Server 2017 e abilitare i servizi di Machine Learning e scegliere il linguaggio R. Viene descritto il processo di installazione [documentazione Online di SQL Server 2016](http://msdn.microsoft.com/library/mt696069(SQL.130).aspx).
  
-  **Autorizzazioni per il database**
  
    Per eseguire le query usate per il training del modello, sono necessari i privilegi **db_datareader** per il database in cui sono archiviati i dati. Per eseguire R, l'utente deve disporre dell'autorizzazione, EXECUTE ANY EXTERNAL SCRIPT.

-   **Computer di sviluppo dell'analisi scientifica dei dati**
  
    È necessario installare anche i provider correlati e i pacchetti RevoScaleR nell'ambiente di sviluppo R. Il modo più semplice per eseguire questa operazione è di installare Microsoft R Client o Microsoft R Server (Standalone). Per altre informazioni, vedere [Configurare un client per l'analisi scientifica dei dati](http://msdn.microsoft.co/library/mt696067(SQL.130).aspx)
      
    > [!NOTE] 
    > Altre versioni di Revolution R Enterprise o Revolution R Open non sono supportate.
    > 
    > Una distribuzione open source di R, ad esempio R 3.2.2, non funzioneranno in questa esercitazione, poiché solo le funzioni RevoScaleR è possono usare contesti di calcolo remoto.
  
-   **Pacchetti R aggiuntivi**
  
    Per questa esercitazione, è necessario installare i pacchetti seguenti: **dplyr**, **ggplot2**, **ggthemes**, **reshape2**ed **e1071**. Le istruzioni sono incluse nell'esercitazione.
  
    Tutti i pacchetti devono essere installati in due posizioni: nel computer utilizzato per lo sviluppo di soluzioni R e nel computer SQL Server in cui verranno eseguiti gli script R. Se non si dispone dell'autorizzazione per installare i pacchetti nel computer del server, chiedere all'amministratore. **Non installare i pacchetti in una libreria utente.** È importante che i pacchetti installati nella libreria di pacchetti R che viene utilizzata dall'istanza di SQL Server.

Per ulteriori informazioni, vedere [prerequisiti per le procedure dettagliate di analisi scientifica dei dati](../../advanced-analytics/tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md).



## <a name="next-step"></a>Passaggio successivo

[Lavorare con i dati di SQL Server con R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)


