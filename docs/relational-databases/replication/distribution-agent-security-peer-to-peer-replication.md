---
title: "Sicurezza agente di distribuzione (replica peer-to-peer) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.p2pwizard.DA.f1"
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Sicurezza agente di distribuzione (replica peer-to-peer)
  Il **sicurezza agente di distribuzione** pagina consente di specificare gli account con cui viene eseguito l'agente di distribuzione e stabilisce le connessioni ai computer in una topologia peer-to-peer. Per informazioni sulle autorizzazioni necessarie agli agenti e le procedure consigliate per la sicurezza della replica, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md) e [procedure ottimali di protezione della replica](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Se l'agente di distribuzione per una sottoscrizione è già stato configurato in un'esecuzione precedente della procedura guidata, non è possibile modificare le credenziali utilizzate in questa procedura. Se vengono specificate nuove credenziali, queste verranno ignorate. Per modificare le credenziali, utilizzare il **le proprietà della sottoscrizione** la finestra di dialogo. Per ulteriori informazioni, vedere [visualizzare e modificare le impostazioni di sicurezza](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## Opzioni  
 Fare clic sul pulsante delle proprietà (**...**) nella riga per ogni sottoscrittore per accedere al **sicurezza agente di distribuzione** la finestra di dialogo. Fare clic su **Guida** sul **sicurezza agente di distribuzione** la finestra di dialogo che viene avviata per ulteriori informazioni sulle autorizzazioni necessarie per gli account utilizzati dagli agenti.  
  
 Dopo l'immissione delle impostazioni in una delle finestre di dialogo, le informazioni di connessione per il Sottoscrittore vengono visualizzate nella griglia.  
  
 **Agente per Sottoscrittore**  
 Nome di ciascun peer.  
  
 **Database peer**  
 Il database nel peer che fungerà da database di pubblicazione e da database di sottoscrizione.  
  
 **Connessione al server di distribuzione**  
 Contesto in cui viene creata la connessione al server di distribuzione. Le connessioni locali vengono create sempre mediante il contesto dell'account di Windows utilizzato per l'esecuzione dell'agente. Questa procedura guidata crea le sottoscrizioni push (la connessione locale è la connessione al server di distribuzione), pertanto in questo campo viene sempre visualizzato: **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'**.  
  
 **Connessione al Sottoscrittore**  
 Contesto in cui viene creata la connessione al Sottoscrittore. La connessione può essere creata tramite il contesto dell'account di Windows utilizzato per l'esecuzione dell'agente o nel contesto di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il campo viene visualizzato uno dei seguenti: **accesso utilizzare ' \< Login>'**, **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] si consiglia che tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
## Vedere anche  
 [Amministrare una topologia Peer-to-Peer & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Replica transazionale peer-to-peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  