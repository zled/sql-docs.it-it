---
title: "&lt;AgentName&gt; Agent Security | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.agentnameagentsecurity.f1"
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# &lt;AgentName&gt; Agent Security
  Il **\< AgentName> agente protezione** pagina consente di specificare gli account con cui l'agente di distribuzione (per la replica transazionale e snapshot) o l'agente di Merge (per la replica di tipo merge) esecuzione e le connessioni ai computer in una topologia di replica. Per informazioni sulle autorizzazioni necessarie agli agenti e le procedure consigliate per la sicurezza della replica, vedere [modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md) e [procedure ottimali di protezione della replica](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## Opzioni  
 Fare clic sul pulsante delle proprietà (**...**) nella riga per ogni sottoscrittore per accedere al **sicurezza agente di distribuzione** o **sicurezza agente di Merge** la finestra di dialogo. Fare clic su **Guida** nella finestra di dialogo che viene avviata per ulteriori informazioni sulle autorizzazioni necessarie per gli account utilizzati dagli agenti.  
  
 Dopo l'immissione delle impostazioni in una delle finestre di dialogo, le informazioni di connessione per il Sottoscrittore vengono visualizzate nella griglia.  
  
 **Agente per Sottoscrittore**  
 Nome di ciascun Sottoscrittore.  
  
 **Connessione al server di distribuzione**  
 Visualizzato per la replica transazionale e snapshot. Contesto in cui viene creata la connessione al server di distribuzione. Le connessioni locali vengono create sempre mediante il contesto dell'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows utilizzato per l'esecuzione dell'agente:  
  
-   Per le sottoscrizioni push, la connessione locale è la connessione al server di distribuzione, pertanto in questo campo viene sempre visualizzato: **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'** per le sottoscrizioni push.  
  
-   Per le sottoscrizioni pull, la connessione può inoltre essere creata nel contesto di un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso. Il campo viene visualizzato uno dei seguenti: **accesso utilizzare ' \< Login>'**, **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] si consiglia che tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
 **Connessione al server di pubblicazione e al server di distribuzione**  
 Visualizzato per la replica di tipo merge. Contesto in cui vengono create le connessioni al server di pubblicazione e al server di distribuzione. Le connessioni locali vengono create sempre mediante il contesto dell'account di Windows utilizzato per l'esecuzione dell'agente:  
  
-   Per le sottoscrizioni push, la connessione locale è la connessione al server di pubblicazione e server di distribuzione, pertanto in questo campo viene sempre visualizzato: **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'** per le sottoscrizioni push.  
  
-   Per le sottoscrizioni pull, la connessione può inoltre essere creata nel contesto di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il campo viene visualizzato uno dei seguenti: **accesso utilizzare ' \< Login>'**, **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] si consiglia che tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
 **Connessione al Sottoscrittore**  
 Contesto in cui viene creata la connessione al Sottoscrittore. Le connessioni locali vengono create sempre mediante il contesto dell'account di Windows utilizzato per l'esecuzione dell'agente:  
  
-   Per le sottoscrizioni pull, la connessione locale è la connessione al sottoscrittore, pertanto in questo campo viene sempre visualizzato: **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'** per le sottoscrizioni push.  
  
-   Per le sottoscrizioni push, la connessione può inoltre essere creata nel contesto di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il campo viene visualizzato uno dei seguenti: **accesso utilizzare ' \< Login>'**, **Impersonate ' \< dominio>\\< account di accesso\>'** o **Impersonate ' \< Computer>\\< account di accesso\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] si consiglia che tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
## Vedere anche  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Gestione degli account di accesso e delle password nella replica](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  