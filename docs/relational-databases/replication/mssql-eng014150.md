---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 222ab67a59cad879dde9b6c823170ffed10a5338
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng014150"></a>MSSQL_ENG014150
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14150|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Replica-%s: l'esecuzione dell'agente %s è riuscita. %s|  
  
## <a name="explanation"></a>Spiegazione  
 Il messaggio indica che l'esecuzione di un agente di replica è stata completata correttamente. Nella replica vengono utilizzati gli agenti seguenti:  
  
-   Agente snapshot. Questo agente viene utilizzato da tutte le pubblicazioni.  
  
-   Agente di lettura log. Questo agente viene utilizzato da tutte le pubblicazioni transazionali.  
  
-   Agente di lettura coda. Questo agente viene utilizzato dalle pubblicazioni transazionali abilitate per le sottoscrizioni ad aggiornamento in coda.  
  
-   Agente di distribuzione. Questo agente consente di sincronizzare le sottoscrizioni con le pubblicazioni transazionali e snapshot.  
  
-   Agente di merge. Questo agente consente di sincronizzare le sottoscrizioni con le pubblicazioni di tipo merge.  
  
-   Processi di manutenzione della replica.  
  
## <a name="user-action"></a>Azione dell'utente  
 L'agente di lettura log, l'agente di lettura coda e l'agente di distribuzione vengono in genere eseguiti in modo continuo, mentre altri agenti vengono eseguiti su richiesta o in base a una pianificazione. Se il completamento dell'esecuzione di un agente non è previsto, verificare lo stato dell'agente. Per altre informazioni, vedere [Monitor Replication Agents](../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione dell'agente di replica](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agente distribuzione repliche](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agente lettura log repliche](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agente merge repliche](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agente di lettura coda repliche](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
