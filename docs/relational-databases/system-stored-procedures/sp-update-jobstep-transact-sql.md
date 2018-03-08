---
title: sp_update_jobstep (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_update_jobstep
- sp_update_jobstep_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobstep
ms.assetid: e158802c-c347-4a5d-bf75-c03e5ae56e6b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c81c22e3fb6de374b378df4ef52b316efe65fdb6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spupdatejobstep-transact-sql"></a>sp_update_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica l'impostazione di un passaggio in un processo utilizzato per l'esecuzione di operazioni automatizzate.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_update_jobstep   
     {   [@job_id =] job_id   
       | [@job_name =] 'job_name' } ,  
     [@step_id =] step_id  
     [ , [@step_name =] 'step_name' ]  
     [ , [@subsystem =] 'subsystem' ]   
     [ , [@command =] 'command' ]  
     [ , [@additional_parameters =] 'parameters' ]  
     [ , [@cmdexec_success_code =] success_code ]  
     [ , [@on_success_action =] success_action ]   
     [ , [@on_success_step_id =] success_step_id ]  
     [ , [@on_fail_action =] fail_action ]   
     [ , [@on_fail_step_id =] fail_step_id ]  
     [ , [@server =] 'server' ]   
     [ , [@database_name =] 'database' ]  
     [ , [@database_user_name =] 'user' ]   
     [ , [@retry_attempts =] retry_attempts ]  
     [ , [@retry_interval =] retry_interval ]   
     [ , [@os_run_priority =] run_priority ]  
     [ , [@output_file_name =] 'file_name' ]   
     [ , [@flags =] flags ]  
     [ ,  {   [ @proxy_id = ] proxy_id   
            | [ @proxy_name = ] 'proxy_name' }   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id =**] *job_id*  
 Numero di identificazione del processo a cui appartiene il passaggio. *job_id*è **uniqueidentifier**, con un valore predefinito è NULL. Entrambi *job_id* o *job_name* deve essere specificato ma non è possibile specificarli entrambi.  
  
 [ **@job_name =**] **'***job_name***'**  
 Nome del processo a cui appartiene il passaggio. *job_name*è **sysname**, con un valore predefinito è NULL. Entrambi *job_id* o *job_name* deve essere specificato ma non è possibile specificarli entrambi.  
  
 [ **@step_id =**] *step_id*  
 Numero di identificazione del passaggio del processo da modificare. Questo numero non è modificabile. *step_id*è **int**, non prevede alcun valore predefinito.  
  
 [ **@step_name =**] **'***step_name***'**  
 Nuovo nome del processo. *step_name*è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subsystem =**] **'***sottosistema***'**  
 Il sottosistema utilizzato da Microsoft SQL Server Agent per eseguire *comando*. *sottosistema* è **nvarchar (40)**, con un valore predefinito è NULL.  
  
 [  **@command =**] **'***comando***'**  
 I comandi da eseguire tramite *sottosistema*. *comando* è **nvarchar (max)**, con un valore predefinito è NULL.  
  
 [  **@additional_parameters =**] **'***parametri***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@cmdexec_success_code =**] *success_code*  
 Il valore restituito da un **CmdExec** comando del sottosistema per indicare che *comando* è stata eseguita correttamente. *success_code* è **int**, con un valore predefinito è NULL.  
  
 [  **@on_success_action =**] *success_action*  
 L'azione da eseguire se il passaggio ha esito positivo. *success_action* è **tinyint**, con un valore predefinito è NULL, i possibili valori sono i seguenti.  
  
|Valore|Descrizione (azione)|  
|-----------|----------------------------|  
|**1**|Uscita in caso di esito positivo|  
|**2**|Uscita in caso di esito negativo|  
|**3**|Esecuzione del passaggio successivo|  
|**4**|Andare al passaggio *success_step_id.*|  
  
 [ **@on_success_step_id =**] *success_step_id*  
 Il numero di identificazione del passaggio del processo da eseguire se il passaggio ha esito positivo e *success_action* è **4**. *success_step_id* è **int**, con un valore predefinito è NULL.  
  
 [  **@on_fail_action =**] *fail_action*  
 Azione da eseguire se il passaggio non viene completato correttamente. *fail_action* è **tinyint**, con un valore predefinito è NULL e può avere uno di questi valori.  
  
|Valore|Descrizione (azione)|  
|-----------|----------------------------|  
|**1**|Uscita in caso di esito positivo|  
|**2**|Uscita in caso di esito negativo|  
|**3**|Esecuzione del passaggio successivo|  
|**4**|Andare al passaggio *fail_step_id * *.*|  
  
 [ **@on_fail_step_id =**] *fail_step_id*  
 Il numero di identificazione del passaggio del processo da eseguire se il passaggio ha esito negativo e *fail_action* è **4**. *fail_step_id* è **int**, con un valore predefinito è NULL.  
  
 [ **@server =**] **'***server***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *server* è **nvarchar (128)**, con un valore predefinito è NULL.  
  
 [ **@database_name =**] **'***database***'**  
 Nome del database in cui eseguire un passaggio [!INCLUDE[tsql](../../includes/tsql-md.md)]. *database*è **sysname**. I nomi racchiusi tra parentesi quadre ([ ]) non sono ammessi. Il valore predefinito è NULL.  
  
 [  **@database_user_name =**] **'***utente***'**  
 Nome dell'account utente da utilizzare quando viene eseguito un passaggio [!INCLUDE[tsql](../../includes/tsql-md.md)]. *utente*è **sysname**, con un valore predefinito è NULL.  
  
 [  **@retry_attempts =**] *retry_attempts*  
 Numero di tentativi da eseguire in caso di esecuzione errata del passaggio. *retry_attempts*è **int**, con un valore predefinito è NULL.  
  
 [ **@retry_interval =**] *retry_interval*  
 Numero di minuti che devono trascorrere tra i tentativi. *retry_interval* è **int**, con un valore predefinito è NULL.  
  
 [ **@os_run_priority =**] *run_priority*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@output_file_name =**] **'***file_name***'**  
 Nome del file in cui salvare l'output del passaggio. *file_name* è **nvarchar (200)**, con un valore predefinito è NULL. Questo parametro è valido solo con comandi eseguiti nei sottosistemi [!INCLUDE[tsql](../../includes/tsql-md.md)] o CmdExec.  
  
 Per impostare nuovamente output_file_name su NULL, è necessario impostare *output_file_name* su una stringa vuota (' ') o in una stringa di caratteri vuoti, ma è possibile utilizzare il **CHAR(32)** (funzione). Ad esempio, impostare questo argomento su una stringa vuota nel modo descritto di seguito:  
  
 **@output_file_name = ' '**  
  
 [  **@flags =**] *flag*  
 Opzione che consente di controllare il comportamento. *flag* è **int**, i possibili valori sono i seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**0** (predefinito)|L'output sovrascrive il contenuto del file di output.|  
|**2**|L'output viene aggiunto alla fine del file di output.|  
|**4**|L'output del passaggio del processo Transact-SQL viene scritto nella cronologia dei passaggi|  
|**8**|Il log viene scritto nella tabella. La cronologia esistente viene sovrascritta|  
|**16**|Il log viene scritto nella tabella in aggiunta alla cronologia esistente|  
  
 [ **@proxy_id**= ] *proxy_id*  
 ID del proxy in base al quale viene eseguito il passaggio del processo. *proxy_id* è di tipo **int**, con un valore predefinito è NULL. Se non *proxy_id* è specificato, non *proxy_name* è specificato e nessun *nome_utente* viene specificata, il passaggio del processo viene eseguito come account del servizio per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente.  
  
 [ **@proxy_name**= ] **'***proxy_name***'**  
 Nome del proxy in base al quale viene eseguito il passaggio del processo. *proxy_name* è di tipo **sysname**, con un valore predefinito è NULL. Se non *proxy_id* è specificato, non *proxy_name* è specificato e nessun *nome_utente* viene specificata, il passaggio del processo viene eseguito come account del servizio per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_update_jobstep** deve essere eseguita la **msdb** database.  
  
 L'aggiornamento di un passaggio di processo comporta un incremento del numero di versione del processo.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Solo i membri di **sysadmin** possibile aggiornare un passaggio del processo di proprietà di un altro utente.  
  
 Se il passaggio di processo richiede l'accesso a un proxy, l'autore del passaggio deve disporre dell'accesso al proxy per tale passaggio. Tutti i sottosistemi, a esclusione di Transact-SQL, richiedono un account proxy. I membri di **sysadmin** hanno accesso a tutti i proxy e utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account del servizio agente per il proxy.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene modificato il numero di tentativi per il primo passaggio del processo `Weekly Sales Data Backup`. Dopo aver eseguito questo esempio, il numero di tentativi sarà `10`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1,  
    @retry_attempts = 10 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Consente di visualizzare o modificare i processi](http://msdn.microsoft.com/library/57f649b8-190c-4304-abd7-7ca5297deab7)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
