---
title: sp_remove_job_from_targets (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- sp_remove_job_from_targets_TSQL
- sp_remove_job_from_targets
dev_langs: TSQL
helpviewer_keywords: sp_remove_job_from_targets
ms.assetid: b8171fb1-c11d-4244-8618-a12e28a150ce
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8748e6968197faeb3809cf8adef59bc9b2452d57
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spremovejobfromtargets-transact-sql"></a>sp_remove_job_from_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove il processo specificato dai server di destinazione o gruppi di server di destinazione specificati.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_remove_job_from_targets [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name'   
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@job_id =**] *job_id*  
 Numero di identificazione del processo da cui rimuovere i server di destinazione o i gruppi di server di destinazioni specificati. Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi. *job_id* è **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [  **@job_name =**] **'***job_name***'**  
 Nome del processo da cui rimuovere i server di destinazione o i gruppi di server di destinazione specificati. Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi. *job_name* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@target_server_groups =**] **'***target_server_groups***'**  
 Elenco delimitato da virgole dei gruppi di server di destinazione da rimuovere dal processo specificato. *target_server_groups* è **nvarchar (1024)**, con un valore predefinito è NULL.  
  
 [  **@target_servers =**] **'***target_servers***'**  
 Elenco delimitato da virgole dei server di destinazione da rimuovere dal processo specificato. *target_servers* è **nvarchar (1024)**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni di esecuzione per questa procedura vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il processo `Weekly Sales Backups` creato in precedenza viene rimosso dal gruppo di server di destinazione `Servers Processing Customer Orders` e dai server `SEATTLE1` e `SEATTLE2`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_remove_job_from_targets  
    @job_name = N'Weekly Sales Backups',  
    @target_server_groups = N'Servers Processing Customer Orders',   
    @target_servers = N'SEATTLE2,SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_apply_job_to_targets &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
