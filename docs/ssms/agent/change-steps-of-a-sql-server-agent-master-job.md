---
title: Modificare i passaggi di un processo master di SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f1a0ee6-49ff-4080-94ca-d661daeff2a6
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 599646177ad22cb5131b0c57dc07206db66153a2
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="change-steps-of-a-sql-server-agent-master-job"></a>Change Steps of a SQL Server Agent Master Job
In questo argomento verrà descritto come apportare modifiche ai passaggi di un processo master di SQL Server Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per apportare modifiche ai passaggi di un processo master di SQL Server Agent tramite:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
Un processo master di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent non può essere destinato sia a server locali sia a server remoti.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
È possibile modificare solo i processi di cui si è proprietari, a meno che non si appartenga al ruolo predefinito del server **sysadmin** . Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a>Per apportare modifiche ai passaggi di un processo master di SQL Server Agent  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server contenente il processo in cui si desidera modificare passaggi.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic sul segno più per espandere la cartella **Processi** .  
  
4.  Fare clic con il pulsante destro del mouse sul processo in cui si intende modificare passaggi e scegliere **Proprietà**.  
  
5.  In **Seleziona una pagina***nella finestra di dialogo* Proprietà processo – **nome_processo**selezionare **Passaggi**.  
  
6.  Fare clic su **Modifica** per aprire la finestra di dialogo **Proprietà passaggio processo –***nome_passaggio_processo*. Per altre informazioni sulle opzioni disponibili nella finestra di dialogo, vedere [Proprietà passaggio processo - nuovo passaggio di processo &#40;pagina generale &#41;](../../ssms/agent/job-step-properties-new-job-step-general-page.md) e [Proprietà passaggio processo - nuovo passaggio di processo &#40;pagina avanzate&#41;](../../ssms/agent/job-step-properties-new-job-step-advanced-page.md).  
  
7.  Al termine, fare clic su **OK**.  
  
8.  Nella finestra di dialogo **Proprietà processo–***nome_processo* scegliere **OK**.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a>Per apportare modifiche ai passaggi di un processo master di SQL Server Agent  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- changes the number of retry attempts for the first step
    -- of the Weekly Sales Data Backup job.   
    -- After running this example, the number of retry attempts is 10   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1,  
        @retry_attempts = 10 ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_update_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/e158802c-c347-4a5d-bf75-c03e5ae56e6b).  
  

