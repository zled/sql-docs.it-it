---
title: "Procedura approfondita per l&#39;analisi scientifica dei dati: Uso dei pacchetti RevoScaleR | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Procedura approfondita per l&#39;analisi scientifica dei dati: Uso dei pacchetti RevoScaleR
Questa esercitazione è un'introduzione ai pacchetti R avanzati disponibili in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Si apprenderà come usare il framework Enterprise scalabile per l'esecuzione di pacchetti R in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].   Usando queste funzioni R scalabili, un analista dei dati può creare soluzioni R personalizzate da eseguire in contesti locali o server per supportare l'analisi dei Big Data ad alte prestazioni.  
  
In questa esercitazione verrà illustrato come spostare i dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alla workstation R e viceversa, analizzare e tracciare i dati e creare e distribuire i modelli.  
    
## Panoramica 
 
Per illustrare la flessibilità e le potenzialità di elaborazione dei pacchetti ScaleR, in questa esercitazione verranno spostati i dati e scambiati i contesti di calcolo di frequente.

+ I dati vengono inizialmente ottenuti dai file CSV o XDF. Verrà eseguita l'importazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le funzioni del pacchetto RevoScaleR.    
+ Il training e l'assegnazione dei punteggi dei modelli verranno eseguiti nel contesto di calcolo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
    Verranno create nuove tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le funzioni **rx** per salvare i risultati dell'assegnazione dei punteggi.    
+ Verranno creati tracciati sia nel contesto di calcolo del server che nel contesto di calcolo locale.  
+ Per il training del modello, si useranno i dati già archiviati un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tutti i calcoli verranno eseguiti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    
+ Verrà estratto un subset di dati che verrà salvato come file XDF per usarlo nell'analisi nella workstation locale.    
+ I nuovi dati usati durante il processo di valutazione vengono estratti dal database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando una connessione ODBC. Tutti i calcoli vengono eseguiti nella workstation locale. 
+ Infine, verrà eseguita una simulazione in base a una funzione R personalizzata usando il contesto di calcolo del server.

### Introduzione  

Per completare questa esercitazione è necessaria circa un'ora, esclusa l'installazione.  

-   [Lezione 1: Usare dati SQL Server con R](../../advanced-analytics/r-services/lesson-1-work-with-sql-server-data-using-r-data-science-deep-dive.md)  
  
-   [Lezione 2: Creare ed eseguire script R](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
-   [Lezione 3: Trasformare i dati con R](../../advanced-analytics/r-services/lesson-3-transform-data-using-r-data-science-deep-dive.md)  
  
-   [Lezione 4: Analizzare i dati in un contesto di calcolo locale](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
-   [Lezione 5: Creare una simulazione semplice](../../advanced-analytics/r-services/lesson-5-create-a-simple-simulation-data-science-deep-dive.md)  

      
### Destinatari  
  
Questa esercitazione è indirizzata agli analisti dei dati o a utenti che hanno già una certa familiarità con R e le attività di analisi dei dati, tra cui l'esplorazione, l'analisi statistica e la sintonizzazione dei modelli.  Tuttavia, poiché il codice viene fornito, è sufficiente eseguire il codice e attenersi alle istruzioni, a condizione che vengano usati gli ambienti server e client richiesti.  
  
È anche opportuno avere familiarità con la sintassi di [!INCLUDE[tsql](../../includes/tsql-md.md)] e sapere come accedere a un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o altri strumenti di database, ad esempio Visual Studio.  
  
> [!TIP]  
> Salvare l'area di lavoro R tra le lezioni in modo da individuare facilmente il punto in cui è stata interrotta l'esercitazione.  
  
### Prerequisiti  
  
-   **Server di database con supporto per R**  
  
    Installare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e abilitare SQL Server R Services (in-Database). Questo processo è descritto nella [documentazione online di SQL Server 2016](http://msdn.microsoft.com/library/mt696069(SQL.130).aspx).  
  
-   **Autorizzazioni per il database**  
  
    Per eseguire le query usate per il training del modello, sono necessari i privilegi **db_datareader** per il database in cui sono archiviati i dati.  
  
  
-   **Workstation di analisi scientifica dei dati**  
  
    È necessario installare i pacchetti RevoScaleR. Il modo più semplice per eseguire questa operazione è installare Microsoft R Server (Standalone) o Microsoft R Client. Per altre informazioni, vedere [Configurare un client per l'analisi scientifica dei dati](http://msdn.microsoft.co/library/mt696067(SQL.130).aspx)
      
    > [!NOTE] 
    > Altre versioni di Revolution R Enterprise o Revolution R Open non sono supportate. 
    > 
    > Le distribuzioni open source di R, ad esempio R 3.2.2, non funzionano in questa esercitazione poiché solo la funzione ScaleR può usare contesti di calcolo remoti. 
  
-   **Pacchetti R aggiuntivi**  
  
    Per questa esercitazione, è necessario installare i pacchetti seguenti: **dplyr**, **ggplot2**, **ggthemes**, **reshape2** ed **e1071**. Le istruzioni sono incluse nell'esercitazione.  
  
    Tutti i pacchetti devono anche essere installati nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui si svolgerà la formazione. È importante che i pacchetti siano installati nella libreria di pacchetti R usata da SQL Server. **Non installare i pacchetti in una libreria utente.** Se non si ha l'autorizzazione per installare i pacchetti in questa cartella, chiedere a un amministratore del database di aggiungere i pacchetti.   
  
Per altre informazioni, vedere [Prerequisiti per le procedure dettagliate per l'analisi scientifica dei dati &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/prerequisites-for-data-science-walkthroughs-sql-server-r-services.md).  
  
## Strategie dei dati per le soluzioni R distribuite
    
In generale, prima di iniziare a scrivere ed eseguire gli script R nell'ambiente di sviluppo locale, è consigliabile dedicare sempre un minuto alla pianificazione dell'uso dei dati e determinare dove eseguire ogni parte della soluzione per ottenere prestazioni ottimali.  

In questa esercitazione verranno usate le funzioni ad alte prestazioni per l'analisi dei dati, la creazione di modelli e la creazione di grafici inclusi in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Queste funzioni vengono chiamate in generale ScaleR o Microsoft R per distinguerle dalle funzioni derivate da altri pacchetti R open source. Per altre informazioni sulle differenze tra Microsoft R e R open source, vedere questa [Guida introduttiva](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#microsoft-r-products). 

Uno dei vantaggi principali dell'uso delle funzioni ScaleR consiste nella possibilità di usare *origini dati* locali o server e *contesti di calcolo* locali o remoti.  Per questa ragione, durante l'esecuzione di questa esercitazione, considerare le strategie dei dati che potrebbero essere necessarie per le propri soluzioni.
  
-   **Che tipo di analisi si vuole eseguire?** Si prevede di svolgere il lavoro da soli o di condividere modelli, risultati o grafici con altri utenti?
 
    In questa esercitazione verrà illustrato come spostare i risultati dall'ambiente di sviluppo al server e viceversa per facilitare la condivisione e l'analisi. 
  
-   **Il pacchetto R necessario supporta l'esecuzione remota?** Tutte le funzioni dei pacchetti ScaleR inclusi in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] possono essere eseguite in contesti di calcolo remoti ed eventualmente usare l'esecuzione parallela. Al contrario, le funzioni dei pacchetti di terze parti potrebbero richiedere ulteriori risorse per l'esecuzione a thread singolo. 
    
    In questa esercitazione verrà illustrato come passare da un contesto di calcolo locale a un contesto remoto e viceversa per usare le risorse del server quando necessario. Verrà inoltre descritto come eseguire il wrapping delle funzioni R standard in *rxExec* per supportare l'esecuzione remota di funzioni R arbitrarie.
    
  
-   **Dove sono i dati e quali sono le caratteristiche?**  Se i dati si trovano in locale, è necessario decidere se caricare tutti i nuovi dati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o eseguire il training in locale e salvare solo il modello nel database. Tuttavia, quando si esegue la distribuzione alla produzione, potrebbe essere necessario eseguire il training da dati Enterprise e usare i processi ETL per pulire e caricare i dati.  
  
-   Domande simili a queste riguardano i dati di valutazione. Verrà creata la pipeline di dati per la valutazione dei dati nella workstation o si useranno origini dati aziendali? La pulizia e la preparazione dei dati devono essere eseguite come parte dei processi ETL o si sta effettuando un esperimento occasionale?  

    In questa esercitazione verrà descritto come spostare i dati in modo efficiente e sicuro dall'ambiente R locale a SQL Server e viceversa. 
  
-   **Quale contesto di calcolo verrà usato?** È possibile eseguire il training del modello in locale su dati campionati e quindi passare all'uso dei dati del server per il test e la produzione.

    In questa esercitazione verrà descritto come spostare i dati da SQL Server a R e viceversa usando R. Verrà inoltre illustrato come usare i dati con file XDF e come elaborarli in blocchi mediante le funzioni ScaleR.  
  
 
  
## Passaggio successivo  
[Lezione 1: Lavorare con i dati di SQL Server mediante R &#40;procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-1-work-with-sql-server-data-using-r-data-science-deep-dive.md)  
  
  
  
