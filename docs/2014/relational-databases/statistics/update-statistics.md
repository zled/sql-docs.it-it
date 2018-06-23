---
title: Aggiornare le statistiche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-statistics
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- updating statistics
- statistics [SQL Server], updating
ms.assetid: 4b97c0b4-03ff-4cfb-9c3f-3b33290b7a2c
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7de18c4a939daf93aa37764b41e7b5df24a26f18
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166565"
---
# <a name="update-statistics"></a>Aggiorna statistiche
  È possibile aggiornare le statistiche di ottimizzazione delle query per una tabella o una vista indicizzata in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per impostazione predefinita, tramite Query Optimizer vengono già aggiornate le statistiche nel modo necessario per migliorare il piano di query. In alcuni casi, è possibile migliorare le prestazioni di esecuzione delle query utilizzando UPDATE STATISTICS o la stored procedure `sp_updatestats` per aggiornare le statistiche con una maggiore frequenza rispetto agli aggiornamenti predefiniti.  
  
 Sebbene consenta di garantire che le query vengano compilate con statistiche aggiornate, l'aggiornamento delle statistiche causa la ricompilazione delle query. Si consiglia di non aggiornare le statistiche troppo frequentemente perché è necessario mantenere un equilibrio a livello di prestazioni tra la necessità di migliorare i piani di query e il tempo necessario per la ricompilazione delle query. Tale equilibrio dipende dall'applicazione in uso. Per le operazioni UPDATE STATISTICS è possibile usare tempdb per ordinare l'esempio di righe per la compilazione di statistiche.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Aggiornare un oggetto statistiche tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Se si utilizza UPDATE STATISTICS o si apportano modifiche tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], è necessaria l'autorizzazione ALTER per la tabella o la vista. Se si usa `sp_updatestats`, è necessario essere un membro del ruolo predefinito del server **sysadmin** o il proprietario del database (**dbo**).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-update-a-statistics-object"></a>Per aggiornare un oggetto statistiche  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il database in cui si desidera aggiornare la statistica.  
  
2.  Fare clic sul segno più per espandere la cartella **Tabelle** .  
  
3.  Fare clic sul segno più per espandere la tabella in cui si desidera aggiornare la statistica.  
  
4.  Fare clic sul segno più per espandere la cartella **Statistiche** .  
  
5.  Fare clic con il pulsante destro del mouse sull'oggetto che si vuole aggiornare e scegliere **Proprietà**.  
  
6.  Nella finestra di dialogo **Proprietà statistiche -***nome_statistiche* selezionare la casella di controllo **Aggiorna statistiche per le colonne selezionate** e quindi fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-update-a-specific-statistics-object"></a>Per aggiornare un oggetto statistiche specifico  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example updates the statistics for the AK_SalesOrderDetail_rowguid index of the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;   
    GO  
    ```  
  
#### <a name="to-update-all-statistics-in-a-table"></a>Per aggiornare tutte le statistiche in una tabella  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all indexes on the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail;   
    GO  
    ```  
  
 Per altre informazioni, vedere [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).  
  
#### <a name="to-update-all-statistics-in-a-database"></a>Per aggiornare tutte le statistiche in un database  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all tables in the database.   
    EXEC sp_updatestats;  
    ```  
  
 Per altre informazioni, vedere [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).  
  
  
