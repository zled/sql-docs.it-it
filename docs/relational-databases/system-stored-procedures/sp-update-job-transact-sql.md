---
title: sp_update_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_job
- sp_update_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_job
ms.assetid: cbdfea38-9e42-47f3-8fc8-5978b82e2623
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3e36396f911c7506660fd82c5540307e95023950
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262216"
---
# <a name="spupdatejob-transact-sql"></a>sp_update_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica gli attributi di un processo.  
  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_update_job [ @job_id =] job_id | [@job_name =] 'job_name'  
     [, [@new_name =] 'new_name' ]   
     [, [@enabled =] enabled ]  
     [, [@description =] 'description' ]   
     [, [@start_step_id =] step_id ]  
     [, [@category_name =] 'category' ]   
     [, [@owner_login_name =] 'login' ]  
     [, [@notify_level_eventlog =] eventlog_level ]  
     [, [@notify_level_email =] email_level ]  
     [, [@notify_level_netsend =] netsend_level ]  
     [, [@notify_level_page =] page_level ]  
     [, [@notify_email_operator_name =] 'operator_name' ]  
     [, [@notify_netsend_operator_name =] 'netsend_operator' ]  
     [, [@notify_page_operator_name =] 'page_operator' ]  
     [, [@delete_level =] delete_level ]   
     [, [@automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id =**] *job_id*  
 Numero di identificazione del processo da aggiornare. *job_id*viene **uniqueidentifier**.  
  
 [ **@job_name =**] **'***job_name***'**  
 Nome del processo. *job_name*viene **nvarchar (128)**.  
  
> **Nota:** entrambi *job_id* o *job_name* deve essere specificato ma non è possibile specificarli entrambi.  
  
 [ **@new_name =**] **'***new_name***'**  
 Nuovo nome del processo. *nuovo_nome*viene **nvarchar (128)**.  
  
 [  **@enabled =**] *abilitato*  
 Specifica se il processo è abilitato (**1**) o non è abilitata (**0**). *abilitata*viene **tinyint**.  
  
 [  **@description =**] **'***descrizione***'**  
 Descrizione del processo. *Descrizione* viene **nvarchar(512)**.  
  
 [ **@start_step_id =**] *step_id*  
 Numero di identificazione del primo passaggio da eseguire per il processo. *step_id*viene **int**.  
  
 [  **@category_name =**] **'***categoria***'**  
 Categoria del processo. *categoria*viene **nvarchar (128)**.  
  
 [  **@owner_login_name =**] **'***account di accesso***'**  
 Nome dell'account di accesso proprietario del processo. *account di accesso*viene **nvarchar (128)** solo i membri della **sysadmin** ruolo predefinito del server è possibile modificare la proprietà dei processi.  
  
 [  **@notify_level_eventlog =**] *eventlog_level*  
 Viene specificato quando inserire una voce per il processo nel registro applicazioni di Microsoft Windows. *eventlog_level*viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione (azione)|  
|-----------|----------------------------|  
|**0**|Never|  
|**1**|In caso di esito positivo|  
|**2**|In caso di esito negativo|  
|**3**|Always|  
  
 [  **@notify_level_email =**] *email_level*  
 Viene specificato quando inviare un messaggio di posta elettronica al termine del processo. *email_level*viene **int**. *email_level*utilizza gli stessi valori *eventlog_level*.  
  
 [ **@notify_level_netsend =**] *netsend_level*  
 Viene specificato quando inviare un messaggio di rete al termine del processo. *netsend_level*viene **int**. *netsend_level*utilizza gli stessi valori *eventlog_level*.  
  
 [  **@notify_level_page =**] *page_level*  
 Viene specificato quando inviare una pagina al termine del processo. *page_level*viene **int**. *page_level*utilizza gli stessi valori *eventlog_level*.  
  
 [  **@notify_email_operator_name =**] **'***operator_name***'**  
 Il nome dell'operatore a cui viene inviato il messaggio di posta elettronica quando *email_level* viene raggiunto. *indirizzo_posta_elettronica* viene **nvarchar (128)**.  
  
 [  **@notify_netsend_operator_name =**] **'***netsend_operator***'**  
 Nome dell'operatore a cui viene inviato il messaggio di rete. *netsend_operator* viene **nvarchar (128)**.  
  
 [  **@notify_page_operator_name =**] **'***page_operator***'**  
 Nome dell'operatore a cui viene inviata una pagina. *page_operator* viene **nvarchar (128)**.  
  
 [  **@delete_level =**] *i possibili*  
 Specifica quando eliminare il processo. *delete_value*viene **int**. *i possibili*utilizza gli stessi valori *eventlog_level*.  
  
 [  **@automatic_post =**] *automatic_post*  
 Riservato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_update_job** deve essere eseguita la **msdb** database.  
  
 **sp_update_job** cambia solo le impostazioni per il parametro che vengono forniti i valori. Se si omette un parametro, viene mantenuta l'impostazione corrente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Solo i membri di **sysadmin** può utilizzare questa stored procedure per modificare gli attributi dei processi di proprietà di altri utenti.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono modificati il nome, la descrizione e lo stato di attivazione del processo `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_job  
    @job_name = N'NightlyBackups',  
    @new_name = N'NightlyBackups -- Disabled',  
    @description = N'Nightly backups disabled during server migration.',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
