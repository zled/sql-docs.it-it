---
title: Catalog. create_execution (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 45d0c2f6-1f38-445f-ac06-e2a01f6ac600
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 7e9d38935a91bba81359bee7fdbd64dba86d0d26
ms.contentlocale: it-it
ms.lasthandoff: 10/20/2017

---
# <a name="catalogcreateexecution-ssisdb-database"></a>catalog.create_execution (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crea un'istanza di esecuzione nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Questa stored procedure utilizza il livello di registrazione server predefinito.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.create_execution [@folder_name = folder_name  
     , [@project_name =] project_name  
     , [@package_name =] package_name  
  [  , [@reference_id =] reference_id ]  
  [  , [@use32bitruntime =] use32bitruntime ] 
  [  , [@runinscaleout =] runinscaleout ]
  [  , [@useanyworker =] useanyworker ] 
     , [@execution_id =] execution_id OUTPUT  
```  
  
## <a name="arguments"></a>Argomenti  
 [@folder_name =] *nome_cartella*  
 Nome della cartella contenente il pacchetto che deve essere eseguito. Il *nome_cartella* è **nvarchar (128)**.  
  
 [@project_name =] *project_name*  
 Nome del progetto contenente il pacchetto che deve essere eseguito. Il *project_name* è **nvarchar (128)**.  
  
 [@package_name =] *nome_pacchetto*  
 Nome del pacchetto che deve essere eseguito. Il *nome_pacchetto* è **nvarchar (260)**.  
  
 [@reference_id =] *reference_id*  
 Identificatore univoco per un riferimento all'ambiente. Questo parametro è facoltativo. Il *reference_id* è **bigint**.  
  
 [@use32bitruntime =] *use32bitruntime*  
 Viene indicato se il runtime a 32 bit deve essere utilizzato per eseguire il pacchetto in un sistema operativo a 64 bit. Utilizzare il valore 1 per eseguire il pacchetto con il runtime a 32 bit quando in esecuzione in un sistema operativo a 64 bit. Utilizzare il valore pari a 0 per eseguire il pacchetto con il runtime a 64 bit quando in esecuzione in un sistema operativo a 64 bit. Questo parametro è facoltativo. Il *Use32bitruntime* è **bit**.  
 
 [@runinscaleout =] *runinscaleout*  
 Indica se l'esecuzione in orizzontale. Utilizzare il valore 1 per eseguire il pacchetto in orizzontale. Utilizzare il valore 0 per eseguire il pacchetto senza orizzontale. Questo parametro è facoltativo. Se non specificato, il relativo valore è impostato su DEFAULT_EXECUTION_MODE in [SSISDB]. [catalog]. [catalog_properties]. Il *runinscaleout* è **bit**. 
 
 [@useanyworker =] *useanyworker*  
  Indica se qualsiasi scala i thread di lavoro è consentito effettuare l'esecuzione. Utilizzare il valore 1 per eseguire il pacchetto con qualsiasi scala i thread di lavoro. Utilizzare il valore 0 per indicare che scala non tutti i lavori sono autorizzati a eseguire il pacchetto. Questo parametro è facoltativo. Se non specificato, il valore è impostato su 1. Il *useanyworker* è **bit**. 
  
 [@execution_id =] *valore di execution_id*  
 Viene restituito l'identificatore univoco per un'istanza di esecuzione. Il *valore di execution_id* è **bigint**.  

  
## <a name="remarks"></a>Osservazioni  
 Un'esecuzione viene utilizzata per specificare i valori del parametro utilizzati da un pacchetto durante una singola istanza di esecuzione del pacchetto.  
  
 Se viene specificato un riferimento all'ambiente con il *reference_id* parametro, la stored procedure consente di popolare i parametri di progetto e di pacchetto con valori letterali o valori di cui viene fatto riferimenti dalle variabili di ambiente corrispondente. Se viene specificato il riferimento all'ambiente, durante l'esecuzione del pacchetto vengono utilizzati i valori di parametro predefiniti. Per determinare esattamente quali valori vengono utilizzati per una particolare istanza di esecuzione, utilizzare il *valore di execution_id* valore del parametro da questa stored procedure e query di output di [execution_parameter_values](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md) visualizzazione.  
  
 In un'esecuzione possono essere specificati solo i pacchetti contrassegnati come pacchetti del punto di ingresso. In caso contrario, l'esecuzione non viene completata.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene chiamato Catalog. create_execution per creare un'istanza di esecuzione per il pacchetto child1, che non è in orizzontale. Il pacchetto è incluso in Project1 di Integration Services. Nell'esempio viene chiamato catalog.set_execution_parameter_value per impostare i valori per i parametri Parameter1, Parameter2 e LOGGING_LEVEL. Inoltre viene chiamato catalog.start_execution per avviare un'istanza di esecuzione.  
  
```sql  
Declare @execution_id bigint  
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Child1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'TestDeply4', @project_name=N'Integration Services Project1', @use32bitruntime=False, @reference_id=Null  
Select @execution_id  
DECLARE @var0 sql_variant = N'Child1.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter1', @parameter_value=@var0  
DECLARE @var1 sql_variant = N'Child2.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter2', @parameter_value=@var1  
DECLARE @var2 smallint = 1  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var2  
EXEC [SSISDB].[catalog].[start_execution] @execution_id  
GO  
```  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e EXECUTE sul progetto e, se applicabile, autorizzazioni READ sull'ambiente a cui si fa riferimento  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  

 Se @runinscaleout è 1, la stored procedure richiede una delle seguenti autorizzazioni:
 
-   L'appartenenza al **ssis_admin** ruolo del database

-   L'appartenenza al **ssis_cluster_executor** ruolo del database

-   L'appartenenza al **sysadmin** ruolo del server
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Il pacchetto non esiste.  
  
-   Utente senza autorizzazioni appropriate.  
  
-   Il riferimento all'ambiente, *reference_id*, non è valido.  
  
-   Specificato pacchetto che non è un pacchetto del punto di ingresso.  
  
-   Tipo di dati della variabile di ambiente a cui si fa riferimento diverso dal tipo di dati del parametro di progetto o di pacchetto.  
  
-   Progetto o pacchetto in cui sono contenuti parametri che richiedono valori, ma non è stato assegnato alcun valore.  
  
-   Impossibile trovare le variabili di ambiente a cui fa riferimento nell'ambiente che fa riferimento l'ambiente, *reference_id*, specifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Catalog. start_execution &#40; Database SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)   
 [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 [Catalog.add_execution_worker &#40; Database SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)  
  

