---
title: "Avviare e arrestare un agente di replica (SQL Server Management Studio) | Microsoft Docs"
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
  - "agenti [replica di SQL Server], arresto"
  - "agenti [replica di SQL Server], avvio"
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Avviare e arrestare un agente di replica (SQL Server Management Studio)
  Avviare e arrestare gli agenti dal **processi** cartella e il **replica** cartella [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e da Monitoraggio replica. Avviare e arrestare gli agenti e i processi seguenti:  
  
-   Agente snapshot, utilizzato da tutte le pubblicazioni.  
  
-   Agente di lettura log, utilizzato da tutte le pubblicazioni transazionali.  
  
-   Agente di lettura coda, utilizzato dalle pubblicazioni transazionali abilitate per le sottoscrizioni ad aggiornamento in coda.  
  
-   Agente di distribuzione, che consente di sincronizzare le sottoscrizioni con le pubblicazioni transazionali e snapshot.  
  
-   Agente di merge, che consente di sincronizzare le sottoscrizioni con le pubblicazioni di tipo merge.  
  
-   Processi di manutenzione della replica.  
  
 Per ulteriori informazioni sull'avvio dell'agente di Merge e l'agente di distribuzione, vedere [sincronizzare una sottoscrizione Push](../../../relational-databases/replication/synchronize-a-push-subscription.md) e [sincronizzare una sottoscrizione Pull](../../../relational-databases/replication/synchronize-a-pull-subscription.md). Per ulteriori informazioni sui processi di manutenzione, vedere [eseguire processi di manutenzione della replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md).  
  
 Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Per avviare e arrestare un agente snapshot o un agente di lettura log da Management Studio  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], quindi espandere il nodo del server e il **replica** cartella.  
  
2.  Espandere il **pubblicazioni locali** cartella e quindi fare di una pubblicazione.  
  
3.  Fare clic su **Visualizza stato agente Snapshot** o **Visualizza stato agente di lettura Log**.  
  
4.  Fare clic su **avviare** o **arrestare**.  
  
### Per avviare e arrestare un agente di lettura coda da Management Studio  
  
1.  Connettersi al server di distribuzione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Il pulsante destro del processo per l'agente e quindi fare clic su **Avvia processo** o **Arresta processo**. Il nome del processo per l'agente di lettura coda è nel formato **[\< Distributor>]. \< integer>**.  
  
### Per avviare e arrestare un agente snapshot, un agente di lettura log o un agente di lettura coda da Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic su di **agenti** scheda.  
  
3.  Fare doppio clic su un agente e quindi fare clic su **Avvia agente** o **Arresta agente**.  
  
## Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Concetti di base relativi ai file eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Panoramica degli agenti di replica](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  