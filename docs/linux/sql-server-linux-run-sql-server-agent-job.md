---
title: Creare ed eseguire processi di SQL Server in Linux | Documenti Microsoft
description: In questa esercitazione viene illustrato come eseguire il processo di agente SQL Server in Linux.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3ffb76838940f42d7a696e1c17f227517d89012d
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---

# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>Creare ed eseguire processi di SQL Server Agent in Linux
Processi di SQL Server vengono utilizzati per eseguire regolarmente la stessa sequenza di comandi nel database di SQL Server. In questo argomento vengono forniti esempi di come creare processi di SQL Server Agent in Linux tramite Transact-SQL e SQL Server Management Studio (SSMS).

Per i problemi noti con SQL Server Agent in questa versione, vedere il [note sulla versione](sql-server-linux-release-notes.md).

## <a name="prerequisites"></a>Prerequisiti 
Per creare ed eseguire i processi, è innanzitutto necessario installare il servizio SQL Server Agent. Per istruzioni sull'installazione, vedere il [argomento di installazione di SQL Server Agent](sql-server-linux-setup-sql-agent.md).

## <a name="create-a-job-with-transact-sql"></a>Creare un processo con Transact-SQL

I passaggi seguenti forniscono un esempio di come creare un processo di agente SQL Server in Linux con comandi Transact-SQL. Questi processo in questo esempio viene eseguito un backup giornaliero, un database di esempio `SampleDB`. 


> [!TIP]
> È possibile utilizzare qualsiasi client di T-SQL per eseguire questi comandi. In Linux, ad esempio, è possibile utilizzare [sqlcmd](sql-server-linux-setup-tools.md) o [codice di Visual Studio](sql-server-linux-develop-use-vscode.md). Da un Server remoto di Windows, è anche possibile eseguire query in SQL Server Management Studio (SSMS) o usare l'interfaccia dell'interfaccia utente per la gestione dei processi, descritto nella sezione successiva.

1. **Creare il processo**. L'esempio seguente usa [sp_add_job](https://msdn.microsoft.com/library/ms182079.aspx) per creare un processo denominato `Daily AdventureWorks Backup`.

    ```tsql
     -- Adds a new job executed by the SQLServerAgent service 
     -- called 'Daily SampleDB Backup'  
     CREATE DATABASE SampleDB
     USE msdb ;  
     GO  
     EXEC dbo.sp_add_job  
         @job_name = N'Daily SampleDB Backup' ;  
     GO

    ```

2. **Aggiungere uno o più passaggi di processo**. Il seguente script Transact-SQL Usa [sp_add_jobstep](https://msdn.microsoft.com/library/ms187358.aspx) per creare un passaggio di processo che consente di creare un backup del `AdventureWlorks2014` database.

    ```tsql
    -- Adds a step (operation) to the job  
    EXEC sp_add_jobstep  
      @job_name = N'Daily SampleDB Backup',  
      @step_name = N'Backup database',  
      @subsystem = N'TSQL',  
      @command = N'BACKUP DATABASE SampleDB TO DISK = \
      N''/var/opt/mssql/data/SampleDB.bak'' WITH NOFORMAT, NOINIT, \
              NAME = ''SampleDB-full'', SKIP, NOREWIND, NOUNLOAD, STATS = 10',   
      @retry_attempts = 5,  
      @retry_interval = 5 ;  
    GO
    ```

3. **Creare una pianificazione di processo**. Questo esempio viene utilizzato [sp_add_schedule](https://msdn.microsoft.com/library/ms366342.aspx) per creare una pianificazione giornaliera per il processo.

    ```tsql
    -- Creates a schedule called 'Daily'  
    EXEC dbo.sp_add_schedule  
     @schedule_name = N'Daily SampleDB',  
     @freq_type = 4,  
     @freq_interval = 1,
     @active_start_time = 233000 ;  
   USE msdb ;  
   GO
    ```

4. **Collegare la pianificazione del processo al processo**. Utilizzare [sp_attach_schedule](https://msdn.microsoft.com/library/ms186766.aspx) per collegare la pianificazione del processo al processo.

    ```tsql
    -- Sets the 'Daily' schedule to the 'Daily AdventureWorks Backup' Job  
    EXEC sp_attach_schedule  
     @job_name = N'Daily SampleDB Backup',  
     @schedule_name = N'Daily SampleDB';  
    GO
    ```

5. **Assegnare il processo a un server di destinazione**. Assegnare il processo a un server di destinazione con [sp_add_jobserver](https://msdn.microsoft.com/library/ms178625.aspx). In questo esempio, il server locale è la destinazione.

    ```tsql
    EXEC dbo.sp_add_jobserver  
     @job_name = N'Daily SampleDB Backup',  
     @server_name = N'(LOCAL)';  
    GO
    ```
6. **Avviare il processo**. 

    ```tsql
    EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
    GO
    ```
## <a name="create-a-job-with-ssms"></a>Creare un processo con SQL Server Management Studio

È anche possibile creare e gestire i processi in modalità remota tramite SQL Server Management Studio (SSMS) in Windows.

1. **Avviare SQL Server Management Studio in Windows e connettersi all'istanza del Server SQL di Linux.** Per ulteriori informazioni, vedere [gestire SQL Server in Linux con SSMS](sql-server-linux-develop-use-ssms.md).

1. **Creare un nuovo database denominato SampleDB**.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

2. **Verificare che SQL Agent è stato installato e configurato correttamente.** Cercare sul segno più accanto a SQL Server Agent in Esplora oggetti. Se non è installato SQL Server Agent, vedere [installare SQL Server Agent in Linux](sql-server-linux-setup-sql-agent.md).

    ![Verificare che sia stato installato SQL Server Agent](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)


3. **Creare un nuovo processo.**

    ![Creare un nuovo processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)


4. **Assegnare il processo di un nome e il passaggio di processo di creazione.**

    ![Creare un passaggio di processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)


5. **Specificare il sottosistema che si desidera utilizzare e che il passaggio del processo deve essere eseguita.**

    ![Sottosistema di processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

    ![Azione del passaggio processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

6. **Creare una nuova pianificazione processo.**

    ![Pianificazioni processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)
  
    ![Pianificazioni processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

7. **Avviare il processo.**

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sulla creazione e gestione di processi di SQL Server Agent, vedere [SQL Server Agent](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent).

