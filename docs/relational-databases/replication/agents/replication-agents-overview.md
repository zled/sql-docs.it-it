---
title: "Panoramica degli agenti di replica | Microsoft Docs"
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
  - "Agente di distribuzione"
  - "agenti [replica di SQL Server]"
  - "agente di lettura coda, informazioni sull'agente di lettura coda"
  - "Agente di lettura coda"
  - "agente di merge, informazioni sull'agente di merge"
  - "agente di lettura log, informazioni sull'agente di lettura log"
  - "replica [SQL Server], agenti e profili"
  - "Agente di lettura log"
  - "agente di distribuzione, informazioni sull'agente di distribuzione"
  - "agenti [replica di SQL Server], informazioni sugli agenti"
  - "Agente di merge"
  - "agente snapshot, informazioni sull'agente snapshot"
  - "agente snapshot"
ms.assetid: a35ecd7d-f130-483c-87e3-ddc8927bb91b
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Panoramica degli agenti di replica
  La replica utilizza alcuni programmi autonomi, denominati agenti, per eseguire le attività associate al rilevamento delle modifiche e alla distribuzione dei dati. Per impostazione predefinita, gli agenti di replica vengono eseguiti come processi pianificati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent e, a tale scopo, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent deve essere in funzione. Gli agenti di replica possono inoltre essere eseguiti dalla riga di comando e dalle applicazioni che utilizzano gli oggetti RMO (Replication Management Objects) e possono essere amministrati con Monitoraggio replica per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e con [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
## SQL Server Agent  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agente host e pianifica gli agenti utilizzati nella replica e fornisce un modo semplice per eseguire gli agenti di replica. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent consente inoltre di controllare e monitorare le operazioni all'esterno di replica. Per altre informazioni, vedere [Configure SQL Server Agent](../../../ssms/agent/configure-sql-server-agent.md).  
  
> [!IMPORTANT]  
>  Per impostazione predefinita, il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è disabilitato durante l'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a meno che non si scelga in modo esplicito di avviarlo automaticamente durante l'installazione. Per ulteriori informazioni sull'avvio di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] servizio agente, vedere [avviare, arrestare o sospendere il servizio SQL Server Agent](../../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).  
  
## agente snapshot  
 L'agente snapshot viene in genere utilizzato con tutti i tipi di replica. Questo agente prepara schemi e file dei dati iniziali di tabelle pubblicate e di altri oggetti, archivia i file di snapshot e registra le informazioni sulla sincronizzazione nel database di distribuzione. L'agente snapshot viene eseguito nel server di distribuzione. Per ulteriori informazioni, vedere [agente Snapshot repliche](../../../relational-databases/replication/agents/replication-snapshot-agent.md).  
  
## Agente di lettura log  
 L'agente di lettura dei log viene utilizzato nella replica transazionale. Questo agente sposta le transazioni contrassegnate per la replica dal log delle transazioni nel server di pubblicazione al database di distribuzione. A ogni database pubblicato tramite la replica transazionale è associato un agente di lettura log specifico eseguito nel server di distribuzione e connesso al server di pubblicazione. Il server di distribuzione e il server di pubblicazione possono coesistere nello stesso computer. Per altre informazioni, vedere [Replication Log Reader Agent](../../../relational-databases/replication/agents/replication-log-reader-agent.md).  
  
## Agente di distribuzione  
 L'agente di distribuzione viene utilizzato nella replica snapshot e nella replica transazionale. Questo agente applica lo snapshot iniziale al Sottoscrittore e trasferisce nei Sottoscrittori le transazioni archiviate nel database di distribuzione. L'agente di distribuzione viene eseguito nel server di distribuzione per le sottoscrizioni push o nel Sottoscrittore per le sottoscrizioni pull. Per ulteriori informazioni, vedere [agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
## Agente di merge  
 L'agente di merge viene utilizzato nella replica di tipo merge. Questo agente applica lo snapshot iniziale al Sottoscrittore e trasferisce e riconcilia le modifiche incrementali apportate ai dati. Per ogni sottoscrizione di tipo merge è disponibile un agente di merge specifico che si connette sia al server di pubblicazione che al Sottoscrittore aggiornandoli entrambi. L'agente di merge viene eseguito nel server di distribuzione per le sottoscrizioni push o nel Sottoscrittore per le sottoscrizioni pull. Per impostazione predefinita, l'agente di merge carica le modifiche dal Sottoscrittore al server di pubblicazione e quindi scarica le modifiche dal server di pubblicazione al Sottoscrittore. Per ulteriori informazioni, vedere [agente Merge repliche](../../../relational-databases/replication/agents/replication-merge-agent.md).  
  
## Agente di lettura coda  
 L'agente di lettura coda viene utilizzato nella replica transazionale con l'opzione di aggiornamento in coda. L'agente viene eseguito nel server di distribuzione e trasferisce le modifiche apportate nel Sottoscrittore nuovamente nel server di pubblicazione. A differenza dell'agente di distribuzione e dell'agente di merge, per tutti i server di pubblicazione e le pubblicazioni di un database di distribuzione specifico esiste una sola istanza dell'agente di lettura coda. Per ulteriori informazioni sull'agente di lettura coda, vedere [agente di lettura coda repliche](../../../relational-databases/replication/agents/replication-queue-reader-agent.md). Per ulteriori informazioni sulle sottoscrizioni aggiornabili, vedere [sottoscrizioni aggiornabili per la replica transazionale](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
## Processi di manutenzione della replica  
 La replica include alcuni processi di manutenzione che consentono di eseguire operazioni di manutenzione pianificata e su richiesta. Per ulteriori informazioni, vedere [amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md).  
  
## Vedere anche  
 [Avviare e arrestare un agente di replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Eseguire processi di manutenzione della replica & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)   
 [Concetti di base relativi ai file eseguibili dell'agente di replica](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Amministrazione dell'agente di replica](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  