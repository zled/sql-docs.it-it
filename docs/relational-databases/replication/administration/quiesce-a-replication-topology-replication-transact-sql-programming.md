---
title: "Come mettere una topologia di replica in stato di inattivit&#224; (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "amministrazione della replica, disattivazione"
  - "stato di inattività [replica di SQL Server]"
  - "replica transazionale, backup e ripristino"
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Come mettere una topologia di replica in stato di inattivit&#224; (programmazione Transact-SQL della replica)
  *Disattivazione* un sistema significa arrestare le attività sulle tabelle pubblicate in tutti i nodi e verificare che ogni nodo abbia ricevuto tutte le modifiche apportate dagli altri nodi. In questo argomento è illustrato come mettere in stato di inattività una topologia di replica, operazione necessaria per diverse attività amministrative, e assicurarsi che un nodo abbia ricevuto tutte le modifiche dagli altri nodi.  
  
### Per mettere in stato di inattività una topologia di replica transazionale con sottoscrizioni di sola lettura  
  
1.  Arrestare l'attività in tutte le tabelle pubblicate nel server di pubblicazione.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_posttracertoken & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md).  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
4.  Assicurarsi che ciascun Sottoscrittore abbia ricevuto il token di traccia.  
  
### Per mettere in stato di inattività una topologia di replica transazionale con sottoscrizioni aggiornabili  
  
1.  Arrestare l'attività in tutte le tabelle pubblicate nel server di pubblicazione e in tutti i Sottoscrittori.  
  
2.  Se i Sottoscrittori utilizzano sottoscrizioni ad aggiornamento in coda:  
  
    1.  Se l'agente di lettura coda non viene eseguito in modalità continua, eseguire l'agente. Per ulteriori informazioni sull'esecuzione degli agenti, vedere [concetti eseguibili agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) o [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    2.  Per verificare che la coda è vuota, eseguire [sp_replqueuemonitor](../../../relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql.md) in ogni sottoscrittore.  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_posttracertoken](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md).  
  
4.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
5.  Assicurarsi che ciascun Sottoscrittore abbia ricevuto il token di traccia.  
  
### Per mettere in stato di inattività una topologia di replica transazionale peer-to-peer  
  
1.  Arrestare l'attività in tutte le tabelle pubblicate in tutti i nodi.  
  
2.  Eseguire [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) su ciascun database di pubblicazione nella topologia.  
  
3.  Se l'agente di lettura log o l'agente di distribuzione non viene eseguito in modalità continua, eseguire l'agente. L'agente di lettura log deve essere avviato prima l'agente di distribuzione. Per ulteriori informazioni sull'esecuzione degli agenti, vedere [concetti eseguibili agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) o [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
4.  Eseguire [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) su ciascun database di pubblicazione nella topologia. Assicurarsi che il set di risultati contenga risposte da ciascuno degli altri nodi.  
  
### Per assicurarsi che un nodo peer-to-peer abbia ricevuto tutte le modifiche precedenti  
  
1.  Eseguire [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) nel database di pubblicazione in corrispondenza del nodo che si stanno archiviando.  
  
2.  Se l'agente di lettura log o l'agente di distribuzione non viene eseguito in modalità continua, eseguire l'agente. L'agente di lettura log deve essere avviato prima l'agente di distribuzione. Per ulteriori informazioni sull'esecuzione degli agenti, vedere [concetti eseguibili agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) o [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  Eseguire [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) nel database di pubblicazione in corrispondenza del nodo che si stanno archiviando. Assicurarsi che il set di risultati contenga risposte da ciascuno degli altri nodi.  
  
### Per mettere in stato di inattività una topologia di replica di tipo merge  
  
1.  Arrestare l'attività in tutte le tabelle pubblicate nel server di pubblicazione e in tutti i Sottoscrittori.  
  
2.  Eseguire due volte l'agente di merge per ciascuna sottoscrizione: sincronizzare una volta tutte le sottoscrizioni, quindi sincronizzare ciascuna di esse una seconda volta. In questo modo si garantisce che tutte le modifiche vengano replicate in tutti i nodi. Per ulteriori informazioni sull'esecuzione degli agenti, vedere [concetti eseguibili agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) o [avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    > [!NOTE]  
    >  Se si verificano conflitti durante la sincronizzazione, è possibile che le modifiche richieste per la risoluzione dei conflitti non vengano propagate in tutti i nodi dopo aver eseguito due volte l'agente di merge.  
  
## Vedere anche  
 [Amministrare una topologia Peer-to-Peer & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Measure Latency and Validate Connections for Transactional Replication](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  