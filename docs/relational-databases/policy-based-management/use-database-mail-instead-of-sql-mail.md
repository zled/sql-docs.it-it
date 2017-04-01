---
title: "Utilizzo di Posta elettronica database anzich&#233; di SQL Mail | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Procedure consigliate [Motore di database]"
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Utilizzo di Posta elettronica database anzich&#233; di SQL Mail
  Questa regola consente di controllare la vista del catalogo sys.configurations per determinare se l'opzione di configurazione SQL Mail XPS per l'intero server è impostata su ON.  
  
## Procedure consigliate  
 SQL Mail verrà rimosso in una delle versioni future di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Per inviare messaggi, utilizzare Posta elettronica database.  
  
 SQL Mail viene eseguito in-process nel servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se l'esecuzione di SQL Mail si interrompe, anche il server diventa inattivo. Posta elettronica database viene eseguito in un processo distinto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è scalabile e non richiede l'installazione di componenti client MAPI estesi nel server di produzione.  
  
## Ulteriori informazioni  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)  
  
## Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  