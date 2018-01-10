---
title: Pianificare l'esecuzione del pacchetto SSIS in Azure | Microsoft Docs
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26160f982982b1a8163662f57cb317e7252ab0e4
ms.sourcegitcommit: 6e016a4ffd28b09456008f40ff88aef3d911c7ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2017
---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Pianificare l'esecuzione di un pacchetto SSIS in Azure
È possibile pianificare l'esecuzione dei pacchetti archiviati nel database del catalogo SSISDB in un server di database SQL di Azure scegliendo una delle opzioni di pianificazione seguenti:
-   [SQL Server Agent](#agent)
-   [Processi elastici del database SQL](#elastic)
-   [Attività stored procedure di SQL Server di Azure Data Factory](#sproc)

## <a name="agent"></a> Pianificare un pacchetto con SQL Server Agent

### <a name="prerequisite"></a>Prerequisiti

Prima di usare SQL Server Agent in locale per pianificare l'esecuzione di pacchetti archiviati in un server di database SQL di Azure, è necessario aggiungere il server di database SQL come server collegato. Per altre informazioni, vedere [Creazione di server collegati](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) e [Server collegati](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Creare un processo di SQL Server Agent

Per pianificare un pacchetto con SQL Server Agent in locale, creare un processo con un passaggio di processo che chiami le stored procedure del catalogo SSIS `[catalog].[create_execution]` e quindi `[catalog].[start_execution]`. Per altre informazioni, vedere [Processi di SQL Server Agent per i pacchetti](../packages/sql-server-agent-jobs-for-packages.md).

1.  In SQL Server Management Studio connettersi al database di SQL Server locale in cui si vuole creare il processo.

2.  Fare clic con il pulsante destro del mouse sul nodo **SQL Server Agent**, selezionare **Nuovo** e quindi selezionare **Processo** per aprire la finestra di dialogo **Nuovo processo**.

3.  Nella finestra di dialogo **Nuovo processo** selezionare la pagina **Passaggi** e quindi selezionare **Nuovo** per aprire la finestra di dialogo **Nuovo passaggio di processo**.

4.  Nella finestra di dialogo **Nuovo passaggio di processo** selezionare `SSISDB` come **Database.**

5.  Nel campo del comando immettere uno script Transact-SQL simile allo script riportato nell'esempio seguente:

    ```sql
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
    @folder_name=N'folderName', @project_name=N'projectName', 
    @package_name=N'packageName', @use32bitruntime=0, 
    @runinscaleout=1, @useanyworker=1, @execution_id=@exe_id OUTPUT 
 
    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id

    GO
    ```

6.  Completare la configurazione e la pianificazione del processo.

## <a name="elastic"></a> Pianificare un pacchetto con i processi elastici del database SQL

Per altre informazioni sui processi elastici del database SQL, vedere [Gestione dei database cloud con scalabilità orizzontale](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Prerequisites

Per poter usare i processi elastici per pianificare i pacchetti SSIS archiviati nel database del catalogo SSISDB in un server di database SQL di Azure, è necessario eseguire queste operazioni:

1.  Installare e configurare i componenti dei processi di database elastico. Per altre informazioni, vedere [Installazione dei processi di database elastico (panoramica)](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Creare le credenziali con ambito database che i processi possono usare per inviare comandi al database del catalogo SSIS. Per altre informazioni, vedere [CREARE le CREDENZIALI nell'ambito del DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Creare un processo elastico

Creare il processo usando uno script Transact-SQL simile allo script riportato nell'esempio seguente:

```sql
-- Create Elastic Jobs target group 
EXEC jobs.sp_add_target_group 'TargetGroup' 

-- Add Elastic Jobs target group member 
EXEC jobs.sp_add_target_group_member @target_group_name='TargetGroup', 
    @target_type='SqlDatabase', @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB' 

-- Add a job to schedule SSIS package execution
EXEC jobs.sp_add_job @job_name='ExecutePackageJob', @description='Description', 
    @schedule_interval_type='Minutes', @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXEC jobs.sp_add_jobstep @job_name='ExecutePackageJob', 
    @command=N'DECLARE @exe_id bigint 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runinscaleout=1, @useanyworker=1, 
            @execution_id=@exe_id OUTPUT         
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0', 
    @credential_name='YourDBScopedCredentials', 
    @target_group_name='TargetGroup' 

-- Enable the job schedule 
EXEC jobs.sp_update_job @job_name='ExecutePackageJob', @enabled=1, 
    @schedule_interval_type='Minutes', @schedule_interval_count=60 
```

## <a name="sproc"></a> Pianificare un pacchetto con l'attività stored procedure di SQL Server di Azure Data Factory

Per informazioni su come pianificare un pacchetto SSIS usando l'attività della stored procedure di Azure Data Factory, vedere gli articoli seguenti:

-   Per Data Factory versione 2: [Richiamare un pacchetto SSIS usando l'attività della stored procedure in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity)

-   Per Data Factory versione 1: [Richiamare un pacchetto SSIS usando l'attività della stored procedure in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/v1/how-to-invoke-ssis-package-stored-procedure-activity)

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su SQL Server Agent, vedere [Processi di SQL Server Agent per i pacchetti](../packages/sql-server-agent-jobs-for-packages.md).

Per altre informazioni sui processi elastici del database SQL, vedere [Gestione dei database cloud con scalabilità orizzontale](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).
