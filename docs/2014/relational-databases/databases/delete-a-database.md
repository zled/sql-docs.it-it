---
title: Eliminare un database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- database removal [SQL Server], SQL Server Management Studio
- removing databases
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- database removal [SQL Server]
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a98ae854f2608eead7820418eb918fc1ba713aa9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061031"
---
# <a name="delete-a-database"></a>Eliminare un database
  In questo argomento si descrive come eliminare un database definito dall'utente in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Prerequisiti](#Prerequisites)  
  
     [Indicazioni](#Recommendations)  
  
     [Security](#Security)  
  
-   **Per eliminare un database tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Dopo l'eliminazione di un database](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   I database di sistema non possono essere eliminati.  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   Eliminare qualsiasi snapshot di database presente nel database. Per altre informazioni, vedere [Eliminare uno snapshot del database &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).  
  
-   Se il database è coinvolto nel log shipping, rimuovere quest'ultimo.  
  
-   Se il database viene pubblicato per la replica transazionale oppure viene pubblicato o sottoscritto per la replica di tipo merge, rimuovere la replica dal database.  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Valutare l'opportunità di eseguire un backup completo del database. È possibile ricreare un database eliminato solo tramite il ripristino di un backup.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per eseguire DROP DATABASE, un utente deve disporre almeno dell'autorizzazione CONTROL per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-database"></a>Per eliminare un database  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quindi espandere questa istanza.  
  
2.  Espandere **Database**, fare clic con il pulsante destro del mouse sul database che si vuole eliminare e quindi scegliere **Elimina**.  
  
3.  Confermare che è stato selezionato il database corretto, quindi fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-delete-a-database"></a>Per eliminare un database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Nell'esempio si rimuovono i database `Sales` e `NewSales` .  
  
```tsql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="FollowUp"></a> Completamento: Dopo l'eliminazione di un database  
 Eseguire il backup del database **master** . Se è necessario ripristinare il database **master** , per qualsiasi database eliminato dopo l'ultimo backup del database **master** saranno ancora disponibili riferimenti nelle viste del catalogo di sistema, pertanto potranno essere generati messaggi di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
