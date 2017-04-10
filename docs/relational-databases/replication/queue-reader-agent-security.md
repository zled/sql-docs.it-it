---
title: "Sicurezza agente di lettura coda | Microsoft Docs"
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
  - "sql13.rep.security.QRA.f1"
helpviewer_keywords: 
  - "Sicurezza agente di lettura coda - finestra di dialogo"
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Sicurezza agente di lettura coda
  Il **sicurezza agente di lettura coda** la finestra di dialogo consente di specificare il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account Windows con cui viene eseguito l'agente di lettura coda e stabilisce connessioni locali al server di distribuzione. L'agente si connette al server di pubblicazione utilizzando l'account specificato nella **proprietà server di pubblicazione** la finestra di dialogo (disponibile dalla **proprietà server di distribuzione** la finestra di dialogo); l'agente si connette al sottoscrittore utilizzando lo stesso contesto dell'agente di distribuzione per la sottoscrizione. Per ulteriori informazioni, vedere [visualizzare e modificare le impostazioni di sicurezza](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 L'account deve essere valido è deve essere stata specificata la password corretta. Gli account e le password vengono convalidati solo dopo l'avvio dell'esecuzione di un agente.  
  
## Opzioni  
 **Account processo**  
 Consente di immettere l'account di Windows con cui viene eseguito l'agente di lettura coda nel server di distribuzione. L'account Windows specificato come minimo deve essere un membro del **db_owner** ruolo predefinito del database nel database di distribuzione.  
  
 **Password** e **Conferma password**  
 Immettere la password per l'account di Windows.  
  
## Vedere anche  
 [Gestione degli account di accesso e delle password nella replica](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  