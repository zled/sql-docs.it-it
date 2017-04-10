---
title: "Creazione di flussi di lavoro che usano R in SQL Server | Microsoft Docs"
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
ms.assetid: 34c3b1c2-97db-4cea-b287-c7f4fe4ecc1b
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Creazione di flussi di lavoro che usano R in SQL Server
  Un database relazionale è una tecnologia altamente ottimizzata per la fornitura di soluzioni scalabili di elaborazione, archiviazione e l'esecuzione di query dei dati delle transazioni. Tuttavia, sempre soluzioni R sono in genere basata sull'importazione di dati da diverse origini, spesso in formato CSV, per eseguire ulteriori esplorazione dei dati e modellazione. Si tratta di procedure non solo poco efficienti, ma anche non sicure.  
  
 Utilizzando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre più vantaggi:  
  
-   Protezione dei dati. La potenza di R verrà inserita nel database, verso l'origine dei dati. Consente di evitare lo spostamento di dati eccessiva o non protetto.  
  
-   Velocità. I database sono ottimizzati per operazioni basate su set. Inoltre, innovazioni recenti nel database come tabelle in memoria e archiviazione dei dati a colonne ulteriori migliorare le analisi scientifica dei dati apportando aggregazioni fulmine fast.  
  
-   Integrazione. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è il punto centrale di operazioni per molte altre attività di gestione dati e applicazioni che utilizzano enterprise. Utilizzando i dati già nel database garantisce che i dati siano compatibili e aggiornate. Invece di elaborare i dati in R, è possibile utilizzare le pipeline di dati aziendali tra cui [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e Data Factory di Azure. Reporting dei risultati o analisi è facile tramite Power BI o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Con la giusta combinazione di SQL e R per le diverse attività di elaborazione e analisi di dati, sia i data scientist che gli sviluppatori possono essere più produttivi. Questa sezione descrive come integrare R con altre soluzioni aziendali per la trasformazione dei dati, l'analisi e la creazione di report.  
  
##  <a name="bkmk_ssis"></a> Creare flussi di lavoro efficienti con R e il database  
 I flussi di lavoro per l'analisi scientifica dei dati sono altamente iterativi e implicano molte trasformazioni dei dati, tra cui ridimensionamento, aggregazioni, calcolo delle probabilità, ridenominazione e unione degli attributi. Data Scientist sono abituati a eseguire molte di queste attività in R, Python o un'altra lingua. Tuttavia, l'esecuzione di tali flussi di lavoro sui dati aziendali richiede una perfetta integrazione con strumenti ETL e i processi.  
  
 Poiché [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] consente di eseguire operazioni complesse in R tramite Transact-SQL e stored procedure, è possibile integrare attività specifiche di R con i processi ETL esistenti senza operazioni di sviluppo minime. Invece di eseguire una catena di attività di memoria ntensive in R, la preparazione dei dati può essere ottimizzata mediante gli strumenti più efficienti, tra cui [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Ad esempio, è possibile combinare con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in scenari come i:  
  
-   Utilizzare [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] attività per creare gli oggetti necessari nel database SQL  
  
-   Usare la diramazione condizionale per cambiare il contesto di calcolo per i processi R  
  
-   Eseguire processi R che generano dati propri  
  
-   Utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per chiamare uno script R salvato in una variabile di testo  
  
### Esempi e risorse  
 [Rendere operativo il progetto di formazione machine utilizzando SQL Server 2016 SSIS e servizi R](https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/)  
  
 In questo post di blog, si apprenderà come:  
  
-   Usare R nell'attività Esegui SQL per generare i dati e salvare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Utilizzare una stored procedure per eseguire il training di un modello R e archiviarle nel database  
  
-   Eseguire l'assegnazione dei punteggi sul modello utilizzando l'attività Script e l'attività Esegui SQL  
  
##  <a name="bkmk_ssrs"></a> Creare visualizzazioni con R e strumenti per la creazione di report aziendali  
 Anche se R consente di creare grafici e visualizzazioni interessanti, non è ben integrato con le origini dati esterne e questo significa che ogni grafico deve essere prodotto singolarmente. Condivisione inoltre può essere difficile.  
  
 Utilizzando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è possibile eseguire operazioni complesse in R tramite [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, che possono essere facilmente utilizzate da un'ampia gamma di strumenti, tra cui creazione di report aziendali [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e Power BI.  
  
-   Visualizzare gli oggetti graphics restituiti da uno script R   
    utilizzo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   Utilizzare la tabella in Power BI  
  
## Esempi e risorse  
 [Dispositivo di grafica R per Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/)  
  
 Questo progetto CodePlex fornisce il codice per la creazione di un elemento del report personalizzato che esegue il rendering di output grafico di R come un'immagine che può essere utilizzata in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.  Utilizzando l'elemento del report personalizzato, è possibile:  
  
-   Pubblicare grafici e i tracciati creati con il dispositivo di grafica R per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Dashboard  
  
-   Passare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] parametri grafici R  
  
> [!NOTE]  
>  Si noti che il codice che supporta il dispositivo di grafica R per Reporting Services deve essere installato nel server di Reporting Services, nonché in Visual Studio. Configurazione e la compilazione manuale è obbligatorio.  
  
  