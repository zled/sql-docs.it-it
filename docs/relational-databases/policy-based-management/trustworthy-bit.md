---
title: "Bit relativo alla propriet&#224; trustworthy | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Procedure consigliate [Motore di database]"
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Bit relativo alla propriet&#224; trustworthy
  Questa regola consente di determinare se il ruolo dbo per un database è assegnato al ruolo predefinito del server sysadmin e se per il database il bit relativo alla proprietà trustworthy è impostato su ON.  
  
 Se queste condizioni vengono soddisfatte, un utente di database con privilegi potrà elevare il livello di privilegi al ruolo sysadmin. In questo ruolo l'utente può creare ed eseguire assembly non protetti che potrebbero danneggiare il sistema.  
  
## Procedure consigliate  
 Disattivare il bit relativo alla proprietà trustworthy o revocare le autorizzazioni sysadmin al ruolo del database dbo.  
  
## Ulteriori informazioni  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  