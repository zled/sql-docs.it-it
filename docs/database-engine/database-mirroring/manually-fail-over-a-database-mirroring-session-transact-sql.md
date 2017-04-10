---
title: "Failover manuale in una sessione di mirroring del database (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "failover [SQL Server], mirroring del database"
  - "failover manuale [SQL Server]"
  - "mirroring del database [SQL Server], failover"
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
caps.latest.revision: 32
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 32
---
# Failover manuale in una sessione di mirroring del database (Transact-SQL)
  Quando il database con mirroring è sincronizzato, ovvero è in stato SYNCHRONIZED, il proprietario del database può iniziare il failover manuale al server mirror. Il failover manuale può essere avviato solo dal server principale.  
  
### Per eseguire il failover manuale in una sessione di mirroring del database  
  
1.  Connettersi al server principale.  
  
2.  Impostare il contesto del database sul database **master**:  
  
     **USE master;**  
  
3.  Eseguire l'istruzione seguente sul server principale:  
  
     [ALTER DATABASE](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md) *nome_database* SET PARTNER FAILOVER, dove *nome_database* rappresenta il database con mirroring.  
  
     Verrà avviata una transizione immediata del server mirror al ruolo principale.  
  
 Nel server principale precedente i client verranno disconnessi dal database e verrà eseguito il rollback delle transazioni di cui è in corso la migrazione.  
  
> [!NOTE]  
>  Le transazioni preparate utilizzando [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator ma delle quali non sia stato ancora eseguito il commit quando si verifica un failover sono considerate interrotte dopo il failover del database.  
  
## Vedere anche  
 [Mirroring del database di ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [Failover manuale di una sessione di mirroring del database &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [Cambio di ruolo durante una sessione di mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  