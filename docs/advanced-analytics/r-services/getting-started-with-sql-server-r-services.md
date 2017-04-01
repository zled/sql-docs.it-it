---
title: "Introduzione a SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 5b28a663-effe-41f6-9bda-eda95f0c6943
caps.latest.revision: 34
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 32
---
# Introduzione a SQL Server R Services
 Un tipico flusso di lavoro per la creazione di una soluzione di analisi avanzata inizia con l'esplorazione dei dati e la modellazione predittiva, mentre l'esperto di dati sviluppa gli script R e i modelli efficaci per l'attività specifica. Gli script e i modelli creati possono essere distribuiti in produzione e integrati in applicazioni nuove o esistenti.   
  
Servizi R per SQL Server è progettato per l'esecuzione di queste attività di analisi scientifica dei dati. È possibile continuare a lavorare con gli strumenti R o SQL preferiti e applicare l'analisi a miliardi di record senza hardware aggiuntivo, migliorare le prestazioni ed evitare spostamenti dei dati non necessari. A questo punto è possibile inviare il codice R in produzione senza doverlo riscrivere in un altro linguaggio. È semplice usare R anche per i calcoli statistici che potrebbero essere difficili da implementare tramite SQL. Allo stesso tempo, è possibile sfruttare le potenzialità di SQL Server per ottenere prestazioni ottimali usando funzionalità come il motore di database in memoria e gli indici columnstore.  
  
Le sezioni seguenti offrono una panoramica di alcuni flussi di lavoro di analisi tipici e sulla loro attivazione con Servizi R per SQL Server.  

> [!TIP] Vedere l'esercitazione per iniziare rapidamente. Verrà illustrato come una società di noleggio di sci può usare l'apprendimento automatico per prevedere i noleggi futuri e pianificare il personale per soddisfare la domanda.
> 
> [Build an intelligent app with SQL Server and R](https://www.microsoft.com/sql-server/developer-get-started/r) (Creare un'app intelligente con SQL Server e R)


  
-   **Sviluppo**  
  
     Gli esperti di dati usano R per esplorare i dati e creare modelli predittivi dalla propria workstation con l'ambiente IDE R preferito. L'esperto ripete test e ottimizzazione fino a quando non ottiene un modello predittivo valido. 
     
     I componenti client [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offrono tutti gli strumenti necessari all'esperto di dati per le attività di sperimentazione e sviluppo. Gli strumenti includono il runtime di R e la libreria del kernel matematico di Intel, che migliorano le prestazioni delle operazioni standard di R, oltre a un set di pacchetti R avanzati che supportano l'esecuzione del codice R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Come di consueto, gli esperti possono connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e aggiornare i dati nel client per l'analisi in locale. Una soluzione migliore consiste nell'usare le API **ScaleR** per trasferire i calcoli sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], evitando spostamenti costosi e non sicuri.  
  
     Per lo sviluppo di soluzioni R, gli esperti possono usare qualsiasi ambiente IDE Windows che supporti R, inclusi [Strumenti R per Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx) o RStudio.  
 
    ![rsql_keyscenario2](../../advanced-analytics/r-services/media/rsql-keyscenario2.PNG) 
 
     Per altre informazioni, vedere [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).  

  
-   **Ottimizzazione**  
  
     Quando analizzano set di dati di grandi dimensioni con R, gli esperti riscontrano frequenti problemi di prestazioni e scalabilità, poiché l'implementazione di common runtime è a thread singolo e riesce a gestire solo i set di dati che entrano nella memoria disponibile del computer locale. Per ottenere prestazioni migliori e lavorare con una maggior quantità di dati, l'esperto di dati può usare le API **ScaleR** incluse in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Il pacchetto **RevoScaleR** contiene le implementazioni di alcune delle funzioni R più diffuse, riprogettate per garantire parallelismo e scalabilità. Il pacchetto include anche funzioni che incrementano scalabilità e prestazioni trasferendo i calcoli sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dotato in genere di più memoria e potenza di calcolo.  
  
     Per altre informazioni, vedere [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).  
  
-   **Distribuzione**  
  
     Quando lo script R o il modello è pronto per l'uso in produzione, lo sviluppatore di database può incorporare il codice o il modello nelle stored procedure e richiamare il codice salvato da un'applicazione. L'archiviazione e l'esecuzione di codice R da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenta numerosi vantaggi: è possibile usare l'interfaccia intuitiva di [!INCLUDE[tsql](../../includes/tsql-md.md)] e tutti i calcoli avvengono nel database evitando spostamenti di dati non necessari. È possibile usare [!INCLUDE[tsql](../../includes/tsql-md.md)] per generare punteggi da un modello predittivo in produzione o restituire tracciati generati da R e presentarli in un'applicazione come [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
     Per ottimizzare il codice R incorporato nelle stored procedure di sistema, è consigliabile usare le API del pacchetto [ScaleR](https://msdn.microsoft.com/microsoft-r/rserver/rserver-scaler-getting-started) che possono elaborare set di dati con volumi più elevati. I pacchetti supportano l'esecuzione in-database per calcoli multithread, multicore e multiprocesso.  
  
     Quando è necessario distribuire codice R nell'ambiente di produzione, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre il meglio di R e SQL. È infatti possibile usare R per i calcoli statistici difficili da implementare con SQL e sfruttare la potenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ottenere prestazioni ottimali grazie a funzionalità quali il motore di database in memoria e gli indici columnstore.  
  
    ![rsql_keyscenario1](../../advanced-analytics/r-services/media/rsql-keyscenario1.PNG)  
  
     Per altre informazioni, vedere [Operatività del codice R](../../advanced-analytics/r-services/operationalizing-your-r-code.md).  
 
 > [!TIP] Per altre informazioni sull'integrazione di SQL Server con l'analisi scientifica dei dati, vedere il manuale [Data Science with Microsoft SQL Server 2016](https://mva.microsoft.com/ebooks/) (Analisi scientifica dei dati con Microsoft SQL Server 2016) disponibile come download gratuito in Microsoft Virtual Academy

-   **Gestione e monitoraggio**  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] usa una nuova architettura di estendibilità che protegge il motore di database e isola le sessioni di R. Consente inoltre di controllare gli utenti autorizzati a eseguire gli script R e di specificare quali database sono accessibili dal codice R. : è possibile controllare la quantità di risorse allocate al runtime di R, per evitare che calcoli di grande entità possano compromettere le prestazioni complessive del server.  
  
     Se i processi di R vengono eseguiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile controllare i dati usati dagli analisti o pianificare i processi e creare flussi di lavoro che contengono script R, esattamente come accade con altre stored procedure.  
  
     Per altre informazioni, vedere [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
  
  
-   **Integrazione**  
  
     Non è più necessario investire il budget IT in strumenti enterprise per funzionano con un ambiente di runtime R esterno. Si può lavorare nell'ormai familiare ambiente di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e sviluppare flussi di lavoro integrati e soluzioni per la creazione di report con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
     Per altre informazioni, vedere [Creazione di flussi di lavoro che usano R in SQL Server](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md).  
  
  
## <a name="how-do-i-get-it"></a>Come si ottiene?  
   
  
+   **Installare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] o versione successiva e abilitare Servizi R (In-Database)** )  
  
    [Configurare Servizi R per SQL Server &#40;In-Database&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
  
-   **Configurare una workstation client**  
  
     [Configurare un client per l'analisi scientifica dei dati](../../advanced-analytics/r-services/set-up-a-data-science-client.md)  
   
> [!TIP]   
>   
> È necessario creare un server per i processi R ma non è necessario SQL Server? Provare [Microsoft R Server](https://msdn.microsoft.com/library/mt674874.aspx).  
  
## <a name="how-to-run-r-code-using-sql-server-r-services"></a>Come eseguire codice R con SQL Server R Services  
 Dopo aver completato l'installazione, è possibile eseguire il codice R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] incorporando R nelle stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] o creando script R specifici per l'uso con dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Informazioni su come chiamare R da un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] e restituire i risultati in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
     [Usare il codice R in Transact-SQL](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)  
  
-   Informazioni sul flusso completo per la creazione di una soluzione di analisi avanzata dei dati e la distribuzione tramite Servizi R per SQL Server  
  
     [Procedura dettagliata end-to-end per l'analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)  
  
-   Informazioni sull'uso del pacchetto RevoScaleR per un'analisi scalabile e ad alte prestazioni e sull'invio dei calcoli R al computer SQL Server  
  
     [Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
-   Incorporare script R funzionanti nelle stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] in modo da poter chiamare i modelli per la stima, ripetere il training dei modelli o ottenere stime dalle applicazioni  
  
     [Analisi avanzata nel database per sviluppatori SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
  
-   Usare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e i relativi strumenti di business intelligence nello stack [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per automatizzare i processi di machine learning. È possibile automatizzare la preparazione dei dati e la creazione di report con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]e visualizzare grafici R e altri report con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] o Power View.  
  
+ Per altri esempi, inclusi modelli di soluzioni e codice R di esempio  
   [SQL Server R Services Tutorials](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi R per SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Introduzione a Microsoft R Server &#40;Standalone&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  