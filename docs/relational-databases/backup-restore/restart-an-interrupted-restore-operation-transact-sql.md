---
title: Riavviare un&quot;operazione di ripristino interrotta (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1a41e345b6122be18ca05186e7bc82d48c566fb9
ms.lasthandoff: 04/11/2017

---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a>Riavvio di un'operazione di ripristino interrotta (Transact-SQL)
  In questo argomento viene descritta la procedura per il riavvio di un'operazione di ripristino interrotta.  
  
### <a name="to-restart-an-interrupted-restore-operation"></a>Per riavviare un'operazione di ripristino interrotta  
  
1.  Eseguire nuovamente l'istruzione RESTORE interrotta, specificando:  
  
    -   Le stesse clausole utilizzate nell'istruzione RESTORE originale.  
  
    -   La clausola RESTART.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene riavviata un'operazione di ripristino interrotta.  
  
```tsql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristini di database completi &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Ripristini di database completi &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
