---
title: "Visualizzare le informazioni ed eseguire attivit&#224; relative agli agenti associati a una pubblicazione (Monitoraggio replica) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agenti [replica di SQL Server], visualizzazione di informazioni"
  - "visualizzazione di informazioni sugli agenti di replica"
  - "agenti [replica di SQL Server], attività in Monitoraggio replica"
ms.assetid: 2a420da2-66f4-4650-9bdd-1992221ed3fd
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Visualizzare le informazioni ed eseguire attivit&#224; relative agli agenti associati a una pubblicazione (Monitoraggio replica)
  Monitoraggio replica consente di **agenti** scheda, che include informazioni sugli agenti associati alla pubblicazione selezionata. L'agente di distribuzione e l'agente di Merge sono associati alle sottoscrizioni; Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
 In questa scheda vengono visualizzate informazioni relative agli agenti seguenti:  
  
-   Agente snapshot, utilizzato da tutte le pubblicazioni.  
  
-   Agente di lettura log, utilizzato da tutte le pubblicazioni transazionali.  
  
-   Agente di lettura coda, utilizzato dalle pubblicazioni transazionali abilitate per le sottoscrizioni ad aggiornamento in coda.  
  
 Per visualizzare altre informazioni relative alle opzioni della scheda, fare clic su **?** sulla barra dei menu. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Per visualizzare informazioni ed eseguire attività relative agli agenti associati a una pubblicazione  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic su di **agenti** scheda per visualizzare le informazioni sugli agenti. In questa scheda è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività:  
  
    -   Per visualizzare informazioni dettagliate su un agente (ad esempio i messaggi informativi ed eventuali messaggi di errore), fare doppio clic sull'agente e quindi fare clic su **Visualizza dettagli**.  
  
    -   Per visualizzare informazioni dettagliate sul processo che esegue l'agente (ad esempio la pianificazione, i dettagli di passaggio di processo e così via), fare doppio clic sull'agente e quindi fare clic su **proprietà**.  
  
    -   Per gestire i profili per l'agente, fare doppio clic sull'agente e quindi fare clic su **profilo agente**. Per ulteriori informazioni, vedere [utilizzare profili agenti di replica](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Per avviare un agente che non è in esecuzione, fare doppio clic sull'agente e quindi fare clic su **Avvia agente**.  
  
    -   Per arrestare un agente che è in esecuzione, fare doppio clic sull'agente e quindi fare clic su **Arresta agente**.  
  
## Vedere anche  
 [Impostazione di valore soglia e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività per una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  