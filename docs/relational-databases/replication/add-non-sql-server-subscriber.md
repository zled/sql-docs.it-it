---
title: "Aggiungi Sottoscrittore non SQL Server | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.addnonsqlsubscriber.f1"
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Aggiungi Sottoscrittore non SQL Server
  La replica supporta la creazione di sottoscrizioni push delle pubblicazioni transazionali e snapshot per i Sottoscrittori Oracle e IBM DB2.  
  
## Opzioni  
 **Tipo di Sottoscrittore da aggiungere**  
 Consente di selezionare un Sottoscrittore Oracle o IBM DB2. Per ulteriori informazioni sul supporto per questi abbonati, vedere [sottoscrittori Non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Nome origine dati**  
 Nome utilizzato per individuare il database in rete. La replica produce una stringa di connessione per il database utilizzando il nome dell'origine dati, combinato con l'account di accesso, password e le opzioni di connessione specificate nel **sicurezza agente di distribuzione** pagina della procedura guidata.  
  
> [!NOTE]  
>  La stringa di connessione e nome origine dati non vengono convalidati da [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fino a quando l'agente di distribuzione tenta di inizializzare la sottoscrizione.  
  
## Vedere anche  
 [Create a Subscription for a Non-SQL Server Subscriber](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Sottoscrittori non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  