---
title: Monitoraggio della replica | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2dc65ac3d6356ff9c2a69d0a30a8c5a1ecc76782
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="monitoring-replication-overview"></a>Panoramica del monitoraggio della replica
  Monitoraggio replica di[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è uno strumento grafico che consente di monitorare lo stato generale di una topologia di replica. Tale strumento offre informazioni dettagliate sullo stato e sulle prestazioni di pubblicazioni e sottoscrizioni, consentendo all'utente di rispondere a domande comuni quali:  
  
-   Il sistema di replica funziona correttamente?  
  
-   Quali sottoscrizioni sono lente?  
  
-   Con quale ritardo viene eseguita la sottoscrizione transazionale?  
  
-   In quanto tempo una transazione di cui è stato appena eseguito il commit raggiungerà un Sottoscrittore nella replica transazionale?  
  
-   Per quale motivo la sottoscrizione di tipo merge è lenta?  
  
-   Perché l'agente non è in esecuzione?  
  
 Per monitorare la replica, è necessario che un utente sia un membro del ruolo predefinito del server **sysadmin** nel server di distribuzione o un membro del ruolo predefinito del database **replmonitor** nel database di distribuzione. Un amministratore di sistema può aggiungere qualsiasi utente al ruolo **replmonitor** , consentendo a tale utente di visualizzare l'attività di replica in Monitoraggio replica, ma non di amministrare la replica.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Negli argomenti seguenti sono incluse informazioni sulle funzionalità di Monitoraggio replica.  
  
 [Panoramica dell'interfaccia di Monitoraggio replica](../../../relational-databases/replication/monitor/overview-of-the-replication-monitor-interface.md)  
 Vengono descritte tutte le finestre e le schede di Monitoraggio replica e sono incluse informazioni su come rispondere alle domande elencate in precedenza.  
  
 [Avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)  
 Viene descritto come avviare Monitoraggio replica.  
  
 [Consentire a utenti non amministratori di usare Monitoraggio replica](../../../relational-databases/replication/monitor/allow-non-administrators-to-use-replication-monitor.md)  
 Viene descritto come assegnare autorizzazioni agli utenti non amministratore in modo che possano utilizzare Monitoraggio replica.  
  
 [Aggiungere e rimuovere server di pubblicazione da Monitoraggio replica](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md)  
 Viene descritto come aggiungere o rimuovere server di pubblicazione da Monitoraggio replica.  
  
 [Aggiornare i dati in Monitoraggio replica](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md)  
 Viene descritto come aggiornare i dati in Monitoraggio replica.  
  
 [Monitorare le prestazioni con Monitoraggio replica](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
 Descrive come monitorare le prestazioni in Monitoraggio replica, incluse le informazioni sull'impostazione delle soglie di prestazione. Include informazioni sulle statistiche a livello di articolo per la replica di merge per ottenere una vista dettagliata dell'elaborazione.  
  
 [Misurare la latenza e convalidare le connessioni per la replica transazionale](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
 Descrive i token di traccia che consentono di misurare le prestazioni di una topologia di replica transazionale.  
  
 [Monitorare gli agenti di replica](../../../relational-databases/replication/monitor/monitor-replication-agents.md)  
 Descrive come reperire informazioni su ogni agente di replica.  
  
 [Impostare valori di soglia e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
 Descrive gli avvisi e le soglie che è possibile impostare in Monitoraggio replica. È consigliabile abilitare gli avvisi per la topologia, in modo da poter essere informati tempestivamente sullo stato e sulle prestazioni.  
  
 [Memorizzazione nella cache, aggiornamento e prestazioni di Monitoraggio replica](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)  
 Descrive il modo in cui Monitoraggio replica memorizza dati e calcoli nella cache per migliorare le prestazioni e illustra la relazione tra l'aggiornamento dell'interfaccia utente e quello della cache.  
  
 [Visualizzare lo stato delle pubblicazioni e delle sottoscrizioni in Monitoraggio replica](../../../relational-databases/replication/monitor/view-publication-and-subscription-status-in-replication-monitor.md)  
 Viene descritto come visualizzare informazioni sullo stato di una Pubblicazione o Sottoscrizione tramite Monitoraggio replica.  
  
 [Visualizzare le informazioni ed eseguire attività relative a un server di pubblicazione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per un server di pubblicazione tramite Monitoraggio replica  
  
 [Visualizzare le informazioni ed eseguire attività per una pubblicazione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per una pubblicazione tramite Monitoraggio replica  
  
 [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una pubblicazione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per gli agenti associati a una pubblicazione tramite Monitoraggio replica.  
  
 [Visualizzare le informazioni ed eseguire attività relative a una sottoscrizione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per una Sottoscrizione tramite Monitoraggio replica  
  
 [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)  
 Viene descritto come visualizzare le informazioni e come eseguire le attività per gli agenti associati a una Sottoscrizione tramite Monitoraggio replica.  
  
  

