---
title: "Rimuovere un punto di controllo dell'utilità (Utilità SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: af1d64ea7139a213947dfd9d9da5f44822dc7985
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a>Rimuovere un punto di controllo dell'utilità (Utilità SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento illustra come rimuovere un punto di controllo dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per rimuovere un punto di controllo dell'utilità utilizzando:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Prima di utilizzare questa procedura per rimuovere il punto di controllo dell'utilità da Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tenere presente i requisiti seguenti. La stored procedure eseguirà i controlli necessari come parte dell'operazione.  
  
-   Prima di eseguire questa procedura, è necessario che tutte le istanze gestite di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengano rimosse dal punto di controllo dell'utilità. Si noti che il punto di controllo dell'utilità è un'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Rimuovere un'istanza di SQL Server da Utilità SQL Server](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
-   È necessario eseguire la procedura in un computer configurato come punto di controllo dell'utilità.  
  
-   Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da cui è stato rimosso il punto di controllo dell'utilità dispone di un set di raccolta dati non appartenente all'utilità, il database UMDW (sysutility_mdw) non verrà eliminato dalla procedura. In tal caso, è necessario eliminare manualmente il database UMDW (sysutility_mdw) prima di creare nuovamente il punto di controllo dell'utilità.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 La procedura deve essere eseguita da un utente che disponga di autorizzazioni **sysadmin** , le stesse necessarie per la creazione di un punto di controllo dell'utilità.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-remove-a-utility-control-point"></a>Per rimuovere un punto di controllo dell'utilità  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e funzionalità di Utilità SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Utilizzo di Esplora utilità per gestire Utilità SQL Server](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Risoluzione dei problemi relativi a Utilità SQL Server](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453)  
  
  
