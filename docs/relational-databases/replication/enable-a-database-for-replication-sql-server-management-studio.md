---
title: "Abilitazione di un database per la replica (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "database [replica di SQL Server]"
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Abilitazione di un database per la replica (SQL Server Management Studio)
  Un database in modo implicito è abilitato per la replica quando un membro del **sysadmin** ruolo predefinito del server viene creata una pubblicazione con la creazione guidata nuova pubblicazione. Un membro del **sysadmin** ruolo predefinito del server possono inoltre attivare un database per la replica in modo esplicito, in modo che un membro del **db_owner** ruolo predefinito del database è possibile creare una o più pubblicazioni in tale database. Per abilitare un database in modo esplicito, utilizzare il **i database di pubblicazione** pagina della **proprietà server di pubblicazione - \< Publisher>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [creare una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md).  
  
### Per abilitare un database per la replica  
  
1.  Nel **i database di pubblicazione** pagina del **proprietà server di pubblicazione - \< Publisher>** la finestra di dialogo, selezionare il **transazionale** e/o **Merge** casella di controllo per ogni database che si desidera replicare. Selezionare **transazionale** per abilitare il database per la replica snapshot.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  