---
title: Monitoraggio (replica) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d3e1b64c1c03a1e81fa83983427efbb60a399418
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810939"
---
# <a name="monitoring-replication"></a>Monitoraggio (replica)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il monitoraggio di una topologia di replica rappresenta un aspetto essenziale della distribuzione di una replica. Dato che l'attività di replica viene distribuita, è fondamentale monitorarne l'attività e lo stato su tutti i computer interessati. Per monitorare la replica è possibile utilizzare gli strumenti seguenti:  
  
-   Monitoraggio replica di[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]   
  
     Monitoraggio replica è lo strumento principale per il monitoraggio della replica, caratterizzato da una vista dell'intera attività di replica con priorità al server di pubblicazione. Per altre informazioni, vedere [Monitoring Replication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] consente di accedere a Monitoraggio replica. Consente inoltre di visualizzare lo stato attuale e l'ultimo messaggio registrato dall'agente di lettura log, dall'agente snapshot, dall'agente di merge e dall'agente di distribuzione, con la possibilità di avviare e arrestare ognuno di loro. Per altre informazioni, vedere [Monitor Replication Agents](../../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] e oggetti RMO (Replication Management Objects)  
  
     Entrambe le interfacce consentono di monitorare tutti i tipi di replica dal server di distribuzione. La replica di tipo merge consente inoltre di monitorare la replica dal Sottoscrittore.  
  
-   Avvisi per gli eventi degli agenti di replica  
  
     Durante la replica sono disponibili vari avvisi predefiniti per gli eventi degli agenti di replica. Se necessario, è inoltre possibile crearne di nuovi. Gli avvisi possono essere utilizzati per avviare una risposta automatica in seguito a un evento e/o per inviare notifiche all'amministratore. Per altre informazioni, vedere [Usare gli avvisi per gli eventi degli agenti di replica](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md).  
  
-   Monitor di sistema  
  
     Questa opzione può essere utile per monitorare le prestazioni della replica tramite vari contatori. Per altre informazioni, vedere [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione &#40;Replica&#41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Best Practices for Replication Administration](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
