---
title: "SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 38
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 36
---
# SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre una piattaforma per lo sviluppo e la distribuzione di applicazioni intelligenti che apre nuove prospettive. È possibile usare il linguaggio R, potente e ricco di funzionalità, e i numerosi pacchetti per creare modelli e generare stime tramite i dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] integra il linguaggio R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la soluzione consente di allineare analisi e dati ed eliminare i costi e i rischi di protezione associati allo spostamento dei dati.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta il linguaggio R open source e una serie completa di strumenti e tecnologie [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] che offrono prestazioni superiori, protezione, affidabilità e gestibilità. È possibile distribuire soluzioni R con strumenti familiari e intuitivi. Le applicazioni di produzione possono chiamare il runtime di R e recuperare le stime e gli elementi visivi usando [!INCLUDE[tsql](../../includes/tsql-md.md)]. È anche possibile ottenere le raccolte [ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) per migliorare la scalabilità e le prestazioni delle soluzioni R.  
  
Con l'installazione di SQL Server è possibile installare sia i componenti server che client.  
  
+   **R Services (In-Database):** installare questa funzionalità durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per garantire l'esecuzione sicura degli script di R nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Selezionando questa funzionalità, le estensioni vengono installate nel motore di database a supporto dell'esecuzione di script R. Viene anche creato il nuovo servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], che gestisce le comunicazioni tra il runtime di R e l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
+   **Microsoft R Server (Standalone):** distribuzione di R open source e di pacchetti proprietari che supportano l'elaborazione parallela e altri miglioramenti delle prestazioni. Servizi R (In-Database) e Microsoft R Server (Standalone) includono il runtime di base R e i pacchetti, oltre alle librerie **ScaleR** che migliorano la connettività e le prestazioni. 
  
+    [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/index#mrc) è disponibile come programma di installazione separato e gratuito.  È possibile usare Microsoft R Client per lo sviluppo di soluzioni che possono essere distribuite a Servizi R in esecuzione su SQL Server o a Microsoft R Server in esecuzione su Windows, Teradata o Hadoop. 
     

  > [!NOTE] Se è necessario eseguire il codice R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assicurarsi di installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] come descritto [qui](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).
  >  
  > Microsoft R Server \(Standalone\) è un'opzione separata progettata per usare le librerie ScaleR in un computer Windows che non esegue SQL Server. 
>   
>  Con Enterprise Edition, è tuttavia consigliabile installare Microsoft R Server \)Standalone[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un portatile o in un altro computer che viene usato per lo sviluppo R, in modo da creare soluzioni R che possono essere distribuite facilmente in un'istanza di \( che esegue Servizi R \(In-Database\).
  
## <a name="additional-resources"></a>Risorse aggiuntive  
  
 [Introduzione a Servizi R per SQL Server](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 Vengono descritti scenari comuni per utilizzi di R con SQL Server.  
  
[Configurare Servizi R per SQL Server (In-Database)](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
Vengono descritti l'installazione di R e i componenti di database associati come parte dell'installazione di SQL Server.  
  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
Informazioni su come creare origini dati di SQL Server nel codice R e come usare contesti di calcolo remoti. Altre esercitazioni destinate agli sviluppatori SQL illustrano come eseguire il training e distribuire un modello R in SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
  
 [Introduzione a Microsoft R Server &#40;Standalone&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
 
 [Creare un server R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md) 
  