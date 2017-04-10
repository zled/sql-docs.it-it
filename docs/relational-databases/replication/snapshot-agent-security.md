---
title: "Sicurezza agente snapshot | Microsoft Docs"
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
  - "sql13.rep.security.SSA.f1"
helpviewer_keywords: 
  - "Sicurezza agente snapshot - finestra di dialogo"
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Sicurezza agente snapshot
  Il **sicurezza agente Snapshot** la finestra di dialogo consente di specificare:  
  
-   L'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows con cui viene eseguito l'agente snapshot nel server di distribuzione. L'account di Windows è detto anche *account di processo*, poiché si tratta dell'account con cui viene eseguito il processo dell'agente.  
  
-   Il contesto in cui l'agente Snapshot stabilisce le connessioni per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. La connessione può essere stabilita tramite rappresentazione dell'account di Windows oppure nel contesto di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato dall'utente.  
  
    > [!NOTE]  
    >  L'agente snapshot stabilisce le connessioni al server di pubblicazione anche quando il server di pubblicazione e il server di distribuzione si trovano nello stesso computer. L'agente snapshot stabilisce inoltre le connessioni al server di distribuzione. Tali connessioni vengono sempre stabilite tramite rappresentazione dell'account di  Windows con cui viene eseguito l'agente.  
  
     Server di pubblicazione Oracle, specificare il contesto in cui l'agente Snapshot si connette al server di pubblicazione nel **proprietà server di pubblicazione** la finestra di dialogo (disponibile dalla **proprietà server di distribuzione** la finestra di dialogo). Per ulteriori informazioni, vedere [visualizzare e modificare le impostazioni di sicurezza](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Tutti gli account devono essere validi e per ogni account deve essere stata specificata la password corretta. Gli account e le password vengono convalidati solo dopo l'avvio dell'esecuzione di un agente.  
  
## Opzioni  
 **Account processo**  
 Consente di immettere un account di Windows con cui eseguire l'agente snapshot nel server di distribuzione. L'account di Windows specificato deve:  
  
-   Appartenere almeno il **db_owner** ruolo predefinito del database nel database di distribuzione.  
  
-   Disporre delle autorizzazioni di scrittura per la condivisione snapshot.  
  
 **Password** e **Conferma password**  
 Immettere la password per l'account di Windows.  
  
 **Connessione al server di pubblicazione**  
 Selezionare se l'agente Snapshot deve stabilire connessioni al server di pubblicazione tramite la rappresentazione dell'account specificato nella **account di processo** casella di testo o utilizzando un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account. Se si seleziona l'opzione per l'utilizzo di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , immettere un account di accesso e una password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  È consigliabile scegliere di rappresentare l'account di Windows anziché di utilizzare un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 L'account di Windows o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account utilizzato per la connessione deve essere almeno un membro del **db_owner** ruolo predefinito del database nel database di pubblicazione.  
  
## Vedere anche  
 [Gestione degli account di accesso e delle password nella replica](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  