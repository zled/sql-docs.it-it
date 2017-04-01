---
title: "Autorizzazioni Guest nei database utente | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Procedure consigliate [Motore di database]"
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Autorizzazioni Guest nei database utente
  Questa regola consente di determinare se l'utente guest dispone dell'autorizzazione necessaria per accedere al database. Questa regola si applica solo ai database utente.  
  
## Procedure consigliate  
 Se non è necessaria, revocare l'autorizzazione di accesso al database dell'utente guest.  
  
 L'utente guest non può essere rimosso. È tuttavia possibile disabilitarlo revocandone l'autorizzazione CONNECT tramite l'esecuzione di REVOKE CONNECT FROM GUEST all'interno di un database diverso da master, tempdb o msdb.  
  
## Ulteriori informazioni  
 [Sicurezza di SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  