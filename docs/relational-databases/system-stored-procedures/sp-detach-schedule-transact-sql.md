---
title: sp_detach_schedule (Transact-SQL) | Documenti Microsoft
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
- sp_detach_schedule
- sp_detach_schedule_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_detach_schedule
ms.assetid: 9a1fc335-1bef-4638-a33a-771c54a5dd19
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 08518b0ce80bfb9912c7967d1c1fb80e4f1a70b7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spdetachschedule-transact-sql"></a>sp_detach_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un'associazione tra una pianificazione e un processo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_detach_schedule   
     { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
       { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @delete_unused_schedule = ] delete_unused_schedule   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@job_id=** ] *job_id*  
 Numero di identificazione del processo da cui eliminare la pianificazione. *job_id* è **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [  **@job_name=** ] **'***job_name***'**  
 Nome del processo da cui eliminare la pianificazione. *job_name* è **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [  **@schedule_id=** ] *schedule_id*  
 Numero di identificazione della pianificazione da eliminare per il processo. *schedule_id* è **int**, con un valore predefinito è NULL.  
  
 [  **@schedule_name=** ] **'***schedule_name***'**  
 Nome della pianificazione da eliminare dal processo. *schedule_name* è **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *schedule_id* o *schedule_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [  **@delete_unused_schedule=** ] *delete_unused_schedule*  
 Specifica se eliminare le pianificazioni dei processi non utilizzate. *delete_unused_schedule* è **bit**, il valore predefinito è **0**, il che significa che verranno mantenute tutte le pianificazioni, anche se vi fa riferimento alcun processo. Se impostato su **1**, le pianificazioni dei processi vengono eliminate se vi fa riferimento alcun processo.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Notare che il proprietario del processo può collegare un processo a una pianificazione e può scollegare un processo da una pianificazione senza dovere essere anche il proprietario della pianificazione. Tuttavia, non è possibile eliminare una pianificazione se lo scollegamento la lascia senza processi, a meno che il chiamante sia il proprietario della pianificazione.  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono eseguite verifiche per determinare se l'utente è proprietario della pianificazione. Solo i membri del **sysadmin** ruolo predefinito del server possono scollegare le pianificazioni dei processi di proprietà di un altro utente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimossa un'associazione tra una pianificazione `'NightlyJobs'` e un processo `'BackupDatabase'`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_detach_schedule  
    @job_name = 'BackupDatabase',  
    @schedule_name = 'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)  
  
  
