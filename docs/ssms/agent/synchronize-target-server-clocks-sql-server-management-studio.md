---
title: Sincronizzare gli orologi dei server di destinazione (SQL Server Management Studio) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cacbf8f58717dca6613810ab0b90edcca0df4c83
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a>Synchronize Target Server Clocks (SQL Server Management Studio)
In questo argomento viene descritto come sincronizzare gli orologi dei server di destinazione in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] con l'orologio del server master tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)]. La sincronizzazione di questi orologi di sistema supporta le pianificazioni dei processi.  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per sincronizzare gli orologi dei server di destinazione utilizzando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-synchronize-target-server-clocks"></a>Per sincronizzare gli orologi dei server di destinazione  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server di cui si desidera sincronizzare gli orologi del server di destinazione con l'orologio del server master.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, scegliere **Amministrazione multiserver**e selezionare **Gestione server di destinazione**.  
  
3.  Nella finestra di dialogo **Gestione server di destinazione** , fare clic su **Invia istruzioni**.  
  
4.  Nell'elenco **Tipo istruzione** selezionare **Sincronizza orologi**.  
  
5.  In **Destinatari**eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Tutti i server di destinazione** per sincronizzare gli orologi di tutti i server di destinazione con l'orologio del server master.  
  
    -   Fare clic su **Solo i server di destinazione** seguenti per sincronizzare gli orologi di alcuni server e quindi selezionare ogni server di destinazione di cui si desidera sincronizzare l'orologio con quello del server master.  
  
6.  Al termine, fare clic su **OK**.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-synchronize-target-server-clocks"></a>Per sincronizzare gli orologi dei server di destinazione  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_resync_targetserver (Transact-SQL)](http://msdn.microsoft.com/en-us/40e44df7-d3e3-44ee-b149-08aba629a21f).  
  

