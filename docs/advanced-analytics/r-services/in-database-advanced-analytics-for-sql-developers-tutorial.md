---
title: "Analisi avanzata nel database per sviluppatori SQL (esercitazione) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
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
  - "TSQL"
ms.assetid: c18cb249-2146-41b7-8821-3a20c5d7a690
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Analisi avanzata nel database per sviluppatori SQL (esercitazione)
L'obiettivo di questa procedura dettagliata è offrire ai programmatori SQL un'esperienza pratica diretta su come creare una soluzione di analisi avanzata con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. In questa procedura dettagliata verrà illustrato come incorporare R in un'applicazione o una soluzione di business intelligence eseguendo il wrapping di codice R nelle stored procedure.  
  
## Panoramica  
Il processo di creazione di una soluzione end-to-end normalmente consiste in attività di acquisizione e pulizia dei dati, esplorazione dei dati e progettazione di funzionalità, training e ottimizzazione del modello e infine distribuzione del modello nell'ambiente di produzione. Per lo sviluppo e i test del codice R effettivo è opportuno usare un ambiente di sviluppo progettato per R, ad esempio RStudio o [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]. Dopo la creazione della soluzione, tuttavia è possibile distribuirla facilmente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
Pertanto, in questa procedura dettagliata, si presuppone che l'utente abbia a disposizione tutto il codice R necessario per la soluzione e ci si concentrerà sulla compilazione e la distribuzione di una soluzione di analisi avanzata che è già stata codificata in R.  
  
-   [Passaggio 1: Scaricare i dati di esempio](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md).    Scaricare il set di dati di esempio e i file di script SQL di esempio in un computer locale.  
  
-   [Passaggio 2: Importare i dati in SQL Server usando PowerShell](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md).  Eseguire uno script di PowerShell che crea un database e una tabella nell'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e carica i dati di esempio nella tabella.  
  
-   [Passaggio 3: Esplorare e visualizzare i dati](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md).   Eseguire l'esplorazione e la visualizzazione di base dei dati, chiamando pacchetti e funzioni R dalle stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   [Passaggio 4: Creare funzionalità di dati mediante T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md).  Creare nuove funzionalità di dati usando funzioni personalizzate di SQL.  
  
-   [Passaggio 5: Training e salvataggio di un modello usando T-SQL](../../advanced-analytics/r-services/step-5-train-and-save-a-model-using-t-sql.md).  Creare e salvare il modello di machine learning usando le stored procedure.  
  
-   [Passaggio 6: Rendere operativo il modello](../../advanced-analytics/r-services/step-6-operationalize-the-model-in-database-advanced-analytics-tutorial.md).  Dopo aver salvato il modello per il database, chiamare il modello per la stima da [!INCLUDE[tsql](../../includes/tsql-md.md)] usando le stored procedure.  
  
> [!NOTE]  
> Si consiglia di non usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per scrivere o testare il codice R. Se vengono rilevati problemi nel codice R incorporato in una stored procedure, le informazioni restituite dalla stored procedure non sono in genere sufficienti per capire la causa dell'errore.   
>   
> Per il debug, si consiglia di usare uno strumento come RStudio o [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]. Gli script R contenuti in questa esercitazione sono già stati sviluppati e sottoposti a debug usando gli strumenti tradizionali di R.  
>   
> Per sapere come si sviluppano gli script R che si possono eseguire in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vedere l'esercitazione [Procedura dettagliata end-to-end per l'analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md))  
  
### Scenario  
Questa procedura dettagliata usa il noto set di dati NYC Taxi. Questo set di dati pubblico contiene 20 GB di file CSV compressi (circa 48 GB non compressi), che descrivono i dettagli di oltre 173 milioni di singole corse dei taxi nel 2013, nonché le tariffe pagate per ogni corsa. Per rendere questa procedura dettagliata facile e rapida, è stato creato un campione rappresentativo dei dati: % 1 dei dati oppure 1.703.957 righe e 23 colonne. In questa procedura i dati verranno usati per compilare un modello di classificazione binaria che consente di stimare se per una determinata corsa è probabile o meno che venga lasciata una mancia, in base a colonne come ora del giorno, distanza e luogo dove inizia il servizio.  
  
  
### Requisiti  
Questa procedura dettagliata è destinata agli utenti che hanno già familiarità con le operazioni fondamentali dei database, ad esempio la creazione di tabelle e database, l'importazione dei dati in tabelle e la creazione di query SQL. È disponibile tutto il codice R, quindi non è richiesto un ambiente di sviluppo di R. Un programmatore SQL esperto deve essere in grado di completare questa procedura dettagliata usando [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o eseguendo gli script di PowerShell disponibili.  
  
Tuttavia, prima di avviare la procedura dettagliata, è necessario completare queste operazioni di preparazione:  
  
-   Connettersi a un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] con SQL Server R Services abilitato (richiede CTP 3 o versione successiva). Per informazioni dettagliate, vedere le istruzioni di installazione: [Configurare SQL Server R Services (In-Database)](https://msdn.microsoft.com/library/mt696069.aspx)  
  
 -   L'account di accesso usato per questa procedura deve avere le autorizzazioni necessarie per creare database e altri oggetti, per caricare i dati, selezionare i dati ed eseguire le stored procedure.  
  
## Passaggio successivo  
[Passaggio 1: Scaricare i dati di esempio](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md)  
  
## Vedere anche  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
[SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  
  
