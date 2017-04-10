---
title: "Visualizzare le informazioni ed eseguire attivit&#224; per una pubblicazione (Monitoraggio replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualizzazione di informazioni di pubblicazioni"
  - "pubblicazioni [replica di SQL Server], visualizzazione di informazioni"
  - "pubblicazioni [replica di SQL Server], attività Monitoraggio replica"
ms.assetid: 92e28a07-d6a7-461b-a0b3-bd9bc6afcbe5
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Visualizzare le informazioni ed eseguire attivit&#224; per una pubblicazione (Monitoraggio replica)
  In Monitoraggio replica sono disponibili le schede seguenti che includono le informazioni sulla pubblicazione selezionata:  
  
-   **Tutte le sottoscrizioni**  
  
     In questa scheda vengono visualizzate informazioni su tutte le sottoscrizioni della pubblicazione selezionata.  
  
-   **Agenti**  
  
     In questa scheda vengono visualizzate informazioni su tutti gli agenti utilizzati da una pubblicazione:  
  
    -   Agente snapshot, utilizzato da tutte le pubblicazioni.  
  
    -   Agente di lettura log, utilizzato da tutte le pubblicazioni transazionali.  
  
    -   Agente di lettura coda, utilizzato dalle pubblicazioni transazionali contenenti sottoscrizioni ad aggiornamento in coda.  
  
-   **Avvisi** (per i server di distribuzione in esecuzione [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive)  
  
    -   Questa scheda consente di specificare avvisi per gli agenti.  
  
-   **Token di traccia** (replica transazionale, solo per i server di distribuzione in esecuzione [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive)  
  
     Questa scheda consente di misurare la latenza, ovvero l'intervallo di tempo che intercorre tra il commit di una transazione nel server di pubblicazione e il commit della transazione corrispondente nel Sottoscrittore.  
  
 Per ulteriori informazioni sulle opzioni di ogni scheda, fare clic sulla scheda nel riquadro di destra e quindi fare clic su **Guida** nella barra dei menu. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Per visualizzare le informazioni ed eseguire le attività per una pubblicazione  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Per visualizzare e modificare le proprietà di pubblicazione, fare doppio clic su pubblicazione e quindi fare clic su **proprietà**.  
  
3.  Per visualizzare informazioni sulle sottoscrizioni, fare clic su di **tutte le sottoscrizioni** scheda.  
  
     Per visualizzare e modificare le proprietà della sottoscrizione, fare doppio clic su sottoscrizione e quindi fare clic su **proprietà**. In questa scheda è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività. Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
4.  Per visualizzare le informazioni sugli agenti, fare clic su di **agenti** scheda. In questa scheda è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività. Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
5.  Per visualizzare informazioni sulle soglie e avvisi di agente, fare clic sui **avvisi** scheda. Per ulteriori informazioni, vedere [impostare soglie e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
6.  Per visualizzare informazioni sui token di traccia, fare clic su di **i token di traccia** scheda. Per ulteriori informazioni su come utilizzare i token di traccia, vedere [misurazione latenza e convalidare le connessioni per la replica transazionale](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
## Vedere anche  
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  