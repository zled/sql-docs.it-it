---
title: Modificare i server di destinazione associati a un processo master di Agent | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 176e73b6-08aa-48ec-b349-e84b431e65cc
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b34863f4a5f1a20d17cc0e87181a5f7d850b64d
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a>Modify the Target Server(s) Associated with a SQL Server Agent Master Job
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento descrive come modificare i server di destinazione associati a un processo master di SQL Server Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per modificare i server di destinazione associati a un processo master di SQL Server Agent tramite:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
Un processo master di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent non può essere destinato sia a server locali sia a server remoti.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
È possibile modificare solo i processi di cui si è proprietari, a meno che non si appartenga al ruolo predefinito del server **sysadmin** . Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a>Per modificare i server di destinazione associati a un processo master di SQL Server Agent  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server contenente il processo in cui si desidera modificare il server di destinazione.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic sul segno più per espandere la cartella **Processi** .  
  
4.  Fare clic con il pulsante destro del mouse sul processo in cui si vuole modificare il server di destinazione e scegliere **Proprietà**.  
  
5.  Nella finestra di dialogo **Proprietà processo –***nome_processo* selezionare **Server di destinazione** in **Seleziona una pagina**. Per altre informazioni sulle opzioni disponibili in questa pagina, vedere [Proprietà processo - nuovo processo &#40;pagina Destinazioni&#41;](../../ssms/agent/job-properties-new-job-targets-page.md).  
  
6.  Al termine, fare clic su **OK**.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-delete-a-target-server-currently-associated-with-a-sql-server-agent-master-job"></a>Per eliminare un server di destinazione attualmente associato a un processo master di SQL Server Agent  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- removes the server SEATTLE2 from processing the Weekly Sales Backupsjob   
    -- assumes that the Weekly Sales Backups job exists  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_delete_jobserver (Transact-SQL)](http://msdn.microsoft.com/en-us/6d63ed32-68cf-4d8f-aa40-05a3826e05b8).  
  
#### <a name="to-associate-a-target-server-with-the-current-sql-server-agent-master-job"></a>Per associare un server di destinazione al processo master corrente di SQL Server Agent  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2   
    -- assumes that the Weekly Sales Backups job already exists and that   
    -- SEATTLE2 is registered as a target server for the current instance  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_add_jobserver (Transact-SQL)](http://msdn.microsoft.com/en-us/485252cc-0081-490a-9bd1-cbbd68eea286).  
  
