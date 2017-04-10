---
title: "Scenari di analisi scientifica dei dati e modelli di soluzioni | Microsoft Docs"
ms.custom: ""
ms.date: "04/18/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 49e54fa9-9b28-44ba-b256-06dad4e8dece
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Scenari di analisi scientifica dei dati e modelli di soluzioni
I modelli sono soluzioni di esempio che illustrano le procedure consigliate e possono essere usati per implementare rapidamente una soluzione. Ogni modello è progettato per risolvere un problema specifico e include dati di esempio, codice R (Microsoft R Server) e stored procedure SQL. Le attività incluse in ogni modello vanno dalla preparazione dei dati alla progettazione della funzionalità fino al training e alla valutazione del modello. Il codice può essere eseguito in un IDE R con calcoli in SQL Server o mediante uno strumento client SQL quale SQL Server Management Studio.  
  
È possibile usare questi modelli per apprendere il funzionamento di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] e per compilare e distribuire una soluzione personalizzata, adattando il modello allo scenario operativo.  
  
Per istruzioni relative al download e alla configurazione, vedere [Come usare i modelli](#bkmk_HowTo) al termine del presente argomento.  
  
## Rilevamento di frodi  
[Modello per il rilevamento di frodi online (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)  
  
Un'attività importante per il business online è il rilevamento delle transazioni illecite e l'identificazione delle transazioni eseguite con strumenti o credenziali di pagamento rubate, per ridurre le perdite dovute a chargeback. Quando vengono rilevate transazioni illecite, le aziende in genere adottano misure per bloccare immediatamente determinati conti, al fine di evitare ulteriori perdite. In questo scenario verrà illustrato come usare dati di transazioni di acquisto online per identificare probabili frodi. Questa metodologia può essere applicata facilmente al rilevamento di frodi in altri domini.  
  
In questo modello verrà illustrato come usare dati di transazioni di acquisto online per identificare probabili frodi. Il rilevamento di frodi viene risolto come un problema di classificazione binaria. La metodologia usata in questo modello può essere facilmente applicata al rilevamento di frodi in altri domini.    
  
## Abbandono dei clienti  
[Modello per la previsione dell'abbandono dei clienti (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)  
  
L'analisi e la stima dell'abbandono dei clienti sono importanti per i settori in cui la perdita di clienti a favore di concorrenti va gestita e impedita per quanto possibile, ad esempio nei settori bancario, delle telecomunicazioni e della vendita al dettaglio. L'obiettivo dell'analisi dell'abbandono dei clienti è l'identificazione dei clienti con alta probabilità di abbandono e l'adozione di misure appropriate per mantenere tali clienti e la loro attività.  
  
Questo modello introduce la prevenzione dell'abbandono dei clienti formulando il problema come **classificazione binaria**. Mediante dati di esempio provenienti da due origini (dati demografici e transazioni dei clienti), il modello indica se la probabilità di abbandono dei singoli clienti è alta o bassa.   
  
## Manutenzione predittiva  
[Modello di manutenzione predittiva (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/Introduction.md)  
  
La manutenzione predittiva "basata sui dati" ha lo scopo di aumentare l'efficienza delle attività di manutenzione registrando i guasti precedenti e usando le informazioni per prevedere quando o dove un determinato dispositivo potrebbe far registrare un guasto. La possibilità di prevedere l'obsolescenza dei dispositivi è particolarmente importante per le applicazioni basate su dati distribuiti o sensori, ad esempio negli scenari IoT (Internet of Things).  
  
Questo modello è incentrato sulla risposta alla domanda "Quando si guasterà un dispositivo attualmente funzionante?" I dati di input rappresentano misurazioni simulate di sensori per motori di aerei. I dati ottenuti dal monitoraggio delle condizioni di funzionamento correnti del motore, quali ciclo di lavoro corrente, impostazioni, misurazioni dei sensori e così via vengono usati per creare tre tipi di modelli predittivi:  
  
-   **Modelli di regressione** per stimare quanto un motore può continuare a funzionare prima di bloccarsi. Il modello di esempio consente di stimare il valore di Vita utile residua (RUL, Remaining Useful Life), detta anche Tempo fra i guasti (TTF, Time To Failure).  
  
-   **Modelli di classificazione** per determinare la probabilità che un motore si guasti.  
  
    Il **modello di classificazione binario** prevede se un motore si guasterà entro un determinato periodo di tempo (numero di giorni).  
  
    Il **modello di classificazione a più classi** prevede se un determinato motore si guasterà e in tal caso indica un intervallo di tempo probabile nel quale si verificherà il guasto. Ad esempio, per un determinato giorno, è possibile prevedere se un dispositivo potrebbe guastarsi in tale giorno o in un determinato periodo di tempo successivo al giorno specificato.  
      
      
## Previsione della domanda elettrica  
[Modello per la previsione della domanda elettrica con SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast_Template_with_SQL-Server-R-Services-1)  
  
Questo modello illustra come usare SQL Server R Services per stimare la domanda di energia elettrica. La soluzione include un simulatore di domanda, tutto il codice R e T-SQL necessario per il training del modello e le stored procedure da usare per generare le previsioni e includerle in report.   
  
## <a name="bkmk_HowTo"></a>Utilizzo dei modelli  
Per scaricare i file inclusi in ogni modello è possibile usare i comandi di GitHub oppure aprire il collegamento e fare clic su **Download Zip** (Scarica zip) per salvare tutti i file nel computer.  Dopo che è stata scaricata, la soluzione contiene in genere le seguenti cartelle:  
  
-   **Data**: contiene i dati di esempio per ogni applicazione.  
  
-   **R**: contiene tutto il codice di sviluppo R necessario per la soluzione. La soluzione richiede le librerie di Microsoft R Server, ma può essere aperta e modificata in qualsiasi IDE R. Il codice R è stato ottimizzato con l'esecuzione dei calcoli all'interno del database, impostando il contesto di calcolo su un'istanza di SQL Server.  
  
-   **SQLR**: contiene più file con estensione sql eseguibili in un ambiente SQL quale [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per creare le stored procedure che eseguono attività correlate quali l'elaborazione dei dati, la progettazione delle funzionalità e la distribuzione del modello.  
  
    La cartella contiene anche uno script di PowerShell che consente di chiamare tutti gli script e di creare l'ambiente end-to-end.  
  
    Modificare lo script in base alle esigenze dell'ambiente di elaborazione.  
  
  
## Vedere anche  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
[Annuncio della disponibilità dei modelli in Azure ML](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)  
[Nuovo modello di manutenzione predittiva](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)  
  
  
  
