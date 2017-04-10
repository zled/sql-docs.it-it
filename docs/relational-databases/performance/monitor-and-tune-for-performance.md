---
title: "Monitoraggio e ottimizzazione delle prestazioni | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/18/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "istanze di SQL Server, monitoraggio delle prestazioni"
  - "monitoraggio delle prestazioni del server [SQL Server]"
  - "motore di database [SQL Server], prestazioni"
  - "monitoraggio delle prestazioni [SQL Server], informazioni sulle prestazioni"
  - "prestazioni server [SQL Server]"
  - "monitoraggio delle prestazioni [SQL Server]"
  - "prestazioni del database [SQL Server], informazioni sulle prestazioni"
  - "ottimizzazione di database [SQL Server], informazioni sulle prestazioni"
  - "informazioni sullo stato [SQL Server], monitoraggio delle prestazioni"
  - "monitoraggio di database [SQL Server], informazioni sulle prestazioni"
  - "monitoraggio [SQL Server], prestazioni delle query"
  - "prestazioni del server [SQL Server], informazioni sulle prestazioni"
  - "ottimizzazione di database [SQL Server]"
  - "prestazioni di database [SQL Server]"
  - "monitoraggio [SQL Server], prestazioni del server"
  - "monitoraggio di database [SQL Server]"
  - "monitoraggio delle prestazioni del server [SQL Server], informazioni sul monitoraggio delle prestazioni del server"
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
caps.latest.revision: 35
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# Monitoraggio e ottimizzazione delle prestazioni
  L'obiettivo del monitoraggio dei database consiste nella valutazione delle prestazioni di un server. Un monitoraggio efficace implica l'esecuzione di snapshot periodici delle prestazioni correnti al fine di isolare i processi che causano problemi, nonché la raccolta continua di dati nel tempo per tenere traccia delle tendenze delle prestazioni.  
  
 La valutazione continuativa delle prestazioni del database consente di ridurre al minimo i tempi di risposta e di aumentare al massimo la velocità effettiva, ottimizzando pertanto le prestazioni. Traffico di rete, operazioni di I/O su disco e utilizzo della CPU efficienti sono fattori fondamentali per ottenere prestazioni ottimali. È necessario analizzare accuratamente i requisiti delle applicazioni, comprendere la struttura logica e fisica dei dati, valutare l'utilizzo del database e raggiungere compromessi adeguati tra tipi di utilizzo in conflitto, ad esempio elaborazione delle transazioni online (OLTP) e supporto decisionale.  
  
## Monitoraggio e ottimizzazione del database per le prestazioni  
 In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e nel sistema operativo Microsoft Windows sono disponibili utilità che consentono di visualizzare la condizione corrente del database e di tenere traccia delle prestazioni in caso di variazioni. È disponibile una vasta gamma di strumenti e di tecniche per il monitoraggio di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il monitoraggio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di eseguire queste operazioni:  
  
-   Determinare se è possibile migliorare le prestazioni. Il monitoraggio dei tempi di risposta delle query più frequenti consente, ad esempio, di determinare se sono necessarie modifiche alle query o agli indici nelle tabelle.  
  
-   Valutare le attività degli utenti. Il monitoraggio dei tentativi di connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente ad esempio di determinare se il sistema di sicurezza è adeguatamente impostato e di testare applicazioni e sistemi di sviluppo. Il monitoraggio dell'esecuzione di query SQL consente ad esempio di determinare se le query sono formulate in modo corretto e se producono i risultati previsti.  
  
-   Risolvere problemi o eseguire il debug dei componenti di applicazione, ad esempio di stored procedure.  
  
## Monitoraggio in un ambiente dinamico  
I cambiamenti delle condizioni comportano variazioni nelle prestazioni. Nel corso delle valutazioni, è possibile analizzare le variazioni delle prestazioni in relazione ad aumento del numero di utenti, modifica dei metodi di connessione e accesso degli utenti, aumento dei contenuti del database, cambiamento nelle applicazioni client, variazione dei dati nelle applicazioni, aumento della complessità delle query e incremento del traffico di rete. L'uso di strumenti per il monitoraggio delle prestazioni consente di associare alcune variazioni nelle prestazioni con cambiamenti nelle condizioni e complessità delle query. **Esempi:**:  
  
-   Il monitoraggio dei tempi di risposta delle query più frequenti consente di determinare se sono necessarie modifiche alle query o agli indici nelle tabelle in cui le query vengono eseguite.  
  
-   Il monitoraggio dell'esecuzione di query [!INCLUDE[tsql](../../includes/tsql-md.md)] consente di determinare se le query sono formulate in modo corretto e se producono i risultati previsti.  
  
-   Il monitoraggio dei tentativi di connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di determinare se il sistema di sicurezza è adeguato e di verificare il funzionamento di applicazioni o sistemi di sviluppo.  
  
 I tempi di risposta corrispondono al tempo necessario per la restituzione all'utente della prima riga del set di risultati come conferma visiva dell'elaborazione di una query. La velocità effettiva corrisponde al numero totale di query gestite dal server in un determinato periodo di tempo.  
  
 Con l'aumentare del numero di utenti, aumenta la concorrenza per le risorse del server, che a sua volta comporta un incremento dei tempi di risposta e una diminuzione generale della velocità effettiva.  
  
## Attività di monitoraggio e ottimizzazione delle prestazioni  
  
|Argomento| Attività|  
|-----------|----------------------|  
|[Monitorare i componenti di SQL Server](../../relational-databases/performance/monitor-sql-server-components.md)|Passaggi necessari per monitorare qualsiasi componente di SQL Server.|  
|[Strumenti per il monitoraggio e l'ottimizzazione delle prestazioni](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)|Elenca gli strumenti di monitoraggio e ottimizzazione disponibili con SQL Server.|  
|[Definire una base di riferimento delle prestazioni](../../relational-databases/performance/establish-a-performance-baseline.md)|Come definire una baseline delle prestazioni.|  
|[Isolare i problemi relativi alle prestazioni](../../relational-databases/performance/isolate-performance-problems.md)|Isolare problemi di prestazioni del database.|  
|[Individuare i colli di bottiglia](../../relational-databases/performance/identify-bottlenecks.md)|Monitorare e tenere traccia delle prestazioni del server per identificare colli di bottiglia.|  
|[Monitoraggio delle prestazioni e dell'attività del server](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|Usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e gli strumenti di monitoraggio delle prestazioni e delle attività di Windows.|  
|[Visualizzare e salvare piani di esecuzione](../../relational-databases/performance/display-and-save-execution-plans.md)|Visualizzare e salvare piani di esecuzione in un file in formato XML.|  
|[Statistiche sulle query dinamiche](../../relational-databases/performance/live-query-statistics.md)|Visualizzare statistiche in tempo reale relative ai passaggi per l'esecuzione di query.|  
|[Monitoraggio delle prestazioni con Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)|Usare l'archivio query per acquisire automaticamente una cronologia di query, piani e statistiche di runtime e conservarle per la consultazione.|  
|[Uso di Archivio query con OLTP in-memoria](../../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md)|Considerazioni sulle tabelle con ottimizzazione per la memoria.|  
|[Procedure consigliate per l'archivio query](../../relational-databases/performance/best-practice-with-the-query-store.md)|Consigli sull'uso dell'archivio query.|  
  
## Vedere anche  
 [Amministrazione automatizzata in un'organizzazione](../../ssms/agent/automated-administration-across-an-enterprise.md)   
 [Ottimizzazione guidata motore di database](../../relational-databases/performance/database-engine-tuning-advisor.md)   
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  