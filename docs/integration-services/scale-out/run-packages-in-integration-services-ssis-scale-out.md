---
title: "Scalabilità orizzontale eseguire i pacchetti in SQL Server Integration Services (SSIS) | Documenti Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
f1_keywords:
- sql13.ssis.ssms.ispackageexecuteinscaleout.f1
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2c158ae6a711ecb5f5065561c0c8c303e9a09980
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---

# <a name="run-packages-in-integration-services-ssis-scale-out"></a>Eseguire i pacchetti di Integration Services (SSIS) Scale Out
Dopo aver distribuito i pacchetti nel server di Integration Services, è possibile eseguirli nel servizio di scalabilità orizzontale.

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>Eseguire i pacchetti con una finestra di dialogo Esegui pacchetto In Scale Out 

1. Aprire la finestra di dialogo Execute Package In Scale Out (Esegui pacchetto nel servizio di scalabilità orizzontale)

    In [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] connettersi al server di Integration Services. In Esplora oggetti espandere l'albero per visualizzare il nodo in **Cataloghi di Integration Services**. Fare clic con il pulsante destro del mouse sul nodo **SSISDB** , sul progetto o sul pacchetto che si vuole eseguire e quindi fare clic su **Execute in Scale Out**(Esegui nel servizio di scalabilità orizzontale).

2. Selezionare i pacchetti e impostare le opzioni

    Nella pagina **Selezione pacchetti** selezionare più pacchetti per eseguire e impostare ambiente, parametri, gestori di connessioni e opzioni avanzate per ogni pacchetto. Fare clic su un pacchetto per impostare queste opzioni.
    
    Nella scheda **Avanzate** impostare un'opzione per Scale Out denominata **Numero di tentativi**. Questa opzione consente di impostare il numero di tentativi di esecuzione di un pacchetto in caso di errore.

    > [!Note]
    > Il **Dump su errori** opzione ha effetto solo quando l'account che esegue il servizio di scala il lavoro è un amministratore del computer locale.

3. Selezionare i computer

    Nella pagina **Machine Selection** (Selezione computer) selezionare i computer del ruolo di lavoro di scalabilità orizzontale per l'esecuzione dei pacchetti. Per impostazione predefinita, tutti i computer possono eseguire i pacchetti. 

   > [!Note] 
   > I pacchetti vengono eseguiti con le credenziali degli account utente del servizio Ruolo di lavoro di scalabilità orizzontale, visualizzati nella pagina **Machine Selection** (Selezione computer). Per impostazione predefinita, l'account è NT Service\SSISScaleOutWorker140. È possibile modificarlo in base ai propri account di laboratorio.

   >[!WARNING]
   >Attivato da utenti diversi nel processo di lavoro stesso esecuzioni del pacchetto vengono eseguite con lo stesso account. Non sussiste alcun limite di sicurezza tra di essi. 

4. Eseguire i pacchetti e visualizzare i report 

    Fare clic su **OK** per avviare le esecuzioni dei pacchetti. Per visualizzare il report di esecuzione relativo a un pacchetto, fare clic con il pulsante destro del pacchetto in Esplora oggetti, fare clic su **Report**, **Tutte le esecuzioni**e trovare l'esecuzione.
    
## <a name="run-packages-with-stored-procedures"></a>Eseguire i pacchetti con le stored procedure

1. Creare esecuzioni

    Chiamare [catalog].[create_execution] per ogni pacchetto. Impostare il parametro **@runinscaleout** su True. Se non tutti i computer del ruolo di lavoro di scalabilità orizzontale sono autorizzati a eseguire il pacchetto, impostare il parametro **@useanyworker** su False.   

2. Impostare i parametri di esecuzione

    Chiamare [catalog].[set_execution_parameter_value] per ogni esecuzione.

3. Impostare i ruoli di lavoro di scalabilità orizzontale

    Chiamare [catalog].[add_execution_worker]. Se qualsiasi computer può eseguire il pacchetto, non è necessario chiamare questa stored procedure. 

4. Avviare le esecuzioni

    Chiamare [catalog].[start_execution]. Impostare il parametro **@retry_count** per impostare il numero di tentativi di esecuzione di un pacchetto in caso di errore.
    
#### <a name="example"></a>Esempio
L'esempio seguente esegue due pacchetti, package1.dtsx e package2.dtsx, nel servizio di scalabilità orizzontale con un ruolo di lavoro di scalabilità orizzontale.  

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder1', @project_name=N'project1', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runinscaleout=True
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
GO

Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package2.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder2', @project_name=N'project2', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runinscaleout=True
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
GO
```

### <a name="permissions"></a>Permissions
L'esecuzione dei pacchetti nel servizio di scalabilità orizzontale richiede una delle autorizzazioni seguenti:

-   Appartenenza al ruolo del database **ssis_admin**  

-   Appartenenza al ruolo del database **ssis_cluster_executor**  
  
-   Appartenenza al ruolo del server **sysadmin**  

## <a name="set-default-execution-mode"></a>Impostare la modalità di esecuzione predefinito
Per impostare la modalità di esecuzione predefinito per "Scale Out", fare doppio clic su di **SSISDB** nodo in Esplora oggetti di SQL Server Management Studio e selezionare **proprietà**.
Nel **proprietà catalogo** finestra di dialogo, impostare **modalità di esecuzione predefinito a livello di Server** a **orizzontale**.

Dopo questa impostazione, non è necessario specificare il  **@runinscaleout**  parametro per [catalog]. [ create_execution]. Esecuzioni vengono eseguite automaticamente in orizzontale. 

![Modalità file exe](media\exe-mode.PNG)

Per cambiare la modalità di esecuzione predefinito tornare alla modalità non - scalabile, è sufficiente impostare **modalità di esecuzione a livello di Server predefinito** a **Server**.

## <a name="run-package-in-sql-agent-job"></a>Eseguire un pacchetto nel processo dell'agente SQL
Nel processo di Sql agent, è possibile scegliere di eseguire un pacchetto SSIS come un passaggio del processo. Per eseguire il pacchetto in orizzontale, è possibile utilizzare la modalità di esecuzione predefinito precedente. Dopo l'impostazione della modalità di esecuzione predefinito per "Scale Out", verranno eseguiti i pacchetti di processi di Sql agent in orizzontale.
