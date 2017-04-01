---
title: "Eseguire pacchetti nel servizio di scalabilit&#224; orizzontale di Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c2f4cd7-9c47-416d-bb1e-40acc3e05342
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Eseguire pacchetti nel servizio di scalabilit&#224; orizzontale di Integration Services (SSIS)
Dopo aver distribuito i pacchetti nel server di Integration Services, è possibile eseguirli nel servizio di scalabilità orizzontale.

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>Eseguire i pacchetti con la finestra di dialogo **Esegui pacchetto in scalabilità orizzontale** 

1. ### <a name="open-the-execute-package-in-scale-out-dialog-box"></a>Aprire la finestra di dialogo Execute Package In Scale Out (Esegui pacchetto nel servizio di scalabilità orizzontale) ###
    In [!INCLUDE[ssManStudioFull_md](../includes/ssmanstudiofull-md.md)] connettersi al server di Integration Services. In Esplora oggetti espandere l'albero per visualizzare il nodo in **Cataloghi di Integration Services**. Fare clic con il pulsante destro del mouse sul nodo **SSISDB**, sul progetto o sul pacchetto che si vuole eseguire e quindi fare clic su **Execute in Scale Out** (Esegui nel servizio di scalabilità orizzontale).
2. ### <a name="select-packages-and-set-the-options"></a>Selezionare i pacchetti e impostare le opzioni ###
    Nella pagina **Selezione pacchetti** selezionare più pacchetti per eseguire e impostare ambiente, parametri, gestori di connessioni e opzioni avanzate per ogni pacchetto. Fare clic su un pacchetto per impostare queste opzioni.
    
    Nella scheda **Avanzate** impostare un'opzione per Scale Out denominata **Numero di tentativi**. Questa opzione consente di impostare il numero di tentativi di esecuzione di un pacchetto in caso di errore.
3. ### <a name="select-machines"></a>Selezionare i computer ###
    Nella pagina **Machine Selection** (Selezione computer) selezionare i computer del ruolo di lavoro di scalabilità orizzontale per l'esecuzione dei pacchetti. Per impostazione predefinita, tutti i computer possono eseguire i pacchetti. 

   > [!NOTE]
> I pacchetti vengono eseguiti con le credenziali degli account utente del servizio Ruolo di lavoro di scalabilità orizzontale, visualizzati nella pagina **Machine Selection** (Selezione computer). Per impostazione predefinita, l'account è NT Service\SSISScaleOutWorker140. È possibile modificarlo in base ai propri account di laboratorio.

4. ### <a name="run-the-packages-and-view-reports"></a>Eseguire i pacchetti e visualizzare i report 
    Fare clic su **OK** per avviare le esecuzioni dei pacchetti. Per visualizzare il report di esecuzione relativo a un pacchetto, fare clic con il pulsante destro del pacchetto in Esplora oggetti, fare clic su **Report**, **Tutte le esecuzioni** e trovare l'esecuzione.
    
    
## <a name="run-packages-with-stored-procedures"></a>Eseguire i pacchetti con le stored procedure

1. ### <a name="create-executions"></a>Creare esecuzioni ###
    Chiamare [catalog].[create_execution] per ogni pacchetto. Impostare il parametro **@runincluster** su True. Se non tutti i computer del ruolo di lavoro di scalabilità orizzontale sono autorizzati a eseguire il pacchetto, impostare il parametro **@useanyworker** su False.   
2. ### <a name="set-execution-parameters"></a>Impostare i parametri di esecuzione ###
    Chiamare [catalog].[set_execution_parameter_value] per ogni esecuzione.
3. ### <a name="set-scale-out-workers"></a>Impostare i ruoli di lavoro di scalabilità orizzontale ###
    Chiamare [catalog].[add_execution_worker]. Se qualsiasi computer può eseguire il pacchetto, non è necessario chiamare questa stored procedure. 
4. ### <a name="start-executions"></a>Avviare le esecuzioni ###
    Chiamare [catalog].[start_execution]. Impostare il parametro **@retry_count** per impostare il numero di tentativi di esecuzione di un pacchetto in caso di errore.
    
    ### <a name="example"></a>Esempio  ###  
    L'esempio seguente esegue due pacchetti, package1.dtsx e package2.dtsx, nel servizio di scalabilità orizzontale con un ruolo di lavoro di scalabilità orizzontale.  
    ```
    Declare @execution_id bigint
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder1', @project_name=N'project1', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runincluster=True
    Select @execution_id
    DECLARE @var0 smallint = 1
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
    EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
    EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
    GO

    Declare @execution_id bigint
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package2.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder2', @project_name=N'project2', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runincluster=True
    Select @execution_id
    DECLARE @var0 smallint = 1
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
    EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
    EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
    GO
    ```


## <a name="permissions"></a>Permissions
L'esecuzione dei pacchetti nel servizio di scalabilità orizzontale richiede una delle autorizzazioni seguenti:

-   Appartenenza al ruolo del database **ssis_admin**  

-   Appartenenza al ruolo del database **ssis_cluster_executor**  
  
-   Appartenenza al ruolo del server **sysadmin**  
    