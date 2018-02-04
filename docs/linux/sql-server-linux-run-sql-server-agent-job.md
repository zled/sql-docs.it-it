---
title: Creare ed eseguire processi di SQL Server in Linux | Documenti Microsoft
description: In questa esercitazione viene illustrato come eseguire il processo di agente SQL Server in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.workload: Inactive
ms.openlocfilehash: 526375f9f9f96c9ea0402dcb84f20a2c214fd13f
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>Creare ed eseguire processi di SQL Server Agent in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Processi di SQL Server vengono utilizzati per eseguire regolarmente la stessa sequenza di comandi nel database di SQL Server. In questa esercitazione fornisce un esempio di come creare un processo di agente SQL Server in Linux tramite Transact-SQL e SQL Server Management Studio (SSMS).

> [!div class="checklist"]
> * Installare SQL Server Agent su Linux
> * Creare un nuovo processo per eseguire i backup giornalieri di database
> * Pianificare ed eseguire il processo
> * Eseguire gli stessi passaggi in SQL Server Management Studio (facoltativo)

Per i problemi noti con SQL Server Agent in Linux, vedere il [note sulla versione](sql-server-linux-release-notes.md).

## <a name="prerequisites"></a>Prerequisiti

Per completare questa esercitazione, sono necessari i seguenti prerequisiti:

* Computer Linux con i seguenti prerequisiti:
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), o [Ubuntu](quickstart-install-connect-ubuntu.md)) con gli strumenti da riga di comando.

I prerequisiti seguenti sono facoltativi:

* Computer Windows con SQL Server Management Studio:
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) per passaggi facoltativi di SQL Server Management Studio.

## <a name="install-sql-server-agent"></a>Installare SQL Server Agent

Per utilizzare SQL Server Agent in Linux, è necessario installare il **mssql-server agent** pacchetto in un computer che dispone già di SQL Server 2017 installato.

1. Installare **mssql-server agent** con il comando appropriato per il sistema operativo Linux.

   | Piattaforma | Comandi di installazione |
   |-----|-----|
   | RHEL | `sudo yum install mssql-server-agent` |
   | SLES | `sudo zypper refresh`<br/>`sudo zypper update mssql-server-agent` |
   | Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server-agent` |

1. Riavviare SQL Server con il comando seguente:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="create-a-sample-database"></a>Creare un database di esempio

Utilizzare la procedura seguente per creare un database di esempio denominato **SampleDB**. Questo database viene utilizzato per il processo di backup giornaliero.

1. Nel computer Linux, aprire una sessione terminal bash.

1. Utilizzare **sqlcmd** per l'esecuzione di Transact-SQL **CREATE DATABASE** comando.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'CREATE DATABASE SampleDB'
   ```

1. Verificare che il database viene creato elencando i database nel server.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'SELECT Name FROM sys.Databases'
   ```

## <a name="create-a-job-with-transact-sql"></a>Creare un processo con Transact-SQL

La procedura seguente crea un processo di SQL Server Agent in Linux con comandi Transact-SQL. Il processo viene eseguito un backup del database di esempio, giornaliero **SampleDB**.

> [!TIP]
> È possibile utilizzare qualsiasi client di T-SQL per eseguire questi comandi. In Linux, ad esempio, è possibile utilizzare [sqlcmd](sql-server-linux-setup-tools.md) o [codice di Visual Studio](sql-server-linux-develop-use-vscode.md). Da un Server remoto di Windows, è anche possibile eseguire query in SQL Server Management Studio (SSMS) o usare l'interfaccia dell'interfaccia utente per la gestione dei processi, descritto nella sezione successiva.

1. Utilizzare [sp_add_job](../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md) per creare un processo denominato `Daily SampleDB Backup`.

   ```sql
   -- Adds a new job executed by the SQLServerAgent service
   -- called 'Daily SampleDB Backup'
   USE msdb ;
   GO
   EXEC dbo.sp_add_job
      @job_name = N'Daily SampleDB Backup' ;
   GO
   ```

1. Chiamare [sp_add_jobstep](../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md) per creare un passaggio di processo che consente di creare un backup del `SampleDB` database.

   ```sql
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

1. Quindi creare una pianificazione giornaliera per il processo con [sp_add_schedule](../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md).

   ```sql
   -- Creates a schedule called 'Daily'
   EXEC dbo.sp_add_schedule
      @schedule_name = N'Daily SampleDB',
      @freq_type = 4,
      @freq_interval = 1,
      @active_start_time = 233000 ;
   USE msdb ;
   GO
   ```

1. Collegare la pianificazione del processo per il processo con [sp_attach_schedule](../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md).

   ```sql
   -- Sets the 'Daily' schedule to the 'Daily SampleDB Backup' Job
   EXEC sp_attach_schedule
      @job_name = N'Daily SampleDB Backup',
      @schedule_name = N'Daily SampleDB';
   GO
   ```

1. Utilizzare [sp_add_jobserver](../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md) per assegnare il processo a un server di destinazione. In questo esempio, la destinazione è il server locale.

   ```sql
   EXEC dbo.sp_add_jobserver
      @job_name = N'Daily SampleDB Backup',
      @server_name = N'(LOCAL)';
   GO
   ```
1. Avviare il processo con [sp_start_job](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).

   ```sql
   EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
   GO
   ```

## <a name="create-a-job-with-ssms"></a>Creare un processo con SQL Server Management Studio

È anche possibile creare e gestire i processi in modalità remota tramite SQL Server Management Studio (SSMS) in Windows.

1. Avviare SQL Server Management Studio in Windows e connettersi all'istanza del Server SQL di Linux. Per ulteriori informazioni, vedere [gestire SQL Server in Linux con SSMS](sql-server-linux-develop-use-ssms.md).

1. Verificare che è stato creato un database di esempio denominato **SampleDB**.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

1. Verificare che SQL Agent sia stata [installato](sql-server-linux-setup-sql-agent.md) e configurato correttamente. Cercare sul segno più accanto a SQL Server Agent in Esplora oggetti. Se SQL Server Agent non è abilitato, provare a riavviare il **mssql server** servizio su Linux.

   ![Verificare che sia stato installato SQL Server Agent](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)

1. Creare un nuovo processo.

   ![Creare un nuovo processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)

1. Assegnare il processo di un nome e il passaggio di processo di creazione.

   ![Creare un passaggio di processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)

1. Specificare il sottosistema che si desidera utilizzare e che il passaggio del processo deve essere eseguita.

   ![Sottosistema di processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

   ![Azione del passaggio processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

1. Creare una nuova pianificazione processo.

   ![Pianificazioni processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)

   ![Pianificazioni processo](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

1. Avviare il processo.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione, si è appreso come:

> [!div class="checklist"]
> * Installare SQL Server Agent su Linux
> * Stored procedure per creare processi di utilizzare Transact-SQL e sistema
> * Creare un processo che esegue i backup giornalieri di database
> * Utilizzare SSMS UI per creare e gestire i processi

Successivamente, è possibile esaminare altre funzionalità per la creazione e la gestione dei processi:

> [!div class="nextstepaction"]
>[Documentazione di SQL Server Agent](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)
