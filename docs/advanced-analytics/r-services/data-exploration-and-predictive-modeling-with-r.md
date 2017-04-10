---
title: "Esplorazione dei dati e modellazione predittiva con R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf6de7e2-f394-4b8a-a4b7-0b8dadf25426
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# Esplorazione dei dati e modellazione predittiva con R
  Gli esperti dei dati spesso usano R per esplorare i dati e compilare modelli predittivi. Si tratta in genere di un processo iterativo di prove ed errori fino a ottenere un modello predittivo soddisfacente. Gli esperti di dati possono connettersi al database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e recuperare i dati nella workstation locale usando il pacchetto RODBC, esplorare i dati e compilare un modello predittivo tramite pacchetti R standard.  
  
 Tuttavia, questo approccio presenta svantaggi. Lo spostamento dei dati può essere lento, inefficiente o non sicuro e lo stesso R presenta limitazioni in termini di scalabilità e prestazioni. Questi svantaggi diventano più evidenti quando si intende spostare e analizzare grandi quantità di dati o usare set di dati che non rientrano nella memoria disponibile sul computer.  
  
 È possibile ovviare a questi problemi mediante i nuovi pacchetti scalabili e le funzioni R incluse con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Il pacchetto **RevoScaleR** contiene le implementazioni di alcune delle funzioni R più diffuse, riprogettate per garantire parallelismo e scalabilità. Il pacchetto RevoScaleR fornisce anche supporto per la modifica del *contesto di esecuzione*. Ciò significa che, per un'intera soluzione o per una sola funzione, è possibile indicare che è necessario eseguire calcoli usando le risorse del computer che ospita l’istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , invece della workstation locale. Questa procedura offre numerosi vantaggi: evitare lo spostamento dei dati non necessari e usare risorse di calcolo più grandi nel computer del server.  
  
 Questa sezione fornisce indicazioni per gli esperti di dati sull'uso di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] e su come eseguire attività relative allo sviluppo e alla verifica delle soluzioni R.  
  
##  <a name="bkmk_RDevTools"></a> Strumenti di sviluppo di R  
 Microsoft R Client offre scienziato i dati di un ambiente completo per lo sviluppo e testing dei modelli predittivi. R Client include:  
  
-  **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** Una distribuzione del runtime di R e un set di pacchetti, ad esempio la libreria di kernel Intel matematica, migliorare le prestazioni delle operazioni standard di R.  
  
-   **RevoScaleR:** un pacchetto R che consente di inserire i calcoli a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)]. Include inoltre un set di funzioni R comuni che sono stati riprogettati per offrire scalabilità e prestazioni migliori. È possibile identificare queste funzioni migliorate dal prefisso **rx** . Include anche i provider di dati avanzati per un'ampia gamma di origini. Queste funzioni sono precedute da **Rx**.  
  
-   **Strumenti di sviluppo gratuiti:** è possibile utilizzare qualsiasi editor di codice basato su Windows che supporta R, ad esempio [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] o RStudio. Il download di [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] include anche strumenti da riga di comando comuni per R, ad esempio RGui.exe.  
  
##  <a name="bkmk_packages"></a> Ambiente e pacchetti R  
 L'ambiente R supportato in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è costituito da un runtime, dal linguaggio open source e da un motore grafico supportato ed esteso da più pacchetti. Il linguaggio consente di usare un'ampia gamma di estensioni implementate con i pacchetti.  
  
 Esistono varie fonti di pacchetti R aggiuntivi da usare con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] :  
  
  
-   Pacchetti di uso generale R dal repository pubblico. È possibile ottenere i pacchetti R open source più diffusi da repository pubblici, ad esempio CRAN, che ospita oltre 6000 pacchetti, usabili dagli esperti di dati.  
  
     Sono disponibili pacchetti aggiuntivi per supportare l'analisi predittiva in domini speciali, ad esempio finanza, genomica e così via.  
  
     Per la piattaforma Windows, pacchetti R vengono forniti come file zip e possono essere scaricati e installati con licenza GPL.  
  
     Per informazioni su come installare i pacchetti di terze parti per l'utilizzo con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vedere [installare altri pacchetti R in SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
-   Pacchetti aggiuntivi e le librerie fornite da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].   
  
     Il **RevoScaleR** pacchetto include analisi di big data ad alte prestazioni, versioni migliorate delle funzioni che supportano le attività di analisi scientifica dei dati comuni, gli strumenti di apprendimento ottimizzati per Naive Bayes, regressione lineare, i modelli time series e neural Network e librerie matematiche avanzate.  
  
     Il pacchetto **RevoPemaR** consente di sviluppare algoritmi paralleli di memoria esterna in R.  
  
     Per ulteriori informazioni su questi pacchetti e sul loro utilizzo, vedere [l'esplorazione dei dati e modellazione predittiva & #40; Esercitazione: Servizi SQL Server R & #41;](../../advanced-analytics/r-services/sql-server-r-services.md).  
  
## Uso delle origini dei dati e dei contesti di calcolo  
 Quando si utilizza il pacchetto RevoScaleR per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esistono alcune importanti nuove funzioni da utilizzare nel codice R:  
  
-   [RxSqlServerData](RxSqlServerData.md) è una funzione specificata nel pacchetto di integrazione applicativa dei dati migliorato per supportare RevoScaleR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Usare questa funzione nel codice R per definire l’ *origine dei dati*. L'oggetto di origine dei dati specifica il server e le tabelle in cui i dati si trovano e gestisce le attività di lettura dei dati e scrittura di dati su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Il [RxInSqlServer](rxInSqlServer.md) funzione può essere utilizzata per specificare il *calcolo contesto*.  In altre parole, è possibile indicare in cui deve essere eseguito il codice R: nella workstation locale o nel computer che ospita il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.  
  
     Quando si imposta il contesto di calcolo, influisce soltanto i calcoli che supportano l'esecuzione in contesti, ovvero le operazioni di R fornito dal pacchetto RevoScaleR e funzioni correlate. In genere, soluzioni R basate su pacchetti CRAN standard non possono eseguire in un contesto di elaborazione remota, anche se possono essere eseguiti [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer se avviato da T-SQL. Tuttavia, è possibile utilizzare il `rxExec` funzione per chiamare le singole funzioni R ed eseguirli in remoto [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  
  
 Per esempi di come creare e lavorare con origini dati e i contesti di esecuzione, vedere tre esercitazioni:
 
 + [Approfondimento di analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
 +  [Guida introduttiva al Server SQL RevoScaleR](https://msdn.microsoft.com/microsoft-r/rserver/rserver-scaler-sql-server-getting-started).  
  
## Distribuzione del codice R nell'ambiente di produzione  
 Una parte importante dell'analisi scientifica dei dati è la distribuzione dell'analisi ad altri utenti o l’uso di modelli predittivi per migliorare i risultati e i processi aziendali. In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è facile passare alla produzione quando lo script R o il modello è pronto.  
  
 Per ulteriori informazioni su come è possibile spostare il codice per l'esecuzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [operatività del codice R](../../advanced-analytics/r-services/operationalizing-your-r-code.md).  
  
 Il processo di distribuzione inizia in genere con pulizia dello script in uso al fine di eliminare il codice non necessario nell'ambiente di produzione. Quando si spostano calcoli vicino ai dati, si potrebbe trovare un modo per spostare in modo più efficiente, riepilogare o presentare i dati più operazioni vengono eseguite in R.  
  
 Si consiglia di consultare lo scienziato dati con uno sviluppatore di database sui modi per migliorare le prestazioni, soprattutto se la soluzione non pulizia dei dati o la funzionalità di progettazione che può essere più efficace in SQL. Le modifiche ai processi ETL potrebbero essere necessaria per garantire che i flussi di lavoro per la compilazione o un modello di punteggio non hanno esito negativo e che i dati di input sono disponibili in formato corretto.  
  
##  <a name="bkmk_SQLInR"></a> Argomenti della sezione  

[Confronto delle funzioni di ridimensionamento e R CRAN](Summary%20of%20rx%20Functions.md)

[Funzioni di ridimensionamento per l'utilizzo con SQL Server](../../advanced-analytics/r-services/scaler-functions-for-working-with-sql-server-data.md)
   
## Vedere anche  

 
 [Caratteristiche e attività di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)   
 
 [Operatività del codice R](../../advanced-analytics/r-services/operationalizing-your-r-code.md)  
  
  