---
title: "Differenze nelle funzionalit&#224; R tra le edizioni di SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Differenze nelle funzionalit&#224; R tra le edizioni di SQL Server
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è disponibile nelle edizioni seguenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
-   **Enterprise Edition**  
    
     Include entrambi i servizi R, per l'analisi nel database in SQL Server 2016, nonché R Server (autonomo) in Windows, che può essere utilizzato per connettersi a un'ampia gamma di database e di estrarre i dati per l'analisi a livello di scalabilità, ma che non viene eseguita nel database. Include inoltre **DeployR**, che può essere utilizzato per distribuire script R e i modelli come servizio Web.  

     Nessuna restrizione. Ottimizzare le prestazioni e scalabilità tramite la parallelizzazione e streaming. Analisi di Suopprts di grandi set di dati che non rientrano nella memoria disponibile, utilizzando il **ridimensionamento** funzioni.  
  
     Analisi dei dati nel database in SQL Server supporta la governance delle risorse di script esterni per personalizzare l'utilizzo delle risorse di server.  
  
-   **Developer Edition**  

    Stesse funzionalità di Enterprise Edition. Tuttavia, Developer Edition non può essere utilizzato in ambienti di produzione.  

  
  
-   **Standard Edition**  
  
     Tutte le funzionalità di analisi dei dati nel database incluso in Enterprise Edition, ad eccezione di governance delle risorse flessibile. Prestazioni e scalabilità è limitato: i dati che possono essere elaborati deve essere inserita nella memoria del server e l'elaborazione è limitato a un thread singolo calcolo, anche quando si utilizza il **ridimensionamento** funzioni.
  
-   **Edizioni Express**  
  
     Solo Express Edition with Advanced Services fornisce servizi di R. Le limitazioni delle prestazioni sono simili agli Standard Edition.  
  
 Per ulteriori informazioni sulle altre caratteristiche del prodotto, vedere [funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  

> [!NOTE]
>
> + Microsoft R Open è incluso in tutte le edizioni.
> + Microsoft R Client è possibile lavorare con tutte le edizioni.
  
## Enterprise Edition  
 Prestazioni delle soluzioni di R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere in genere migliore rispetto a qualsiasi implementazione di R convenzionale, dato lo stesso hardware, poiché R possono essere eseguite utilizzando le risorse del server e talvolta distribuite a più processi mediante il **ridimensionamento** funzioni.  
  
 Gli utenti possono inoltre dovrebbero essere presenti differenze notevoli prestazioni e scalabilità per le stesse funzioni R Se eseguito in Visual Studio Enterprise Edition. Standard Edition. Motivi includono il supporto per l'elaborazione parallela, streaming e maggiore thread disponibili per l'elaborazione di lavoro di R.  
  
 Tuttavia, le prestazioni anche nello stesso hardware possono dipendere da diversi fattori all'esterno del codice R, tra cui sulle richieste di risorse server, il tipo di piano di query che viene creato, le modifiche dello schema, la necessità di aggiornare le statistiche o creare un nuovo piano di query, la frammentazione e altro ancora. È possibile che una stored procedure contenenti codice R potrebbero essere eseguiti in secondi sotto un carico di lavoro, ma richiedere minuti quando sono presenti altri servizi in esecuzione.  È pertanto consigliabile monitorare vari aspetti di prestazioni del server, tra cui la rete per contesti di elaborazione remota, quando la quantificazione delle prestazioni di processo R.  

È inoltre consigliabile configurare [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (disponibile in Enterprise Edition) per personalizzare la modalità che i processi R sono classificati o manipolati in carichi di lavoro elevato sul server. È possibile definire funzioni di classificazione per specificare l'origine del processo di R e definire le priorità di alcuni carichi di lavoro, limitare la quantità di memoria utilizzata da query SQL e controllare il numero di processi paralleli consente l'utilizzo del carico di lavoro.  
  
## Developer Edition  
 Developer Edition offre prestazioni equivalenti a quelle di Enterprise Edition. utilizzo di Developer Edition, tuttavia, non è supportato per gli ambienti di produzione.  
  
  
## Standard Edition  
 Anche Standard Edition deve offrire alcuni vantaggi nelle prestazioni, a differenza dei pacchetti R standard, ha la stessa configurazione hardware.  
  
 Tuttavia, Standard Edition non supporta Resource Governor. L'utilizzo di governance delle risorse è il modo migliore per personalizzare le risorse server per supportare diversi carichi di lavoro R come modello di training e assegnazione dei punteggi.  
  
 Standard Edition fornisce inoltre limitava le prestazioni e scalabilità rispetto a Enterprise Edition e Developer Edition. In particolare, tutte le **ridimensionamento** funzioni e i pacchetti sono inclusi con l'edizione Standard, ma è limitato il numero di processi è possibile utilizzare il servizio che avvia e gestisce gli script R. Inoltre, i dati elaborati dallo script devono adattarsi in memoria.  
  
  
## Express Edition with Advanced Services  
 Express Edition è soggetto alle stesse limitazioni di Standard Edition.  
  
## Vedere anche  
 [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
  
  