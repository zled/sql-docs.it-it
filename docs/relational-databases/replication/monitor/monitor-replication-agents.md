---
title: "Monitoraggio degli agenti di replica | Microsoft Docs"
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
  - "monitoraggio delle prestazioni [replica di SQL Server], agenti"
  - "agente di lettura log, monitoraggio"
  - "Monitoraggio replica, agenti"
  - "agente di merge, monitoraggio"
  - "agente di lettura coda, monitoraggio"
  - "agente snapshot, monitoraggio"
  - "agenti [replica di SQL Server], monitoraggio"
  - "agente di distribuzione, monitoraggio"
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Monitoraggio degli agenti di replica
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Monitoraggio replica offre una vista sistemica dell'attività di replica, ma rende semplice trovare informazioni su un agente specifico. Nell'elenco seguente vengono inclusi tutti gli agenti, le relative schede di Monitoraggio replica e un collegamento all'argomento in cui si spiega come accedere a queste schede:  
  
-   Gli agenti seguenti sono associati alle pubblicazioni in Monitoraggio replica:  
  
    -   agente snapshot  
  
    -   Agente di lettura log  
  
    -   Agente di lettura coda  
  
     Accedere alle informazioni e attività associate a questi agenti utilizzare le schede seguenti: **agenti** (disponibile per ogni server di pubblicazione e pubblicazione) e **avvisi** (disponibile per ogni pubblicazione). Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
-   Gli agenti seguenti sono associati alle sottoscrizioni in Monitoraggio replica:  
  
    -   Agente di distribuzione  
  
    -   Agente di merge  
  
     Accedere alle informazioni e attività associate a questi agenti utilizzare le schede seguenti: **elenco verifica sottoscrizioni** (disponibile per ogni server di pubblicazione) o **tutte le sottoscrizioni** (disponibile per ogni pubblicazione). Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Utilizzo di SQL Server Management Studio per il monitoraggio degli agenti di replica  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] fornisce le seguenti finestre di dialogo per il monitoraggio degli agenti di replica:  
  
-   **Visualizza stato agente Snapshot** (per tutte le pubblicazioni)  
  
-   **Visualizza stato agente di lettura Log** (per tutte le pubblicazioni transazionali)  
  
-   **Visualizzare lo stato di sincronizzazione** (per tutte le sottoscrizioni; questa finestra di dialogo consente l'accesso per l'agente di distribuzione e l'agente di Merge)  
  
 Monitoraggio replica offre informazioni aggiuntive su ogni agente e consente di monitorare l'agente di lettura coda, se utilizzato. Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md), [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una pubblicazione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md), e [consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
#### Per monitorare l'agente snapshot e l'agente di lettura log  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Fare doppio clic su una pubblicazione e quindi fare clic su **Visualizza stato agente di lettura Log** o **Visualizza stato agente Snapshot**.  
  
4.  Nel **Visualizza stato agente di lettura Log** o **Visualizza stato agente Snapshot** la finestra di dialogo:  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Fare clic su **monitoraggio** per avviare **Monitoraggio replica**.  
  
5.  Scegliere **Chiudi**.  
  
#### Per monitorare l'agente di distribuzione e l'agente di merge (dal server di pubblicazione)  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione della sottoscrizione da monitorare.  
  
4.  Fare doppio clic su sottoscrizione e quindi fare clic su **Visualizza stato sincronizzazione**.  
  
5.  Nel **Visualizza stato sincronizzazione** la finestra di dialogo:  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Per le sottoscrizioni push, fare clic su **monitoraggio** per avviare **Monitoraggio replica**.  
  
    -   Per le sottoscrizioni pull, fare clic su **Visualizza cronologia processi** per avviare il **Visualizzatore File di Log**, visualizzare l'output del log dell'agente.  
  
6.  Scegliere **Chiudi**.  
  
#### Per monitorare l'agente di distribuzione e l'agente di merge (dal Sottoscrittore)  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Fare doppio clic su sottoscrizione si desidera monitorare e quindi fare clic su **Visualizza stato sincronizzazione**.  
  
4.  Nel **Visualizza stato sincronizzazione** la finestra di dialogo:  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Fare clic su **Visualizza cronologia processi** per avviare il **Visualizzatore File di Log**, visualizzare l'output del log dell'agente.  
  
5.  Scegliere **Chiudi**.  
  
## Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Panoramica degli agenti di replica](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  