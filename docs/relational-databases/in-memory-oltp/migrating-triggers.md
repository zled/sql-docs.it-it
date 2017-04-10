---
title: "Migrazione di trigger | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
caps.latest.revision: 13
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 13
---
# Migrazione di trigger
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  In questo argomento vengono illustrati i trigger DDL e le tabelle con ottimizzazione per la memoria.  
  
 I trigger DML sono supportati nelle tabelle con ottimizzazione per la memoria, ma solo con l'evento trigger FOR | AFTER. Ad esempio, vedere [Implementing UPDATE with FROM or Subqueries](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md) (Implementazione di UPDATE con FROM o sottoquery). 
  
 I trigger LOGON sono trigger definiti per l'attivazione in corrispondenza di eventi LOGON. I trigger LOGON non influiscono sulle tabelle con ottimizzazione per la memoria.  
  
## Trigger DDL  
 I trigger DDL sono trigger definiti per l'attivazione quando un'istruzione CREATE, ALTER, DROP, GRANT, DENY, REVOKE o UPDATE STATISTICS viene eseguita nel database o nel server in cui è definita.  
  
 Non è possibile creare tabelle con ottimizzazione per la memoria se nel database o nel server sono definiti uno o più trigger DDL per l'evento CREATE_TABLE o per qualsiasi gruppo di eventi in cui questo sia incluso. Non è possibile eliminare una tabella con ottimizzazione per la memoria se nel database o nel server sono definiti uno o più trigger DDL per l'evento DROP_TABLE o per qualsiasi gruppo di eventi in cui questo sia incluso.  
  
 Non è possibile creare stored procedure compilate in modo nativo se sono presenti uno o più trigger DDL per gli eventi CREATE_PROCEDURE, DROP_PROCEDURE o per qualsiasi gruppo di eventi in cui questi siano inclusi.  
  
## Vedere anche  
 [Migrazione a OLTP in memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  