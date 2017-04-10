---
title: "Monitoraggio della replica | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "monitoraggio delle prestazioni [replica di SQL Server], Monitoraggio replica"
  - "Monitoraggio replica, informazioni"
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Monitoraggio della replica
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Monitoraggio replica è uno strumento grafico che consente di monitorare l'integrità generale di una topologia di replica. Tale strumento offre informazioni dettagliate sullo stato e sulle prestazioni di pubblicazioni e sottoscrizioni, consentendo all'utente di rispondere a domande comuni quali:  
  
-   Il sistema di replica funziona correttamente?  
  
-   Quali sottoscrizioni sono lente?  
  
-   Con quale ritardo viene eseguita la sottoscrizione transazionale?  
  
-   In quanto tempo una transazione di cui è stato appena eseguito il commit raggiungerà un Sottoscrittore nella replica transazionale?  
  
-   Per quale motivo la sottoscrizione di tipo merge è lenta?  
  
-   Perché l'agente non è in esecuzione?  
  
 Per monitorare la replica, un utente deve essere un membro del **sysadmin** al server di distribuzione o un membro del ruolo predefinito del server di **replmonitor** ruolo predefinito del database nel database di distribuzione. Un amministratore di sistema può aggiungere qualsiasi utente per il **replmonitor** ruolo, che consente all'utente di visualizzare l'attività di replica in Monitoraggio replica, tuttavia, l'utente non è possibile amministrare la replica.  
  
## Argomenti della sezione  
 Negli argomenti seguenti sono incluse informazioni sulle funzionalità di Monitoraggio replica.  
  
 [Panoramica dell'interfaccia di Monitoraggio replica](../../../relational-databases/replication/monitor/overview-of-the-replication-monitor-interface.md)  
 Vengono descritte tutte le finestre e le schede di Monitoraggio replica e sono incluse informazioni su come rispondere alle domande elencate in precedenza.  
  
 [Avvio di Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)  
 Viene descritto come avviare Monitoraggio replica.  
  
 [Allow Non-Administrators to Use Replication Monitor](../../../relational-databases/replication/monitor/allow-non-administrators-to-use-replication-monitor.md)  
 Viene descritto come assegnare autorizzazioni agli utenti non amministratore in modo che possano utilizzare Monitoraggio replica.  
  
 [Aggiunta e rimozione di server di pubblicazione da Monitoraggio replica](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md)  
 Viene descritto come aggiungere o rimuovere server di pubblicazione da Monitoraggio replica.  
  
 [Aggiornamento dei dati in Monitoraggio replica](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md)  
 Viene descritto come aggiornare i dati in Monitoraggio replica.  
  
 [Monitoraggio delle prestazioni con Monitoraggio replica](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
 Descrive come monitorare le prestazioni in Monitoraggio replica, incluse le informazioni sull'impostazione delle soglie di prestazione. Include informazioni sulle statistiche a livello di articolo per la replica di merge per ottenere una vista dettagliata dell'elaborazione.  
  
 [Measure Latency and Validate Connections for Transactional Replication](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
 Descrive i token di traccia che consentono di misurare le prestazioni di una topologia di replica transazionale.  
  
 [Monitoraggio degli agenti di replica](../../../relational-databases/replication/monitor/monitor-replication-agents.md)  
 Descrive come reperire informazioni su ogni agente di replica.  
  
 [Impostazione di valore soglia e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
 Descrive gli avvisi e le soglie che è possibile impostare in Monitoraggio replica. È consigliabile abilitare gli avvisi per la topologia, in modo da poter essere informati tempestivamente sullo stato e sulle prestazioni.  
  
 [Memorizzazione nella cache, aggiornamento e prestazioni di Monitoraggio replica](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)  
 Descrive il modo in cui Monitoraggio replica memorizza dati e calcoli nella cache per migliorare le prestazioni e illustra la relazione tra l'aggiornamento dell'interfaccia utente e quello della cache.  
  
 [Visualizzazione dello stato delle pubblicazioni e delle sottoscrizioni in Monitoraggio replica](../../../relational-databases/replication/monitor/view-publication-and-subscription-status-in-replication-monitor.md)  
 Viene descritto come visualizzare informazioni sullo stato di una Pubblicazione o Sottoscrizione tramite Monitoraggio replica.  
  
 [Consente di visualizzare informazioni ed eseguire attività per un server di pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per un server di pubblicazione tramite Monitoraggio replica  
  
 [Consente di visualizzare informazioni ed eseguire attività per una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per una pubblicazione tramite Monitoraggio replica  
  
 [Consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per gli agenti associati a una pubblicazione tramite Monitoraggio replica.  
  
 [Consente di visualizzare informazioni ed eseguire attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per una Sottoscrizione tramite Monitoraggio replica  
  
 [Consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per gli agenti associati a una Sottoscrizione tramite Monitoraggio replica.  
  
  