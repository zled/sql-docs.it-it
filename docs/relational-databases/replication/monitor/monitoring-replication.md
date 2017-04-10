---
title: "Monitoraggio (replica) | Microsoft Docs"
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
  - "monitoraggio delle prestazioni [replica di SQL Server], informazioni sul monitoraggio della replica"
  - "replica transazionale, monitoraggio"
  - "monitoraggio [replica di SQL Server]"
  - "monitoraggio della replica di tipo merge [replica di SQL Server]"
  - "replica snapshot [SQL Server], monitoraggio"
  - "replica [SQL Server], monitoraggio"
  - "amministrazione della replica, monitoraggio"
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Monitoraggio (replica)
  Il monitoraggio di una topologia di replica rappresenta un aspetto essenziale della distribuzione di una replica. Dato che l'attività di replica viene distribuita, è fondamentale monitorarne l'attività e lo stato su tutti i computer interessati. Per monitorare la replica è possibile utilizzare gli strumenti seguenti:  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Monitoraggio replica  
  
     Monitoraggio replica è lo strumento principale per il monitoraggio della replica, caratterizzato da una vista dell'intera attività di replica con priorità al server di pubblicazione. Per altre informazioni, vedere [Monitoring Replication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] fornisce l'accesso a Monitoraggio replica. Consente inoltre di visualizzare lo stato attuale e l'ultimo messaggio registrato dall'agente di lettura log, dall'agente snapshot, dall'agente di merge e dall'agente di distribuzione, con la possibilità di avviare e arrestare ognuno di loro. Per ulteriori informazioni, vedere [gli agenti di monitoraggio replica](../../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] e Replication Management Objects (RMO)  
  
     Entrambe le interfacce consentono di monitorare tutti i tipi di replica dal server di distribuzione. La replica di tipo merge consente inoltre di monitorare la replica dal Sottoscrittore.  
  
-   Avvisi per gli eventi degli agenti di replica  
  
     Durante la replica sono disponibili vari avvisi predefiniti per gli eventi degli agenti di replica. Se necessario, è inoltre possibile crearne di nuovi. Gli avvisi possono essere utilizzati per avviare una risposta automatica in seguito a un evento e/o per inviare notifiche all'amministratore. Per ulteriori informazioni, vedere [utilizzare avvisi per gli eventi dell'agente di replica](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md).  
  
-   Monitor di sistema  
  
     Questa opzione può essere utile per monitorare le prestazioni della replica tramite vari contatori. Per ulteriori informazioni, vedere [monitoraggio della replica con Monitor di sistema](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md).  
  
## Vedere anche  
 [Amministrazione & #40; Replica & #41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Procedure consigliate per l'amministrazione della replica](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  