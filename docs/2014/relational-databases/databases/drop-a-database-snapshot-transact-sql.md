---
title: Eliminare uno snapshot del database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e20a75d891595333afb19187d90ea7accc679957
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48229561"
---
# <a name="drop-a-database-snapshot-transact-sql"></a>Eliminare uno snapshot del database (Transact-SQL)
  La rimozione di uno snapshot del database comporta l'eliminazione dello snapshot da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nonché l'eliminazione dei file sparse da esso utilizzati. Quando si elimina uno snapshot del database, tutte le relative connessioni utente vengono interrotte.  
  
## <a name="security"></a>Sicurezza  
  
###  <a name="Permissions"></a> Permissions  
 Uno snapshot del database può essere rimosso da qualsiasi utente che disponga delle autorizzazioni DROP DATABASE.  
  
##  <a name="TsqlProcedure"></a> Come eliminare uno snapshot del database (tramite Transact-SQL)  
 **Per eliminare uno snapshot del database**  
  
1.  Identificare lo snapshot del database da eliminare. È possibile visualizzare gli snapshot di un database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Visualizzare uno snapshot del database &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).  
  
2.  Eseguire un'istruzione [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) , specificando il nome dello snapshot del database da eliminare. La sintassi è la seguente:  
  
     DROP DATABASE *database_snapshot_name* [ **,**...*n* ]  
  
     Dove *database_snapshot_name* è il nome dello snapshot del database da eliminare.  
  
####  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 Nell'esempio seguente viene rimosso uno snapshot di database, denominato SalesSnapshot0600, senza influire sul database di origine.  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 Tutte le connessioni utente a SalesSnapshot0600 vengono terminate e tutti i file sparse del file system NTFS utilizzati dallo snapshot vengono eliminati.  
  
> [!NOTE]  
>  Per informazioni sull'uso di file sparse con gli snapshot del database, vedere [Snapshot del database &#40;SQL Server&#41;](database-snapshots-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Creare uno snapshot del database &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md)  
  
-   [Visualizzare uno snapshot del database &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)  
  
-   [Ripristinare un database a uno snapshot del database](revert-a-database-to-a-database-snapshot.md)  
  

  
## <a name="see-also"></a>Vedere anche  
 [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)   
 [Snapshot del database &#40;SQL Server&#41;](database-snapshots-sql-server.md)  
  
  
