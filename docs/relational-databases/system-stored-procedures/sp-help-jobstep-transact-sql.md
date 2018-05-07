---
title: sp_help_jobstep (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobstep_TSQL
- sp_help_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobstep
ms.assetid: 4a13b804-45f2-4f82-987f-42d9a57dd6db
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a614a40001e21fadf708cb2079dbe45171cafe62
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpjobstep-transact-sql"></a>sp_help_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui passaggi di un processo utilizzato dal servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per l'esecuzione di attività automatizzate.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_jobstep { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]   
     [ , [ @step_name = ] 'step_name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id =**] **'***job_id***'**  
 ID del processo per il quale si desidera ottenere le informazioni. *job_id* viene **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [ **@job_name =**] **'***job_name***'**  
 Nome del processo. *job_name* viene **sysname**, con valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [ **@step_id =**] *step_id*  
 Numero di identificazione del passaggio del processo. Se viene omesso, vengono inclusi tutti i passaggi del processo. *step_id* viene **int**, con un valore predefinito è NULL.  
  
 [  **@step_name =**] **'***step_name***'**  
 Nome del passaggio del processo. *step_name* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@suffix =**] *suffix*  
 Un flag che indica se aggiungere una descrizione per il **flag** colonna nell'output. *suffisso*viene **bit**, con il valore predefinito è **0**. Se *suffisso* è **1**, aggiungere una descrizione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|Identificatore univoco del passaggio.|  
|**step_name**|**sysname**|Nome del passaggio del processo.|  
|**subsystem**|**nvarchar(40)**|Sottosistema in cui eseguire il comando del passaggio.|  
|**comando**|**nvarchar(max)**|Comando eseguito nel passaggio.|  
|**flags**|**int**|Maschera di bit dei valori che controllano il funzionamento del passaggio.|  
|**cmdexec_success_code**|**int**|Per un **CmdExec** passaggio, questo è il codice di uscita del processo di un comando eseguito correttamente.|  
|**on_success_action**|**tinyint**|Azione da eseguire se il passaggio viene eseguito correttamente:<br /><br /> **1** = Quit il processo completato correttamente.<br /><br /> **2** = uscita in caso di esito negativo.<br /><br /> **3** = andare al passaggio successivo.<br /><br /> **4** = esecuzione di un passaggio.|  
|**on_success_step_id**|**int**|Se **on_success_action** è 4, indica il passaggio da eseguire.|  
|**on_fail_action**|**tinyint**|Azione da eseguire se il passaggio non viene eseguito correttamente. I valori sono uguali a quelli **on_success_action**.|  
|**on_fail_step_id**|**int**|Se **on_fail_action** è 4, indica il passaggio da eseguire.|  
|**server**|**sysname**|Riservato.|  
|**database_name**|**sysname**|Per un passaggio [!INCLUDE[tsql](../../includes/tsql-md.md)], indica il database in cui viene eseguito il comando.|  
|**database_user_name**|**sysname**|Per un passaggio [!INCLUDE[tsql](../../includes/tsql-md.md)], indica il contesto utente del database in cui viene eseguito il comando.|  
|**retry_attempts**|**int**|Numero massimo di tentativi di esecuzione del comando (nel caso in cui non sia stato eseguito correttamente).|  
|**retry_interval**|**int**|Intervallo in minuti che intercorre tra un tentativo e il successivo.|  
|**os_run_priority**|**int**|Riservato.|  
|**output_file_name**|**nvarchar(200)**|File per il comando che deve essere scritto l'output ([!INCLUDE[tsql](../../includes/tsql-md.md)], **CmdExec**, e **PowerShell** solo per i passaggi).|  
|**last_run_outcome**|**int**|Risultato dell'ultima esecuzione del passaggio:<br /><br /> **0** = non è riuscita<br /><br /> **1** = ha avuto esito positivo<br /><br /> **2** = nuovo tentativo<br /><br /> **3** = annullato<br /><br /> **5** = sconosciuto|  
|**last_run_duration**|**int**|Durata in secondi dell'ultima esecuzione del passaggio.|  
|**last_run_retries**|**int**|Numero di tentativi di esecuzione del comando durante l'ultima esecuzione del passaggio.|  
|**last_run_date**|**int**|Data di inizio dell'ultima esecuzione del passaggio.|  
|**last_run_time**|**int**|Ora di inizio dell'ultima esecuzione del passaggio.|  
|**proxy_id**|**int**|Proxy per il passaggio del processo.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_jobstep** è il **msdb** database.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 I membri di **SQLAgentUserRole** possono visualizzare solo i passaggi del processo per i processi di cui sono proprietari.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-return-information-for-all-steps-in-a-specific-job"></a>A. Restituzione di informazioni su tutti i passaggi di un processo specifico  
 In questo esempio vengono restituiti tutti i passaggi del processo `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-information-about-a-specific-job-step"></a>B. Restituzione di informazioni su un determinato passaggio di un processo  
 Nell'esempio seguente vengono restituite informazioni sul primo passaggio del processo `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
