---
title: sp_help_jobsteplog (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
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
- sp_help_jobsteplog_TSQL
- sp_help_jobsteplog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobsteplog
ms.assetid: 1a0be7b1-8f31-4b4c-aadb-586c0e00ed04
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1d23ab7e7e5c58c040b091f80500fdba3845387
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpjobsteplog-transact-sql"></a>sp_help_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce i metadati relativi a uno specifico [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log dei passaggi di processo dell'agente. **sp_help_jobsteplog** non restituisce il log effettivo.  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]  
     [ , [ @step_name = ] 'step_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id =**] **'***job_id***'**  
 ID del processo per il quale si desidera ottenere le informazioni sul log del passaggio. *job_id* viene **int**, con un valore predefinito è NULL.  
  
 [ **@job_name =**] **'***job_name***'**  
 Nome del processo. *job_name* viene **sysname**, con valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [ **@step_id =**] *step_id*  
 Numero di identificazione del passaggio del processo. Se viene omesso, vengono inclusi tutti i passaggi del processo. *step_id* viene **int**, con un valore predefinito è NULL.  
  
 [  **@step_name =**] **'***step_name***'**  
 Nome del passaggio del processo. *step_name* viene **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID univoco del processo.|  
|**job_name**|**sysname**|Nome del processo|  
|**step_id**|**int**|ID del passaggio all'interno del processo. Ad esempio, se il passaggio è il primo passaggio del processo, il relativo *step_id* è 1.|  
|**step_name**|**sysname**|Nome del passaggio del processo.|  
|**step_uid**|**uniqueidentifier**|ID univoco generato dal sistema del passaggio nel processo.|  
|**date_created**|**datetime**|Data di creazione del passaggio.|  
|**date_modified**|**datetime**|Data dell'ultima modifica del passaggio.|  
|**log_size**|**float**|Dimensioni in megabyte (MB) del log dei passaggi del processo.|  
|**log**|**nvarchar(max)**|Output del log dei passaggi del processo.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_jobsteplog** è il **msdb** database.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 I membri di **SQLAgentUserRole** può visualizzare solo i metadati del log passaggio di processo per i passaggi di processo che possiedono.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returns-job-step-log-information-for-all-steps-in-a-specific-job"></a>A. Restituzione delle informazioni del log su tutti i passaggi di un processo specifico  
 Nell'esempio seguente vengono restituite le informazioni del log su tutti i passaggi di un processo denominato `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-job-step-log-information-about-a-specific-job-step"></a>B. Restituzione delle informazioni del log su un passaggio specifico  
 Nell'esempio seguente vengono restituite le informazioni del log relative al primo passaggio del processo denominato `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)   
 [Stored procedure SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
