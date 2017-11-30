---
title: sp_help_jobs_in_schedule (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_jobs_in_schedule_TSQL
- sp_help_jobs_in_schedule
dev_langs: TSQL
helpviewer_keywords: sp_help_jobs_in_schedule
ms.assetid: 1168aa2c-136b-4ba3-b18e-9070d95a26fa
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ff12f4e1ee3f994a74360969cacd51d9e479a70e
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpjobsinschedule-transact-sql"></a>sp_help_jobs_in_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni sui processi ai quali è associata una pianificazione specifica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_jobs_in_schedule   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@schedule_id =** ] *schedule_id*  
 Identificatore della pianificazione per cui restituire un elenco di informazioni. *schedule_id* è **int**, non prevede alcun valore predefinito. Entrambi *schedule_id* o *schedule_name* può essere specificato.  
  
 [  **@schedule_name =** ] **'***schedule_name***'**  
 Nome della pianificazione per cui restituire un elenco di informazioni. *schedule_name* è **sysname**, non prevede alcun valore predefinito. Entrambi *schedule_id* o *schedule_name* può essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Restituisce il set di risultati seguente:  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID univoco del processo.|  
|**server di origine**|**nvarchar (30)**|Nome del server di provenienza del processo.|  
|**name**|**sysname**|Nome del processo|  
|**abilitato**|**tinyint**|Indica se il processo è abilitato per l'esecuzione.|  
|**Descrizione**|**nvarchar(512)**|Descrizione del processo.|  
|**start_step_id**|**int**|ID del passaggio del processo da cui deve iniziare l'esecuzione.|  
|**categoria**|**sysname**|Categoria del processo.|  
|**proprietario**|**sysname**|Proprietario del processo.|  
|**notify_level_eventlog**|**int**|Maschera di bit che indica le condizioni per la registrazione dell'evento di notifica nel registro applicazioni di Microsoft Windows. I possibili valori sono i seguenti:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo del processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = al termine del processo (indipendentemente dal risultato del processo)|  
|**notify_level_email**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio di posta elettronica di notifica al termine di un processo. I valori possibili sono le stesse di **notify_level_eventlog**.|  
|**notify_level_netsend**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio in rete al termine di un processo. I valori possibili sono le stesse di **notify_level_eventlog**.|  
|**notify_level_page**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio su cercapersone al termine di un processo. I valori possibili sono le stesse di **notify_level_eventlog**.|  
|**notify_email_operator**|**sysname**|Nome di posta elettronica dell'operatore a cui inviare la notifica.|  
|**notify_netsend_operator**|**sysname**|Nome di computer o di utente specificato quando si invia un messaggio in rete.|  
|**notify_page_operator**|**sysname**|Nome di computer o di utente specificato quando si invia un messaggio su cercapersone.|  
|**possibili**|**int**|Maschera di bit che indica le condizioni per l'eliminazione di un processo al termine del processo. I valori possibili sono le stesse di **notify_level_eventlog**.|  
|**Date_Created**|**datetime**|Data di creazione del processo.|  
|**date_modified**|**datetime**|Data dell'ultima modifica del processo.|  
|**Version_number**|**int**|Versione del processo aggiornata automaticamente in corrispondenza di ogni modifica del processo.|  
|**last_run_date**|**int**|Data dell'ultimo avvio dell'esecuzione del processo.|  
|**last_run_time**|**int**|Ora dell'ultimo avvio dell'esecuzione del processo.|  
|**last_run_outcome**|**int**|Risultato dell'ultima esecuzione del processo:<br /><br /> **0** = non riuscito<br /><br /> **1** = ha avuto esito positivo<br /><br /> **3** = annullato<br /><br /> **5** = sconosciuto|  
|**next_run_date**|**int**|Data pianificata per la successiva esecuzione del processo.|  
|**next_run_time**|**int**|Ora pianificata per la successiva esecuzione del processo.|  
|**next_run_schedule_id**|**int**|ID della successiva pianificazione di esecuzione.|  
|**current_execution_status**|**int**|Stato di esecuzione corrente.|  
|**current_execution_step**|**sysname**|Passaggio di esecuzione corrente all'interno del processo.|  
|**current_retry_attempt**|**int**|Se il processo è in esecuzione e il passaggio è stato ripetuto, indica il numero del tentativo in corso.|  
|**has_step**|**int**|Numero di passaggi del processo.|  
|**has_schedule**|**int**|Numero di pianificazioni del processo.|  
|**has_target**|**int**|Numero di server di destinazione del processo.|  
|**tipo**|**int**|Tipo del processo:<br /><br /> **1** = processo locale.<br /><br /> **2** = processo multiserver.<br /><br /> **0** = processo non dispone di alcun server di destinazione.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa stored procedure visualizza le informazioni sui processi associati alla pianificazione specificata.  
  
## <a name="permissions"></a>Permissions  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 I membri di **SQLAgentUserRole** solo possibile visualizzare lo stato dei processi di cui sono proprietari.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono visualizzati i processi associati alla pianificazione `NightlyJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobs_in_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Agent Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
