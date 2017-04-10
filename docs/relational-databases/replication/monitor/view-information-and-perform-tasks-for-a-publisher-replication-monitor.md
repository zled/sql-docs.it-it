---
title: "Visualizzare le informazioni e eseguire attivit&#224; relative a un server di pubblicazione (Monitoraggio replica) | Microsoft Docs"
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
  - "server di pubblicazione [replica di SQL Server], attività Monitoraggio replica"
  - "visualizzazione di informazioni del server di pubblicazione"
  - "server di pubblicazione [replica di SQL Server], visualizzazione di informazioni"
ms.assetid: 1e777e95-377a-4de3-b965-867464aadaaf
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Visualizzare le informazioni e eseguire attivit&#224; relative a un server di pubblicazione (Monitoraggio replica)
  In Monitoraggio replica sono disponibili le schede seguenti in cui vengono visualizzate informazioni sul server di pubblicazione selezionato:  
  
-   **Pubblicazioni**  
  
     In questa scheda vengono visualizzate informazioni su tutte le pubblicazioni del server di pubblicazione selezionato.  
  
-   **Elenco verifica sottoscrizioni**  
  
     In questa scheda vengono visualizzate informazioni sulle sottoscrizioni di tutte le pubblicazioni disponibili sul server di pubblicazione selezionato che presentano errori, avvisi o un livello di prestazioni insufficiente. Questa scheda non viene visualizzata per i server di distribuzione che eseguono versioni precedenti a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   **Agenti** scheda  
  
     In questa scheda vengono visualizzate informazioni dettagliate su agenti e processi utilizzati da tutti i tipi di replica. La scheda consente anche di avviare e arrestare ciascun agente e processo.  
  
 Per visualizzare ulteriori informazioni sulle opzioni di ogni scheda, fare clic sulla scheda nel riquadro di destra e quindi fare clic su **Guida** nella barra dei menu. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Per visualizzare informazioni ed eseguire attività relative a un server di pubblicazione  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro e quindi fare clic su un server di pubblicazione.  
  
2.  Per visualizzare informazioni su tutte le pubblicazioni, fare clic su di **pubblicazioni** scheda.  
  
3.  Per visualizzare informazioni sulle sottoscrizioni, scegliere il **elenco verifica sottoscrizioni** scheda. In questa scheda, è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività.  
  
    -   Per visualizzare informazioni dettagliate sull'agente di cui è associata a una sottoscrizione, fare doppio clic su sottoscrizione e quindi fare clic su **Visualizza dettagli**.  
  
    -   Per visualizzare le proprietà di una sottoscrizione, fare doppio clic su sottoscrizione e quindi fare clic su **proprietà**.  
  
    -   Per sincronizzare una sottoscrizione push, fare doppio clic su sottoscrizione e quindi fare clic su **Avvia sincronizzazione**.  
  
    -   Per reinizializzare una sottoscrizione, fare doppio clic su sottoscrizione e quindi fare clic su **Reinizializza sottoscrizione**.  
  
4.  Per visualizzare le informazioni sugli agenti, fare clic su di **agenti** scheda. In questa scheda è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività:  
  
    -   Per visualizzare informazioni dettagliate su un agente (ad esempio i messaggi informativi ed eventuali messaggi di errore), fare doppio clic sull'agente e quindi fare clic su **Visualizza dettagli**.  
  
    -   Per visualizzare informazioni dettagliate sul processo che esegue l'agente (ad esempio la pianificazione, i dettagli di passaggio di processo e così via), fare doppio clic sull'agente e quindi fare clic su **proprietà**.  
  
    -   Per gestire i profili per l'agente, fare doppio clic sull'agente e quindi fare clic su **profilo agente**. Per ulteriori informazioni, vedere [utilizzare profili agenti di replica](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Per avviare un agente che non è in esecuzione, fare doppio clic sull'agente e quindi fare clic su **Avvia agente**.  
  
    -   Per arrestare un agente che è in esecuzione, fare doppio clic sull'agente e quindi fare clic su **Arresta agente**.  
  
## Vedere anche  
 [View and Modify Distributor and Publisher Properties](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  