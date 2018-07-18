---
title: sp_delete_job (Transact-SQL) | Microsoft Docs
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
- sp_delete_job
- sp_delete_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_job
ms.assetid: b85db6e4-623c-41f1-9643-07e5ea38db09
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 90d213daa9d5a17a6630142e06e5b7ef441a9e9c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spdeletejob-transact-sql"></a>sp_delete_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina un processo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_job { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
     [ , [ @originating_server = ] 'server' ]   
     [ , [ @delete_history = ] delete_history ]  
     [ , [ @delete_unused_schedule = ] delete_unused_schedule ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id=** ] *job_id*  
 Numero di identificazione del processo da eliminare. *job_id* viene **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [ **@job_name=** ] **'***job_name***'**  
 Nome del processo da eliminare. *job_name* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *job_id* o *job_name*deve essere specificato; non è possibile specificarli entrambi.  
  
 [ **@originating_server=** ] **'***server***'**  
 Per uso interno.  
  
 [  **@delete_history=** ] *delete_history*  
 Specifica se eliminare la cronologia per il processo. *delete_history* viene **bit**, il valore predefinito è **1**. Quando *delete_history* è **1**, la cronologia processo per il processo viene eliminata. Quando *delete_history* è **0**, la cronologia processo non viene eliminata.  
  
 Si noti che quando un processo viene eliminato e non viene eliminata la cronologia, le informazioni cronologiche per il processo non saranno inclusi il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cronologia processo dell'interfaccia utente grafica agente, ma le informazioni continueranno comunque a risiedere nel **sysjobhistory**tabella il **msdb** database.  
  
 [  **@delete_unused_schedule=** ] *delete_unused_schedule*  
 Specifica se eliminare le pianificazioni associate a questo processo se non sono associate a nessun altro processo. *delete_unused_schedule* viene **bit**, il valore predefinito è **1**. Quando *delete_unused_schedule* è **1**, pianificazioni associate a questo processo vengono eliminate se nessun altro processo vi fanno riferimento alla pianificazione. Quando *delete_unused_schedule* è **0**, le pianificazioni non vengono eliminate.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Il **@originating_server** argomento è riservato per uso interno.  
  
 Il **@delete_unused_schedule** argomento assicura la compatibilità con le versioni precedenti di SQL Server eliminando automaticamente le pianificazioni che non sono associate ad alcun processo. Si noti che per impostazione predefinita questo parametro assume una funzionalità compatibile con le versioni precedenti. Per mantenere le pianificazioni che non sono associate a un processo, è necessario fornire il valore **0** come il **@delete_unused_schedule** argomento.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è incluso un semplice strumento grafico per la gestione dei processi, che è lo strumento consigliato per la creazione e la gestione dell'infrastruttura dei processi.  
  
 Questa stored procedure non può eliminare i piani di manutenzione né i processi facenti parti dei piani di manutenzione. Per eliminare i piani di manutenzione, utilizzare invece [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 I membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_delete_job** per l'eliminazione di qualsiasi processo. Se un utente non è un membro del ruolo predefinito del server **sysadmin** , può eliminare solo i processi di sua proprietà.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato il processo `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
