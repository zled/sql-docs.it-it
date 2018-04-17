---
title: sp_post_msx_operation (Transact-SQL) | Microsoft Docs
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
- sp_post_msx_operation
- sp_post_msx_operation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_post_msx_operation
ms.assetid: 085deef8-2709-4da9-bb97-9ab32effdacf
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 08cda2f3508e5c4f338c8e607654f5e41ed803f0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sppostmsxoperation-transact-sql"></a>sp_post_msx_operation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Inserisce operazioni (righe) di **sysdownloadlist** tabella di sistema per i server di destinazione di scaricare ed eseguire.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_post_msx_operation  
     [ @operation = ] 'operation'  
     [ , [ @object_type = ] 'object' ]   
     { , [ @job_id = ] job_id }   
     [ , [ @specific_target_server = ] 'target_server' ]   
     [ , [ @value = ] value ]  
     [ , [ @schedule_uid = ] schedule_uid ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@operation =**] **'***operazione***'**  
 Tipo di operazione da richiedere. *operazione*viene **varchar(64)**, non prevede alcun valore predefinito. Operazioni valide dipendono *object_type*.  
  
|Tipo oggetto|Operazione|  
|-----------------|---------------|  
|**JOB**|INSERT<br /><br /> UPDATE<br /><br /> DELETE<br /><br /> START<br /><br /> STOP|  
|**SERVER**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**PIANIFICAZIONE**|INSERT<br /><br /> UPDATE<br /><br /> DELETE|  
  
 [  **@object_type =**] **'***oggetto***'**  
 Tipo di oggetto per cui richiedere un'operazione. I tipi validi sono **processo**, **SERVER**, e **pianificazione**. *oggetto* viene **varchar(64)**, il valore predefinito è **processo**.  
  
 [ **@job_id =**] *job_id*  
 Il numero di identificazione del processo a cui viene applicata l'operazione. *job_id* viene **uniqueidentifier**, non prevede alcun valore predefinito. **0x00** indica tutti i processi. Se *oggetto* è **SERVER**, quindi *job_id*non è obbligatorio.  
  
 [ **@specific_target_server =**] **'***target_server***'**  
 Nome del server di destinazione in cui l'operazione specificata viene applicata. Se *job_id* è specificato, ma *target_server* viene omesso, le operazioni vengono registrate per tutti i server di processo del processo. *target_server* viene **nvarchar(30)**, con un valore predefinito è NULL.  
  
 [  **@value =**] *valore*  
 L'intervallo di polling in secondi. *value* è **int**e il valore predefinito è NULL. Specificare questo parametro solo se *operazione* è **SET-POLL**.  
  
 [  **@schedule_uid=** ] *valore schedule_uid*  
 Identificatore univoco per la pianificazione a cui si riferisce l'operazione. *valore schedule_uid* viene **uniqueidentifier**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **SP_POST_MSX_OPERATION** deve essere eseguita la **msdb** database.  
  
 **SP_POST_MSX_OPERATION** può sempre essere chiamato in modo sicuro perché determina innanzitutto se il server corrente è un agente multiserver di Microsoft SQL Server e, in tal caso, se *oggetto*è un processo multiserver.  
  
 Dopo un'operazione è stata registrata, viene visualizzato nel **sysdownloadlist** tabella. Dopo la creazione e l'inserimento di un processo, è necessario comunicare ai server di destinazione (TSX) tutte le successive modifiche apportate al processo. A tale scopo è possibile utilizzare l'elenco di download.  
  
 È consigliabile gestire l'elenco di download in SQL Server Management Studio. Per ulteriori informazioni, vedere [visualizzare o modificare i processi](http://msdn.microsoft.com/library/57f649b8-190c-4304-abd7-7ca5297deab7).  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa stored procedure, è necessario consentire agli utenti di **sysadmin** ruolo predefinito del server.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_resync_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
