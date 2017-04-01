---
title: "Operativit&#224; del codice R | Microsoft Docs"
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
ms.assetid: f15696b1-2479-4e5f-ac5e-4beaf958a043
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Operativit&#224; del codice R
  Gli sviluppatori di database si occupano di integrare più tecnologie e raggruppare i risultati in modo che possano essere condivisi in tutta l'organizzazione. Lo sviluppatore di database collabora con sviluppatori di applicazioni, sviluppatori di SQL ed esperti di dati per progettare soluzioni, metodi di gestione dei dati consigliati, per architettare e distribuire le soluzioni. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre numerosi vantaggi per gli sviluppatori che lavorano con gli scienziati dati.  
  
-   **Interagire con gli script R utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)].** Applicazione e gli sviluppatori di database, nonché gli analisti che creano report, è possono richiamare uno script R effettuando una chiamata da una stored procedure di sistema.  
  
     Per ulteriori informazioni sulla sintassi di base, vedere [sp_execute_external_script & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) e [usando il codice R in T-SQL](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md).  
 
    Per un esempio dettagliato di come rendere operativi R codice tramite le stored procedure, vedere [nel Database di analisi per gli sviluppatori SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md).
  
     Integrazione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anche significa che è possibile eseguire R script utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)] e incorporare i risultati in un'applicazione. Ad esempio, è possibile creare un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report che viene eseguito una R script e quindi visualizzarla i tracciati insieme le stime nel report.  
  
-   **Prestazioni e scalabilità:** Sebbene il linguaggio R open source è noto per le limitazioni, il pacchetto RevoScaleR API fornite da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] può operare su grandi set di dati e trarre vantaggio da più thread, multi-core, multiprocesso calcoli nel database.  
  
     Se la soluzione R usa aggregazioni complesse o comporta grandi set di dati, è possibile sfruttare le efficienti aggregazioni in memoria e gli indici columnstore di SQL e lasciare che il codice R gestisca i calcoli statistici e l'assegnazione dei punteggi.  
  
-   **Strumenti di sviluppo e gestione standard:** non sono necessari strumenti di amministrazione o distribuzione aggiuntivi; tutti i processi R possono essere chiamati con una stored procedure.  
  
     In aggiunta, lo stesso codice R che viene eseguito sui dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere riusato su altre origini dati, ad esempio Hadoop.  
  
 In questa sezione vengono descritti i concetti è necessario comprendere per convertire le soluzioni R e distribuirli in produzione utilizzando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
## Argomenti della sezione

[Uso dei tipi di dati di R](../../advanced-analytics/r-services/working-with-r-data-types.md)

[Conversione di codice R per l'utilizzo nei servizi di R](../../advanced-analytics/r-services/converting-r-code-for-use-in-r-services.md)

##  <a name="bkmk_RelatedTasks"></a> Attività correlate  
  
[Ottimizzazione delle prestazioni per SQL Server R servizi](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
## Vedere anche  
 [Caratteristiche e attività di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)   
 [sp_execute_external_script & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  
  