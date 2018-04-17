---
title: sp_apply_job_to_targets (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a9b3cca205dc3af412ae9c0dfd426b18c05a4fc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spapplyjobtotargets-transact-sql"></a>sp_apply_job_to_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Applica un processo a uno o più server di destinazione o ai server appartenenti a uno o più gruppi di server di destinazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_apply_job_to_targets { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]   
     [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id =**] *job_id*  
 Numero di identificazione del processo da applicare ai server o ai gruppi di server di destinazione specificati. *job_id* viene **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [ **@job_name =**] **'***job_name***'**  
 Nome del processo da applicare ai server o ai gruppi di server di destinazione specificati. *job_name* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [  **@target_server_groups =**] **'***target_server_groups***'**  
 Elenco delimitato da virgole dei gruppi di server di destinazione ai quali si desidera applicare il processo specificato. *target_server_groups* viene **nvarchar(2048)**, con un valore predefinito è NULL.  
  
 [  **@target_servers=** ] **'***target_servers***'**  
 Elenco delimitato da virgole dei server di destinazione ai quali si desidera applicare il processo specificato. *target_servers*viene **nvarchar(2048)**, con un valore predefinito è NULL.  
  
 [  **@operation=** ] **'***operazione***'**  
 Indica se il processo specificato deve essere applicato o rimosso dai server o dai gruppi di server di destinazione specificati. *operazione*viene **varchar(7)**, con un valore predefinito è APPLY. Le operazioni valide sono **applica** e **rimuovere**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_apply_job_to_targets** fornisce un modo semplice per applicare (o rimuovere) un processo da più server di destinazione, senza che sia un'alternativa alla chiamata **sp_add_jobserver** (o **sp_delete_jobserver**) una volta per ogni server di destinazione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il processo `Backup Customer Information` creato in precedenza viene applicato a tutti i server di destinazione nel gruppo `Servers Maintaining Customer Information`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_apply_job_to_targets  
    @job_name = N'Backup Customer Information',  
    @target_server_groups = N'Servers Maintaining Customer Information',   
    @operation = N'APPLY' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
