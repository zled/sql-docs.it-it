---
title: "Connetti al server (Oracle), Account di accesso | Microsoft Docs"
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
  - "sql13.rep.oracleconnection.login.f1"
helpviewer_keywords: 
  - "Connetti al server (finestra di dialogo), replica"
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Connetti al server (Oracle), Account di accesso
  Utilizzare il **accesso** scheda della finestra il **Connetti al Server** la finestra di dialogo per specificare l'account con cui le connessioni vengono stabilite dal [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di distribuzione al server di pubblicazione Oracle. È necessario utilizzare lo stesso account specificato per lo schema utente di amministrazione della replica durante la configurazione del server di pubblicazione. Per ulteriori informazioni, vedere [configurare un server di pubblicazione Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## Opzioni  
 **Istanza del server**  
 Transparent Network Substrate del server di pubblicazione Oracle specificato durante la configurazione del software client Oracle installato nel server di distribuzione.  
  
 **Autenticazione**  
 Selezionare **autenticazione Standard Oracle** (scelta consigliata) o **l'autenticazione di Windows**. Se si seleziona **l'autenticazione di Windows**:  
  
-   Il server Oracle deve essere configurato in modo da consentire le connessioni con le credenziali di Windows. Per ulteriori informazioni, vedere la documentazione di Oracle.  
  
-   È necessario eseguire l'accesso con lo stesso account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows specificato per lo schema utente di amministrazione della replica.  
  
 **Account di accesso** e **Password**  
 Se è stata selezionata l'opzione **autenticazione Standard Oracle** per il **autenticazione** specificare l'account di accesso e una password da utilizzare, che deve corrispondere a quelli specificati per lo schema utente di amministrazione della replica.  
  
## Vedere anche  
 [Glossario dei termini per la pubblicazione Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  