---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07fcbe83f92a523eea000a9a63b4a72a991228fd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233051"
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
 L'agente di lettura log, l'agente di lettura coda e l'agente di distribuzione vengono in genere eseguiti in modo continuo, mentre altri agenti vengono eseguiti su richiesta o in base a una pianificazione. Se il completamento dell'esecuzione di un agente non è previsto, verificare lo stato dell'agente. Per altre informazioni, vedere [Monitor Replication Agents](agents/replication-agents.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione dell'agente di replica](agents/replication-agent-administration.md)   
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)   
 [Agente distribuzione repliche](agents/replication-distribution-agent.md)   
 [Agente lettura log repliche](agents/replication-log-reader-agent.md)   
 [Agente merge repliche](agents/replication-merge-agent.md)   
 [Agente di lettura coda repliche](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  
