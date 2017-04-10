---
title: "Introduzione a Microsoft R Server (Standalone) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 16
---
# Introduzione a Microsoft R Server (Standalone)
  Microsoft R Server (Standalone) consente di introdurre il diffuso linguaggio open source R nell'organizzazione, per abilitare soluzioni di analisi ad alte prestazioni e l'integrazione con altre applicazioni aziendali.  
  
## Che cos'è Microsoft R Server?  
 Microsoft R Server (Standalone) include i pacchetti R avanzati sviluppati da Revolution Analytics e supporta le connessioni a diverse origini dati, ad esempio Hadoop, Teradata e altro ancora. Installando il server autonomo, è possibile creare un ambiente server per eseguire processi R complessi e scalabili.  
  
## Vantaggi dell'utilizzo di Server Microsoft R (autonomo)  
 R è il linguaggio di programmazione più potente del mondo per l'elaborazione statistica, il machine learning e la grafica ed è supportato da una ricca community globale di utenti, sviluppatori e collaboratori. L'uso di R in uno scenario aziendale presenta in genere alcuni problemi, soprattutto quando aumenta il volume dei dati o quando è necessario distribuire soluzioni in ambienti di produzione. Microsoft R Server risolve il problema di distribuire e rendere operativo il codice R.  
  
 Microsoft R Server può essere installato in qualsiasi computer Windows e include tutti i pacchetti R e strumenti di connettività per abilitare il contesto di elaborazione remota e supportare soluzioni scalabili, eseguibili in parallelo.  
  
 Microsoft R Server (autonomo) supporta questi scenari:  
  
-   **Uso di un server centrale per rendere operative le soluzioni R**  
  
     Il server autonomo garantisce prestazioni di R migliori senza dipendere da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Calcoli complessi o di risorse possono essere eseguiti nel server anziché in un computer portatile o di sviluppo che potrebbe disporre di risorse limitate.  
  
     È inoltre possibile centralizzare i processi, ad esempio, se è necessario assegnare un punteggio rispetto a un modello predittivo in produzione, oppure utilizzare Server R come un singolo punto di contatto per R viene tracciata e stime utilizzato nei report. 
     
     È inoltre consigliabile installare R Server (autonomo) nel computer SQL Server se è spesso necessario eseguire R all'esterno del contesto di SQL Server.
  
-   **Esplorazione dei dati e modellazione predittiva più potenti**  
  
     Per compilare soluzioni R il data scientist può usare qualsiasi workstation client e qualsiasi strumento di sviluppo R. Se la soluzione usa le API del pacchetto RevoScaleR, è possibile eseguire i calcoli sul server, che in genere ha una potenza di elaborazione e una memoria decisamente superiori. In questo modo, le soluzioni possono elaborare set di dati con volumi più elevati e sfruttare calcoli multithread, multicore, multiprocesso.  
  
## Come si ottiene?  
 Per le istruzioni di installazione, vedere [Create a Standalone R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md). Tutti i componenti possono essere installati utilizzando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione.  
  
## Installare gli strumenti di R aggiuntive  
 Se non si dispone di un ambiente di sviluppo preferito R, sono disponibili molte opzioni. Per informazioni dettagliate, vedere [il programma di installazione o configurazione strumenti R](../../advanced-analytics/r-services/setup-or-configure-r-tools.md). 
 
 Per la connessione al Server Microsoft R o a SQL Server R Services da una workstation di analisi scientifica dei dati, si consiglia la versione gratuita [Microsoft R Client](http://aka.ms/rclient/download) (download).  
  
## Esecuzione Script R nel Server Microsoft R (autonomo)  
 Dopo aver configurato i componenti server e installato l'IDE preferito R, è possibile iniziare a sviluppare la soluzione con il pacchetto RevoScaleR. Queste API consentono di inviare comandi R a un server remoto per l'esecuzione.  
  
-   [Ridimensionamento](https://msdn.microsoft.com/microsoft-r/scaler-getting-started): avviare esplorare questa raccolta di funzioni analitiche distribuibile che offrono prestazioni elevate e scalabilità per le soluzioni di R. Include versioni eseguibili in parallelo di molti dei pacchetti, ad esempio clustering k-means, gli alberi delle decisioni e le foreste delle decisioni e strumenti per la manipolazione dei dati di modellazione R più diffusi. È inoltre possibile utilizzare HPC per costruire il proprio algoritmo parallelo.  
    
-   [DeployR](https://msdn.microsoft.com/microsoft-r/deployr-about): questo framework facoltativo fornisce gli strumenti per i programmatori R utilizzare Java, JavaScript o .net per integrare l'analisi di R output con un pacchetto di terze parti.  

È possibile utilizzare i dati in una varietà di formati, inclusi i file SAS, SPSS, Hadoop e testo. È possibile analizzare i dati sul posto o spostare i dati in modo efficiente in ambiente di sviluppo R locale usando il formato di file .xdf.  
  
Per iniziare con R Server, vedere la Guida in MSDN Library: [R Server - Introduzione](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started)  
  
 Per informazioni su come usare i pacchetti di ridimensionamento, vedere [un'esercitazione R nelle 25 funzioni](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#an-r-tutorial-in-25-functions-or-so)  
  
## Vedere anche  
 [Introduzione a SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  