---
title: "Sicurezza agente di lettura log (replica peer-to-peer) | Microsoft Docs"
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
  - "sql13.rep.p2pwizard.LRA.f1"
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Sicurezza agente di lettura log (replica peer-to-peer)
  Il **sicurezza agente di lettura Log** pagina consente di specificare gli account con cui viene eseguito l'agente di lettura Log in ogni peer e stabilisce le connessioni. Per informazioni sulle autorizzazioni necessarie agli agenti e le procedure consigliate per la sicurezza della replica, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md) e [procedure ottimali di protezione della replica](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  esiste un agente di lettura log per ogni database pubblicato tramite la replica transazionale. Se l'agente di lettura log per un database è già stato configurato per una pubblicazione nel corso di una precedente esecuzione di questa procedura guidata oppure per un'altra pubblicazione transazionale nello stesso database, in questa procedura guidata non è possibile modificare le credenziali utilizzate dall'agente di lettura log. Se vengono specificate nuove credenziali, queste verranno ignorate. Per modificare le credenziali, utilizzare il **Proprietà pubblicazione** la finestra di dialogo. Per ulteriori informazioni, vedere [visualizzare e modificare le impostazioni di sicurezza](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## Opzioni  
 Fare clic sul pulsante delle proprietà (**...**) nella riga per ogni peer per accedere al **sicurezza agente di lettura Log** la finestra di dialogo. Fare clic su **Guida** sul **sicurezza agente di lettura Log** la finestra di dialogo che viene avviata per ulteriori informazioni sulle autorizzazioni necessarie per gli account utilizzati dagli agenti.  
  
 Dopo aver immesso le impostazioni nella finestra di dialogo, nella griglia vengono visualizzate le informazioni sulla connessione per il Sottoscrittore.  
  
 **Agenti per il server di pubblicazione**  
 Nome di ogni istanza del server peer.  
  
 **Database peer**  
 Database che funge da database di pubblicazione e da database di sottoscrizione in ogni peer.  
  
 **Connessione al server di distribuzione**  
 Contesto in cui viene creata la connessione al server di distribuzione. La connessione locale al server di distribuzione viene sempre eseguita utilizzando il contesto del [!INCLUDE[msCoName](../../includes/msconame-md.md)] account Windows con cui viene eseguito l'agente, pertanto in questo campo viene sempre visualizzato **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'**.  
  
 **Connessione server di pubblicazione**  
 Contesto nel quale viene stabilita la connessione al server di pubblicazione. La connessione al server di pubblicazione può essere eseguita utilizzando un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso o utilizzando il contesto dell'account di Windows con cui viene eseguito l'agente. Il campo viene visualizzato uno dei seguenti: **accesso utilizzare ' \< Login>'**, **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] si consiglia che tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
## Vedere anche  
 [Amministrare una topologia Peer-to-Peer & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Replica transazionale peer-to-peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  