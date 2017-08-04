---
title: Catalog. set_execution_parameter_value (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 055d86c9-befd-4e63-acb1-6dfe833549d2
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 7b13e7b1c28bad6e573e829183372da4bb62f92d
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="catalogsetexecutionparametervalue-ssisdb-database"></a>catalog.set_execution_parameter_value (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Imposta il valore di un parametro per un'istanza di esecuzione nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Non è possibile modificare un valore di parametro in seguito all'avvio di un'istanza di esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
set_execution_parameter_value [ @execution_id = execution_id  
    , [ @object_type = ] object_type  
    , [ @parameter_name = ] parameter_name  
    , [ @parameter_value = ] parameter_value  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @execution_id =] *valore di execution_id*  
 Identificatore univoco per l'istanza di esecuzione. Il *valore di execution_id* è **bigint**.  
  
 [ @object_type =] *object_type*  
 Tipo di parametro.  
  
 Per i seguenti parametri impostare *object_type* a 50  
  
-   LOGGING_LEVEL  
  
-   CUSTOMIZED_LOGGING_LEVEL  
  
-   DUMP_ON_ERROR  
  
-   DUMP_ON_EVENT  
  
-   DUMP_EVENT_CODE  
  
-   CALLER_INFO  
  
-   SYNCHRONIZED  
  
 Utilizzare il valore `20` per indicare un parametro del progetto o il valore `30` per indicare un parametro del pacchetto.  
  
 Il *object_type* è **smallint**.  
  
 [ @parameter_name =] *parameter_name*  
 Nome del parametro. Il *parameter_name* è **nvarchar (128)**.  
  
 [ @parameter_value =] *parameter_value*  
 Valore del parametro. Il *parameter_value* è **sql_variant**.  
  
## <a name="remarks"></a>Osservazioni  
 Per individuare i valori dei parametri utilizzati per una determinata esecuzione, eseguire una query sulla vista catalog.execution_parameter_values.  
  
 Per specificare l'ambito delle informazioni che viene registrate durante l'esecuzione di un pacchetto, impostare *parameter_name* su LOGGING_LEVEL e *parameter_value* a uno dei valori seguenti.  
  
 Impostare il *object_type* parametro su 50.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|0|Nessuno<br /><br /> La registrazione è disabilitata. Solo lo stato dell'esecuzione del pacchetto viene registrato.|  
|1|Basic<br /><br /> Tutti gli eventi sono registrati, ad eccezione di eventi personalizzati e di diagnostica. Si tratta del valore predefinito.|  
|2|restazioni<br /><br /> Vengono registrati solo le statistiche sulle prestazioni e gli eventi OnError e OnWarning.|  
|3|Dettagliato<br /><br /> Tutti gli eventi vengono registrati, inclusi gli eventi personalizzati e di diagnostica. <br />Gli eventi personalizzati includono gli eventi registrati dalle attività di Integration Services. Per ulteriori informazioni, vedere [Custom Messages for Logging](../../integration-services/performance/integration-services-ssis-logging.md#custom_messages)|  
|4|Derivazione di runtime<br /><br /> Raccoglie i dati necessari per tenere traccia di derivazione nel flusso di dati.|  
|100|Livello di registrazione personalizzato<br /><br /> Specificare le impostazioni nel parametro CUSTOMIZED_LOGGING_LEVEL. Per ulteriori informazioni sui valori che è possibile specificare, vedere [catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md).<br /><br /> Per ulteriori informazioni sui livelli di registrazione personalizzati, vedere [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).|  
  
 Per specificare che il server di Integration Services generi file di dump quando si verifica qualsiasi errore durante un'esecuzione del pacchetto, impostare i valori dei parametri seguenti per un'istanza di esecuzione che non è stata eseguita.  
  
|Parametro|Valore|  
|---------------|-----------|  
|*valore di execution_id*|Identificatore univoco per l'istanza di esecuzione|  
|*object_type*|50|  
|*parameter_name*|‘DUMP_ON_ERROR|  
|*parameter_value*|1|  
  
 Per specificare che il server di Integration Services generi file di dump quando si verificano eventi durante un'esecuzione del pacchetto, impostare i valori dei parametri seguenti per un'istanza di esecuzione che non è stata eseguita.  
  
|Parametro|Valore|  
|---------------|-----------|  
|*valore di execution_id*|Identificatore univoco per l'istanza di esecuzione|  
|*object_type*|50|  
|*parameter_name*|‘DUMP_ON_EVENT|  
|*parameter_value*|1|  
  
 Per specificare gli eventi durante l'esecuzione del pacchetto che inducono il server di Integration Services a generare file di dump, impostare i valori dei parametri seguenti per un'istanza di esecuzione che non è stata eseguita. Separare più codici evento utilizzando un punto e virgola.  
  
|Parametro|Valore|  
|---------------|-----------|  
|*valore di execution_id*|Identificatore univoco per l'istanza di esecuzione|  
|*object_type*|50|  
|*parameter_name*|DUMP_EVENT_CODE|  
|*parameter_value*|Uno o più codici evento|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene specificato che il server di Integration Services genera file di dump quando si verificano errori durante un'esecuzione del pacchetto.  
  
```  
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_ERROR',1  
  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente si specifica che il server di Integration Services genera file di dump quando si verificano eventi durante un'esecuzione del pacchetto e si specifica l'evento che induce il server a generare i file.  
  
```  
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_EVENT',1  
  
declare @event_code nvarchar(50)  
set @event_code = '0xC020801C'  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_EVENT_CODE', @event_code  
```  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY per l'istanza di esecuzione  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Utente senza autorizzazioni appropriate.  
  
-   Identificatore di esecuzione non valido  
  
-   Nome del parametro non valido  
  
-   Tipo di dati del valore del parametro non corrispondente al tipo di dati del parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [Catalog. execution_parameter_values &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)   
 [Generazione di file di dump per l'esecuzione del pacchetto](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
