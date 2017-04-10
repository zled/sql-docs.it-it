---
title: "Sicurezza del database di distribuzione | Microsoft Docs"
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
  - "sicurezza [replica di SQL Server], database di distribuzione"
  - "database di distribuzione [replica di SQL Server], sicurezza"
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Sicurezza del database di distribuzione
  Gli agenti di replica che si connettono al server di distribuzione sono l'agente di lettura log, l'agente snapshot, l'agente di lettura coda, l'agente di distribuzione e l'agente di merge. È importante fornire un account di accesso appropriato per ognuno di questi agenti seguendo il principio di concedere i diritti minimi necessari nonché proteggere l'archiviazione di tutte le password:  
  
-   Per informazioni sulla gestione di account di accesso e password, vedere [gestire account di accesso e password nella replica](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
-   Per informazioni dettagliate sulle autorizzazioni necessarie per ogni agente, vedere [modello di sicurezza dell'agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Oltre a gestire gli account di accesso e password in modo appropriato, è importante comprendere il ruolo di **repl_distributor** collegamento al server remoto e il **distributor_admin** account.  
  
## Protezione della connessione dal server di pubblicazione al server di distribuzione  
 Per supportare la comunicazione necessaria quando il server di pubblicazione e aggiornare le informazioni nel server di distribuzione eseguire stored procedure di amministrazione, replica configura automaticamente il server remoto **repl_distributor**. Il **repl_distributor** voce del server remoto viene utilizzata per la comunicazione con il database di distribuzione a prescindere se il database di distribuzione è contenuto all'interno dell'istanza del server di pubblicazione (server di distribuzione locale) o si trova all'interno di una sessione remota [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza (un server di distribuzione remoto).  
  
 Quando il database di distribuzione è contenuto in un'istanza locale, una password casuale viene generata e configurata automaticamente. Quando il database di distribuzione si trova in un'istanza remota, l'amministratore configura una password condivisa durante l'installazione del server di pubblicazione e server di distribuzione; Questa password viene quindi utilizzata per fornire l'autenticazione del traffico che attraversa il **repl_distributor** collegamento.  
  
 Il server di distribuzione utilizza il **repl_distributor** voce del server remoto per verificare che il server chiamante è configurato come server di pubblicazione nel server di distribuzione, convalida la password fornita dal server di pubblicazione e verifica che la stored procedure è una replica di tipo stored procedure durante l'esecuzione.  
  
 La password configurata per il **repl_distributor** voce durante l'installazione del server remoto è associata un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account di accesso, **distributor_admin**, che viene aggiunto al **sysadmin** ruolo predefinito del server nel server di distribuzione. Il **distributor_admin** account di accesso utilizzato dalla stored procedure di replica durante la connessione al server di distribuzione.  
  
> [!NOTE]  
>  Non modificare la password per il **distributor_admin** manualmente. Utilizzare sempre il **sp_changedistributor_password** stored procedure o **proprietà server di distribuzione** o **Aggiorna password replica** finestre di dialogo [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], in quanto la modifica di password vengono quindi applicate alle pubblicazioni locali automaticamente.  
  
## Sicurezza della cartella snapshot  
 Verificare che la condivisione snapshot disponga di accesso in lettura per l'account con il quale viene eseguito l'agente di merge (per la replica di tipo merge) o l'agente di distribuzione (per la replica snapshot o transazionale) e di accesso in scrittura per l'account con il quale viene eseguito l'agente snapshot. Per ulteriori informazioni sulla cartella snapshot, vedere [sicurezza della cartella Snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
## Vedere anche  
 [View and Modify Replication Security Settings](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Abilitare connessioni crittografate al motore di Database & #40; Gestione configurazione SQL Server & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [Procedure consigliate per la sicurezza della replica](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  