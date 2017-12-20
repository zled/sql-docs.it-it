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
ms.openlocfilehash: d0b8dbc635523b33a480ad887b73d9f395d71c8d
ms.sourcegitcommit: ffa4ce9bd71ecf363604966c20cbd2710d029831
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
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

### <a name="prerequisites"></a>Prerequisiti

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

> [!IMPORTANT]
> Usare gli script JSON dell'esempio seguente con l'attività stored procedure di Azure Data Factory versione 1.

Per pianificare un pacchetto con l'attività stored procedure di SQL Server di Azure Data Factory, eseguire queste operazioni:

1.  Creare una data factory.

2.  Creare un servizio collegato per il database SQL che ospita SSISDB.

3.  Creare un set di dati di output che controlla la pianificazione.

4.  Creare una pipeline della data factory che usa l'attività stored procedure di SQL Server per eseguire il pacchetto SSIS.

Questa sezione contiene una panoramica dei vari passaggi. Un'esercitazione completa su Data Factory non rientra nell'ambito di questo articolo. Per altre informazioni, vedere [Attività stored procedure di SQL Server](https://docs.microsoft.com/azure/data-factory/data-factory-stored-proc-activity).

Se un'esecuzione pianificata ha esito negativo e l'attività stored procedure del file di definizione dell'applicazione (ADF) fornisce un ID per l'esecuzione non riuscita, cercare nel report sull'esecuzione tale ID in SSMS nel catalogo SSIS.

### <a name="created-a-linked-service-for-the-sql-database-that-hosts-ssisdb"></a>Creare un servizio collegato per il database SQL che ospita SSISDB
Il servizio collegato consente a Data Factory di connettersi a SSISDB.

```json
{
    "name": "AzureSqlLinkedService",
    "properties": {
        "description": "",
        "type": "AzureSqlDatabase",
        "typeProperties": {
            "connectionString": "Data Source = tcp: YourSQLDBServer.database.windows.net, 1433; Initial Catalog = SSISDB; User ID = YourUsername; Password = YourPassword; Integrated Security = False; Encrypt = True; Connect Timeout = 30"
        }
    }
}
```

### <a name="create-an-output-dataset"></a>Creare un set di dati di output
Il set di dati di output contiene le informazioni di pianificazione.

```json
{
    "name": "sprocsampleout",
    "properties": {
        "type": "AzureSqlTable",
        "linkedServiceName": "AzureSqlLinkedService",
        "typeProperties": {
            "tableName": "sampletable"
        },
        "availability": {
            "frequency": "Hour",
            "interval": 1
        }
    }
}
```
### <a name="create-a-data-factory-pipeline"></a>Creare una pipeline della data factory
La pipeline usa l'attività stored procedure di SQL Server per eseguire il pacchetto SSIS.

```json
{
    "name": "SprocActivitySamplePipeline",
    "properties": {
        "activities": [{
            "name": "SprocActivitySample",
            "type": "SqlServerStoredProcedure",
            "typeProperties": {
                "storedProcedureName": "sp_executesql",
                "storedProcedureParameters": {
                    "stmt": "Transact-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures"
                }
            },
            "outputs": [{
                "name": "sprocsampleout"
            }],
            "scheduler": {
                "frequency": "Hour",
                "interval": 1
            }
        }],
        "start": "2017-10-01T00:00:00Z",
        "end": "2017-10-01T05:00:00Z",
        "isPaused": false
    }
}
```

Non è necessario creare una nuova stored procedure per incapsulare i comandi Transact-SQL richiesti per creare e avviare l'esecuzione del pacchetto SSIS. È possibile specificare l'intero script come il valore del parametro `stmt` nell'esempio di JSON precedente. Di seguito è riportato un esempio di script:

```sql
-- T-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures
DECLARE @return_value INT,@exe_id BIGINT,@err_msg NVARCHAR(150)

-- Create the exectuion
EXEC @return_value=[SSISDB].[catalog].[create_execution] @folder_name=N'folderName', @project_name=N'projectName', @package_name=N'packageName', @use32bitruntime=0, @runinscaleout=1,@useanyworker=1, @execution_id=@exe_id OUTPUT

-- To synchronize SSIS package execution, set the SYNCHRONIZED execution parameter
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @exe_id, @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

-- Start the execution                                                         
EXEC [SSISDB].[catalog].[start_execution] @execution_id=@exe_id,@retry_count=0
                                          
-- Raise an error for unsuccessful package execution
-- Execution status values include the following:
-- created (1)
-- running (2)
-- canceled (3)
-- failed (4)
-- pending (5)
-- ended unexpectedly (6)
-- succeeded (7)
-- stopping (8)
-- completed (9) 
IF(SELECT [status]
   FROM [SSISDB].[catalog].[executions]
   WHERE execution_id=@exe_id)<>7
BEGIN
    SET @err_msg=N'Your package execution did not succeed for execution ID: ' + CAST(@exe_id AS NVARCHAR(20))
    RAISERROR(@err_msg,15,1)
END
GO
```

Per fornire lo script SQL visualizzato sotto come valore del parametro `stmt`, è in genere necessario includere l'intero script in una singola riga, come illustrato nell'esempio seguente. Lo [standard JSON](https://json.org/) non supporta i caratteri di controllo, incluso il carattere di controllo di nuova riga `\n` usato in altri linguaggi per separare le righe in una stringa con più righe.

```json
{
    "name": "SprocActivitySamplePipeline",
    "properties": {
        "activities": [
            {
                "type": "SqlServerStoredProcedure",
                "typeProperties": {
                    "storedProcedureName": "sp_executesql",
                    "storedProcedureParameters": {
                        "stmt": "DECLARE @return_value INT, @exe_id BIGINT, @err_msg NVARCHAR(150)    EXEC @return_value=[SSISDB].[catalog].[create_execution] @folder_name=N'test', @project_name=N'TestProject', @package_name=N'STestPackage.dtsx', @use32bitruntime=0, @runinscaleout=1, @useanyworker=1, @execution_id=@exe_id OUTPUT    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @exe_id, @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1    EXEC [SSISDB].[catalog].[start_execution] @execution_id=@exe_id, @retry_count=0    IF(SELECT [status] FROM [SSISDB].[catalog].[executions] WHERE execution_id=@exe_id)<>7 BEGIN SET @err_msg=N'Your package execution did not succeed for execution ID: ' + CAST(@exe_id AS NVARCHAR(20)) RAISERROR(@err_msg,15,1) END"
                    }
                },
                "outputs": [
                    {
                        "name": "sprocsampleout"
                    }
                ],
                "scheduler": {
                    "frequency": "Minute",
                    "interval": 15
                },
                "name": "SprocActivitySample"
            }
        ],
        "start": "2017-12-06T12:00:00Z",
        "end": "2017-12-06T12:30:00Z",
        "isPaused": false,
        "hubName": "test_hub",
        "pipelineMode": "Scheduled"
    }
}
```

Per altre informazioni sul codice in questo script, vedere [Distribuire ed eseguire pacchetti SSIS utilizzando le stored procedure](../packages/deploy-integration-services-ssis-projects-and-packages.md#deploy-and-execute-ssis-packages-using-stored-procedures).

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su SQL Server Agent, vedere [Processi di SQL Server Agent per i pacchetti](../packages/sql-server-agent-jobs-for-packages.md).

Per altre informazioni sui processi elastici del database SQL, vedere [Gestione dei database cloud con scalabilità orizzontale](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).
