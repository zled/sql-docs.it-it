---
title: Monitorare gli agenti di replica | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring performance [SQL Server replication], agents
- Log Reader Agent, monitoring
- Replication Monitor, agents
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- agents [SQL Server replication], monitoring
- Distribution Agent, monitoring
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 837bb9a07b2c6ed60bf36d7c2842a346005b07b9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="monitor-replication-agents"></a>Monitoraggio degli agenti di replica
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Monitoraggio replica di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] offre una visualizzazione a livello di sistema dell'attività di replica e semplifica l'individuazione di informazioni su un agente specifico. Nell'elenco seguente vengono inclusi tutti gli agenti, le relative schede di Monitoraggio replica e un collegamento all'argomento in cui si spiega come accedere a queste schede:  
  
-   Gli agenti seguenti sono associati alle pubblicazioni in Monitoraggio replica:  
  
    -   agente snapshot  
  
    -   Agente di lettura log  
  
    -   Agente di lettura coda  
  
     Per accedere alle informazioni e alle attività associate a questi agenti utilizzare la scheda **Agenti** , disponibile per ogni server di pubblicazione e pubblicazione, e la scheda **Avvisi** , disponibile per ogni pubblicazione. Per altre informazioni, vedere [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una pubblicazione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
-   Gli agenti seguenti sono associati alle sottoscrizioni in Monitoraggio replica:  
  
    -   Agente di distribuzione  
  
    -   Agente di merge  
  
     Per accedere alle informazioni e alle attività associate a questi agenti utilizzare le schede di pubblicazione seguenti: **Elenco verifica sottoscrizioni** (disponibile per tutti i server di pubblicazione) o **Tutte le sottoscrizioni** (disponibile per tutte le pubblicazioni). Per altre informazioni, vedere [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
## <a name="using-sql-server-management-studio-to-monitor-replication-agents"></a>Utilizzo di SQL Server Management Studio per il monitoraggio degli agenti di replica  
 In[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] sono disponibili le finestre di dialogo seguenti per il monitoraggio degli agenti di replica:  
  
-   **Visualizza stato agente snapshot** (per tutte le pubblicazioni)  
  
-   **Visualizza stato agente di lettura log** (per tutte le pubblicazioni transazionali)  
  
-   **Visualizza stato sincronizzazione** (per tutte le sottoscrizioni: questa finestra di dialogo consente l'accesso all'agente di distribuzione e all'agente di merge)  
  
 Monitoraggio replica offre informazioni aggiuntive su ogni agente e consente di monitorare l'agente di lettura coda, se utilizzato. Per altre informazioni, vedere [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una pubblicazione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md), [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una pubblicazione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md) e [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione &#40;Monitoraggio replica&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
#### <a name="to-monitor-the-snapshot-agent-and-log-reader-agent"></a>Per monitorare l'agente snapshot e l'agente di lettura log  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Fare clic con il pulsante destro del mouse su una pubblicazione e quindi scegliere **Visualizza stato agente di lettura log** o **Visualizza stato agente snapshot**.  
  
4.  Nella finestra di dialogo **Visualizza stato agente di lettura log** o **Visualizza stato agente snapshot** :  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Fare clic su **Esegui monitoraggio** per avviare **Monitoraggio replica**.  
  
5.  Scegliere **Chiudi**.  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-publisher"></a>Per monitorare l'agente di distribuzione e l'agente di merge (dal server di pubblicazione)  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione della sottoscrizione da monitorare.  
  
4.  Fare clic con il pulsante destro del mouse sulla sottoscrizione e quindi scegliere **Visualizza stato sincronizzazione**.  
  
5.  Nella finestra di dialogo **Visualizza stato sincronizzazione** :  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Per le sottoscrizioni push fare clic su **Esegui monitoraggio** per avviare **Monitoraggio replica**.  
  
    -   Per le sottoscrizioni pull fare clic su **Visualizza cronologia processi** per avviare **Visualizzatore file log**e visualizzare l'output del log dell'agente.  
  
6.  Scegliere **Chiudi**.  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-subscriber"></a>Per monitorare l'agente di distribuzione e l'agente di merge (dal Sottoscrittore)  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Fare clic con il pulsante destro del mouse sulla sottoscrizione che si desidera monitorare e quindi scegliere **Visualizza stato sincronizzazione**.  
  
4.  Nella finestra di dialogo **Visualizza stato sincronizzazione** :  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Fare clic su **Visualizza cronologia processi** per avviare **Visualizzatore file log**e visualizzare l'output del log dell'agente.  
  
5.  Scegliere **Chiudi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Replication Agents Overview](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
