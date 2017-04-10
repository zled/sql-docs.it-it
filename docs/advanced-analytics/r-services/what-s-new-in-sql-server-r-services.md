---
title: "Novit&#224; di SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: 36
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 35
---
# Novit&#224; di SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è una funzionalità di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e SQL Server vNext che supporta l'analisi scientifica dei dati su larga scala.  R è il linguaggio di programmazione più diffuso per l'analisi avanzata e offre un set incredibilmente ricco di pacchetti e una vivace community di sviluppatori in rapida evoluzione. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] consente di adottare in azienda il noto linguaggio R open source. 
  
 > [!TIP] SQL Server 2016 R Services già installato?
 > È ora possibile installare la versione più recente di Microsoft R Server nelle istanze 2016 per sfruttare i vantaggi degli aggiornamenti più frequenti per i componenti di R. Per altre informazioni, vedere [Microsoft R Server 9.0.1](https://msdn.microsoft.com/microsoft-r/rserver-whats-new).  

## <a name="whats-new-in-sql-server-vnext"></a>Novità di SQL Server vNext
  
+ Introduzione al pacchetto **MicrosoftML**

   MicrosoftML è un nuovo pacchetto di apprendimento automatico per R sviluppato dai team di Microsoft R Server e Microsoft Data Science. MicrosoftML offre maggiori livelli di velocità, prestazioni e scalabilità per gestire un ampio corpus di dati di testo e dati categoriali altamente dimensionali nei modelli R con solo poche righe di codice. Inoltre, i clienti di Microsoft R Server avranno accesso a cinque strumenti di apprendimento veloci e molto precisi che sono inclusi in Azure Machine Learning. 
   
   Per altre informazioni, vedere [Uso del pacchetto MicrosoftML con SQL Server R Services](../../advanced-analytics/r-services/using-the-microsoftml-package-with-sql-server-r-services.md).
   
+ Gestione dei pacchetti semplificata per data scientist

  Non è più necessario affidarsi all'amministratore di database per installare i pacchetti R necessari in SQL Server. Le nuove funzioni di installazione e disinstallazione dei pacchetti in **RevoScaleR** consentono di installare e aggiornare facilmente i pacchetti in R Services da un computer client. 
  
  Per l'amministratore del database, in [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] sono inclusi nuovi ruoli per la gestione delle autorizzazioni associate ai pacchetti, sia a livello di istanza sia a livello di database. 
  
  Per altre informazioni, vedere [Gestione dei pacchetti R per SQL Server R Services](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 
     
+ Nuove funzioni di **RevoScaleR** per gli oggetti del modello di lettura e scrittura R

  RevoScaleR include ora nuove funzioni di serializzazione e un formato di archiviazione dei modelli più compatto, per rendere veloci le attività di caricamento e lettura di un modello. 
  
  Per altre informazioni, vedere [Salvare e caricare oggetti R da SQL Server tramite ODBC](../../advanced-analytics/r-services/save-and-load-r-objects-from-sql-server-using-odbc.md). 

+ Pacchetto **sqlrutils** per l'integrazione SQL più semplice

  Questo pacchetto R consente di generare la chiamata a una stored procedure SQL per il codice R. Le stored procedure SQL generate possono quindi essere usate in SQL Server R Services. Sono disponibili esempi che consentono di consolidare il codice R in una funzione che può essere parametrizzata in una stored procedure SQL.
  
  Per altre informazioni, vedere [Generazione di una stored procedure R per il codice R tramite il pacchetto sqlrutils](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md). 
  

+ Pacchetto **olapR** per la connettività SSAS semplificata

   Questo nuovo pacchetto offre una nuova dimensione di connettività per R e SQL Server Analysis Services, rendendo più semplice l'uso dei dati OLAP per l'analisi in R. È possibile eseguire query MDX esistenti e ottenere un frame di dati R oppure creare istruzioni MDX semplici definendo filtri dei dati e assi di cubi nel codice R. 
   
   Per altre informazioni, vedere [Uso dei dati dai cubi OLAP in R](../../advanced-analytics/r-services/using-data-from-olap-cubes-in-r.md).
   

  
## <a name="features-in-sql-server-2016-r-services-and-sql-server-vnext"></a>Funzionalità di SQL Server 2016 R Services e SQL Server vNext  
  
- È disponibile il pacchetto **RevoScaleR** per l'apprendimento automatico veloce e parallelizzabile con R.

-   È incluso il supporto per gli account di accesso SQL e l'autenticazione integrata di Windows.  
    
-   Sono stati apportati miglioramenti significativi alle prestazioni, inclusi quelli di ottimizzazione dei processi di SQL Satellite, che consentono di connettere R e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il supporto per il paging dei dati per consentire l'utilizzo di grandi volumi di dati e lo streaming per abilitare l'elaborazione rapida di miliardi di righe. 
  
-   È possibile usare i pool di risorse di SQL Server per gestire la memoria usata dai processi R. Per altre informazioni, vedere [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md).  
  

### <a name="tools-and-setup"></a>Strumenti e programma di installazione

-   Installazione semplice di tutti i componenti. L'Installazione guidata di SQL Server consente di installare **SQL Server R Services (In-Database)** o **Microsoft R Server (Standalone)**.   Quando si esegue l'Installazione guidata, scegliere R Services, se si configura un'istanza di SQL Server, e R Server (Standalone) se si configura una workstation per l'analisi scientifica dei dati.   Per altre informazioni sulle opzioni di installazione, vedere [Configurare SQL Server R Services &#40;In-Database&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md) o [Creare un server R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md).  

-   Se non è necessario usare dati in SQL Server, valutare l'opportunità di usare [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)], che viene eseguito su una vasta gamma di piattaforme e offre prestazioni e scalabilità aziendale per il noto linguaggio R open source. [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)]. Per informazioni dettagliate, vedere [R Server &#40;Standalone&#41;](../../advanced-analytics/r-services/r-server-standalone.md) o [Introducing R Server](https://msdn.microsoft.com/microsoft-r/rserver) (Introduzione a R Server) su MSDN.

- Per aggiornare l'istanza di SQL Server 2016 per l'uso di Microsoft R Server 9.0.1, eseguire l'[utilità SqlBindR.exe](https://msdn.microsoft.com/library/mt791781.aspx).  

- [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-install) è un ambiente R gratuito che include tutti gli strumenti e le librerie necessari per creare soluzioni R da eseguire su R Services o R Server.  

-   R Tools for Visual Studio è un plug-in gratuito per Visual Studio in grado di offrire supporto avanzato per R, tra cui finestre di variabili e interattive standard per R, Intellisense per funzioni R, debug e markdown R, oltre alla funzionalità di esportazione in Word e HTML.  Per altre informazioni, vedere [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/).  

## <a name="learn-more"></a>Ulteriori informazioni
  
-  Sono disponibili risorse sia per data scientist, interessati a ottenere informazioni sull'integrazione di SQL Server, sia per sviluppatori SQL che vogliono creare soluzioni R usando T-SQL e l'ambiente familiare di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 
   + [Esercitazioni di SQL Server R Services](https://msdn.microsoft.com/library/mt591993.aspx)
   + [E-book gratuito: Data Science with SQL Server 2016](https://mva.microsoft.com/ebooks/) (Analisi scientifica dei dati con SQL Server 2016)
 
+ Se si desiderano soluzioni predefinite, i [modelli di Machine Learning](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/) del team di analisi scientifica dei dati di Microsoft illustrano soluzioni pratiche per attività di analisi comuni, tra cui la manutenzione predittiva e la prevenzione della perdita di clienti.
 

  
## <a name="see-also"></a>Vedere anche  
[Novità di SQL Server vNext](../../sql-server/what-s-new-in-sql-server-vnext.md)
  