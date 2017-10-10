---
title: Pianificare l'esecuzione del pacchetto SSIS in Azure | Documenti Microsoft
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: a3ecfce9a6adac332b72033955ba51271ed8197b
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Pianificare l'esecuzione di un pacchetto SSIS in Azure
È possibile pianificare l'esecuzione di pacchetti archiviati nel database del catalogo di SSISDB in un server di Database SQL di Azure scegliendo una delle opzioni di pianificazione seguenti:
-   [SQL Server Agent](#agent)
-   [Processi elastici di Database SQL](#elastic)
-   [L'attività di Azure Data Factory Stored Procedure SQL Server](#sproc)

## <a name="agent"></a>Pianificare un pacchetto con SQL Server Agent

### <a name="prerequisite"></a>Prerequisiti

È possibile utilizzare SQL Server Agent in locale per pianificare l'esecuzione di pacchetti archiviati in un server di Database SQL di Azure, è necessario aggiungere il server di Database SQL come un server collegato. Per altre informazioni, vedere [creare server collegati](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) e [server collegati](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Creare un processo di SQL Server Agent

Per pianificare un pacchetto con SQL Server Agent in locale, creare un processo con un passaggio di processo che chiama il catalogo SSIS stored procedure `[catalog].[create_execution]` e quindi `[catalog].[start_execution]`. Per altre informazioni, vedere [processi di SQL Server Agent per i pacchetti](../packages/sql-server-agent-jobs-for-packages.md).

1.  In SQL Server Management Studio, connettersi al database di SQL Server locale in cui si desidera creare il processo.

2.  Fare clic su di **SQL Server Agent** nodo, seleziona **New**e quindi selezionare **processo** per aprire la **nuovo processo** la finestra di dialogo.

3.  Nel **nuovo processo** la finestra di dialogo, seleziona il **passaggi** pagina e quindi selezionare **New** per aprire la **nuovo passaggio di processo** la finestra di dialogo.

4.  Nel **nuovo passaggio di processo** nella finestra di dialogo `SSISDB` come il **Database.**

5.  Nella casella comando, immettere uno script Transact-SQL simile allo script illustrato nell'esempio seguente:

    ```sql
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
    @folder_name=N'folderName', @project_name=N'projectName', 
    @package_name=N'packageName', @use32bitruntime=0, 
    @runincluster=1, @useanyworker=1, @execution_id=@exe_id OUTPUT 
 
    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id

    GO
    ```

6.  Completare la configurazione e pianificazione del processo.

## <a name="elastic"></a>Pianificare un pacchetto con i processi di SQL Database elastico

Per ulteriori informazioni sui processi elastici nel Database SQL, vedere [i database di gestione dei cloud di scalabilità orizzontale](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Prerequisiti

È possibile utilizzare processi elastici per pianificare i pacchetti SSIS archiviati nel database del catalogo SSISDB in un server di Database SQL di Azure, è necessario eseguire le operazioni seguenti:

1.  Installare e configurare i componenti di processi di Database elastico. Per altre informazioni, vedere [Panoramica di processi di installazione di Database elastico](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Creare le credenziali con ambito database processi è possono utilizzare per inviare comandi al database del catalogo SSIS. Per altre informazioni, vedere [creare CREDENZIALI con ambito DATABASE (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Creare un processo elastico

Creare il processo tramite uno script Transact-SQL simile allo script illustrato nell'esempio seguente:

```sql
-- Create Elastic Jobs target group 
EXEC jobs.sp_add_target_group 'TargetGroup' 
? 
-- Add Elastic Jobs target group member 
EXEC jobs.sp_add_target_group_member @target_group_name='TargetGroup', 
    @target_type='SqlDatabase', @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB' 
? 
-- Add a job to schedule SSIS package execution
EXEC jobs.sp_add_job @job_name='ExecutePackageJob', @description='Description', 
    @schedule_interval_type='Minutes', @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXEC jobs.sp_add_jobstep @job_name='ExecutePackageJob', 
    @command=N'DECLARE @exe_id bigint 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runincluster=1, @useanyworker=1, 
            @execution_id=@exe_id OUTPUT         
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0', 
    @credential_name='YourDBScopedCredentials', 
    @target_group_name='TargetGroup' 

-- Enable the job schedule 
EXEC jobs.sp_update_job @job_name='ExecutePackageJob', @enabled=1, 
    @schedule_interval_type='Minutes', @schedule_interval_count=60 
```

## <a name="sproc"></a>Pianificare un pacchetto con l'attività di Azure Data Factory Stored Procedure SQL Server

Per pianificare un pacchetto con l'attività di Azure Data Factory Stored Procedure SQL Server, eseguire le operazioni seguenti:
1.  Creare una Data Factory.
2.  Creare un servizio collegato per il Database SQL che ospita il database SSISDB.
3.  Creare un set di dati di output che controlla la pianificazione.
4.  Creare una pipeline di Data Factory che usa l'attività di Stored Procedure di SQL Server per eseguire il pacchetto SSIS.

In questa sezione viene fornita una panoramica dei passaggi. Un'esercitazione di Data Factory completa non rientra nell'ambito di questo articolo. Per altre informazioni, vedere [attività di SQL Server Stored Procedure](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-stored-proc-activity).

### <a name="created-a-linked-service-for-the-sql-database-that-hosts-ssisdb"></a>Creare un servizio collegato per il Database SQL che ospita il database SSISDB
Il servizio collegato consente a Data Factory di connettersi a SSISDB.

```json
{
    "name": "AzureSqlLinkedService",
    "properties": {
        "description": "",
        "type": "AzureSqlDatabase",
        "typeProperties": {
            "connectionString": "Data Source = tcp: YourSQLDBServer.database.windows.net, 1433; Initial Catalog = SSISDB; User ID = YourUsername; Password = YourPassword; Integrated Security = False; Encrypt = True; Connect Timeout = 30 "
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
### <a name="create-a-data-factory-pipeline"></a>Creare una pipeline di Data Factory
La pipeline utilizza l'attività di Stored Procedure di SQL Server per eseguire il pacchetto SSIS.

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

Non è necessario creare una nuova stored procedure per incapsulare i comandi Transact-SQL necessari per creare e avviare l'esecuzione del pacchetto SSIS. È possibile fornire lo script come valore della `stmt` parametro nell'esempio precedente JSON. Di seguito è riportato uno script di esempio:

```sql
-- T-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures
DECLARE @return_value INT,@exe_id BIGINT,@err_msg NVARCHAR(150)

EXEC @return_value=[SSISDB].[catalog].[create_execution] @folder_name=N'folderName', @project_name=N'projectName', @package_name=N'packageName', @use32bitruntime=0, @runincluster=1,@useanyworker=1, @execution_id=@exe_id OUTPUT
                                                         
EXEC [SSISDB].[catalog].[start_execution] @execution_id=@exe_id,@retry_count=0
-- To synchronize SSIS package execution, poll package execution status
-- created (1)
-- running (2)
-- canceled (3)
-- failed (4)
-- pending (5)
-- ended unexpectedly (6)
-- succeeded (7)
-- stopping (8)
-- completed (9) 
                                          
WHILE(SELECT [status]
      FROM [SSISDB].[catalog].[executions]
      WHERE execution_id=@exe_id) NOT IN(3,4,6,7,9)
BEGIN
    WAITFOR DELAY '00:00:01';
END

-- Raise an error for unsuccessful package execution
IF(SELECT [status]
   FROM [SSISDB].[catalog].[executions]
   WHERE execution_id=@exe_id)<>7
BEGIN
    SET @err_msg=N'Your package execution did not succeed for execution ID: '+CAST(@exe_id AS NVARCHAR(20))
    RAISERROR(@err_msg,15,1)
END
GO
```

Per ulteriori informazioni sul codice in questo script, vedere [distribuire ed eseguire pacchetti SSIS utilizzando Stored procedure](../packages/deploy-integration-services-ssis-projects-and-packages.md#deploy-and-execute-ssis-packages-using-stored-procedures).

## <a name="next-steps"></a>Passaggi successivi
Per ulteriori informazioni su SQL Server Agent, vedere [processi di SQL Server Agent per i pacchetti](../packages/sql-server-agent-jobs-for-packages.md).

Per ulteriori informazioni sui processi elastici nel Database SQL, vedere [i database di gestione dei cloud di scalabilità orizzontale](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview).
