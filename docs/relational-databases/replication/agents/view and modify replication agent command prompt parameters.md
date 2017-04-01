---
title: "Visualizzare e modificare i parametri del prompt dei comandi dell&#39;agente di replica (SQL Server Management Studio) | Microsoft Docs"
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
  - "agenti [replica di SQL Server], parametri del prompt dei comandi"
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Visualizzare e modificare i parametri del prompt dei comandi dell&#39;agente di replica (SQL Server Management Studio)
  Gli agenti di replica sono file eseguibili che accettano parametri della riga di comando. Per impostazione predefinita, gli agenti vengono eseguiti in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] passaggi di processo dell'agente, in modo che questi parametri possono essere visualizzati e modificate tramite il **proprietà processo - \< processo>** la finestra di dialogo. Questa finestra di dialogo è disponibile il **processi** cartella [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e dal **agenti** scheda in Monitoraggio replica. Per informazioni sull'avvio di monitoraggio replica, vedere [avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
> [!NOTE]  
>  Le modifiche apportate al parametro dell'agente verranno applicate al successivo avvio dell'agente. Se l'agente viene eseguito in modo continuo, è necessario arrestarlo e riavviarlo.  
  
 Sebbene i parametri possano essere modificati direttamente, in genere li si modifica tramite un profilo agente. Per altre informazioni, vedere [Replication Agent Profiles](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 Se si accede ai processi di agente dal **processi** cartella, utilizzare la tabella seguente per determinare il nome del processo dell'agente e i parametri disponibili per ogni agente.  
  
|Agente|Nome processo|Per l'elenco dei parametri, vedere...|  
|-----------|--------------|------------------------------------|  
|agente snapshot|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< numero intero>**|[Agente snapshot repliche](../../../relational-databases/replication/agents/replication-snapshot-agent.md)|  
|Agente snapshot per una partizione di una pubblicazione di tipo merge|**Dyn_ \< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< GUID>**|[Agente snapshot repliche](../../../relational-databases/replication/agents/replication-snapshot-agent.md)|  
|Agente di lettura log|**\< server di pubblicazione>-\< PublicationDatabase>-\< numero intero>**|[Agente lettura log repliche](../../../relational-databases/replication/agents/replication-log-reader-agent.md)|  
|Agente di merge per le sottoscrizioni pull|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< SubscriptionDatabase>-\< numero intero>**|[Agente merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md)|  
|Agente di merge per le sottoscrizioni push|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>**|[Agente merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md)|  
|Agente di distribuzione per le sottoscrizioni push|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>***|[Agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Agente di distribuzione per le sottoscrizioni pull|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< SubscriptionDatabase>-\< GUID>***\*|[Agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Agente di distribuzione per le sottoscrizioni push di Sottoscrittori non SQL Server|**\< server di pubblicazione>-\< PublicationDatabase>-\< pubblicazione>-\< sottoscrittore>-\< numero intero>**|[Agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|Agente di lettura coda|**[\< distributor>]. \< numero intero>**|[Agente di lettura coda repliche](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)|  
  
 \*Per le sottoscrizioni push a pubblicazioni Oracle è **\< server di pubblicazione>-\< Publisher**> anziché **\< server di pubblicazione>-\< PublicationDatabase>**  
  
 \*\*Per le sottoscrizioni pull a pubblicazioni Oracle, è **\< server di pubblicazione>-\< DistributionDatabase**> anziché **\< server di pubblicazione>-\< PublicationDatabase>**  
  
### Per visualizzare e modificare i parametri della riga di comando dell'agente di replica in Management Studio  
  
1.  Connettersi al computer appropriato in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] e quindi espandere il nodo del server:  
  
    -   Per l'agente di distribuzione e l'agente di merge per le sottoscrizioni pull, connettersi al Sottoscrittore.  
  
    -   Per tutti gli altri agenti, connettersi al server di distribuzione.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Fare doppio clic su un processo e quindi fare clic su **proprietà**.  
  
4.  Nel **passaggi** pagina della **proprietà processo - \< processo>** finestra di dialogo, selezionare il passaggio **eseguire agente**, e quindi fare clic su **modificare**.  
  
5.  Nel **proprietà passaggio processo - esecuzione agente** nella finestra di dialogo Modifica il **comando** campo.  
  
6.  Fare clic su **OK** in entrambe le finestre di dialogo.  
  
### Per visualizzare e modificare i parametri della riga di comando dell'agente di distribuzione e dell'agente di merge in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro a sinistra di Monitoraggio replica, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic sulla scheda **Tutte le sottoscrizioni** .  
  
3.  Fare doppio clic su una sottoscrizione e quindi fare clic su **Visualizza dettagli**.  
  
4.  Nel **sottoscrizione \< SubscriptionName >** finestra, fare clic su **azione**, quindi fare clic su **\< AgentName> proprietà processo**.  
  
5.  Nel **passaggi** pagina della **proprietà processo - \< processo>** finestra di dialogo, selezionare il passaggio **eseguire agente**, e quindi fare clic su **modificare**.  
  
6.  Nel **proprietà passaggio processo - esecuzione agente** nella finestra di dialogo Modifica il **comando** campo.  
  
7.  Fare clic su **OK** in entrambe le finestre di dialogo.  
  
### Per visualizzare e modificare i parametri della riga di comando dell'agente snapshot, dell'agente di lettura log e dell'agente di lettura coda in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro a sinistra di Monitoraggio replica, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic su di **agenti** scheda.  
  
3.  Fare doppio clic su un agente nella griglia e quindi fare clic su **proprietà**.  
  
4.  Nel **passaggi** pagina della **proprietà processo - \< processo>** finestra di dialogo, selezionare il passaggio **eseguire agente**, e quindi fare clic su **modificare**.  
  
5.  Nel **proprietà passaggio processo - esecuzione agente** nella finestra di dialogo Modifica il **comando** campo.  
  
6.  Fare clic su **OK** in entrambe le finestre di dialogo.  
  
## Vedere anche  
 [Amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Concetti di base relativi ai file eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Panoramica degli agenti di replica](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  