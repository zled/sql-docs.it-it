---
title: "Sicurezza agente di lettura log | Microsoft Docs"
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
  - "sql13.rep.security.LRA.f1"
helpviewer_keywords: 
  - "Sicurezza agente di lettura log - finestra di dialogo"
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Sicurezza agente di lettura log
  Il **sicurezza agente di lettura Log** la finestra di dialogo consente di specificare:  
  
-   L'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows utilizzato per l'esecuzione dell'agente di lettura log nel server di distribuzione. L'account di Windows è detto anche *account di processo*, poiché si tratta dell'account con cui viene eseguito il processo dell'agente.  
  
-   Il contesto in cui l'agente di lettura Log stabilisce le connessioni per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. La connessione può essere stabilita tramite rappresentazione dell'account di Windows oppure nel contesto di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato dall'utente.  
  
    > [!NOTE]  
    >  L'agente di lettura log stabilisce le connessioni al server di pubblicazione anche se il server di pubblicazione e il server di distribuzione si trovano sullo stesso computer. L'agente di lettura log stabilisce inoltre le connessioni al server di distribuzione, sempre tramite la rappresentazione dell'account di Windows utilizzato per l'esecuzione dell'agente.  
  
     Server di pubblicazione Oracle, specificare il contesto in cui l'agente di lettura Log si connette al server di pubblicazione nel **proprietà server di pubblicazione** la finestra di dialogo (disponibile dalla **proprietà server di distribuzione** la finestra di dialogo). Per ulteriori informazioni, vedere [visualizzare e modificare le impostazioni di sicurezza](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Tutti gli account devono essere validi e per ogni account deve essere stata specificata la password corretta. Gli account e le password vengono convalidati solo dopo l'avvio dell'esecuzione di un agente.  
  
## Opzioni  
 **Account processo**  
 Consente di immettere un account di Windows utilizzato per l'esecuzione dell'agente di lettura log nel server di distribuzione. L'account Windows specificato come minimo deve essere un membro del **db_owner** ruolo predefinito del database nel database di distribuzione.  
  
 **Password** e **Conferma password**  
 Immettere la password per l'account di Windows.  
  
 **Connessione al server di pubblicazione**  
 Selezionare se l'agente di lettura Log deve stabilire connessioni al server di pubblicazione tramite la rappresentazione dell'account specificato nella **account di processo** casella di testo o utilizzando un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account. Se si seleziona l'opzione per l'utilizzo di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , immettere un account di accesso e una password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di scegliere di rappresentare l'account di Windows anziché utilizzando un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.  
  
 L'account di Windows o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account utilizzato per la connessione deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di pubblicazione.  
  
## Vedere anche  
 [Gestione degli account di accesso e delle password nella replica](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  