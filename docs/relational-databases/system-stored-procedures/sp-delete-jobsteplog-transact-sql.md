---
title: sp_delete_jobsteplog (Transact-SQL) | Documenti Microsoft
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
- sp_delete_jobsteplog
- sp_delete_jobsteplog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobsteplog
ms.assetid: e9ef4c99-abde-4038-b6a3-a25dcbaf0958
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 99f60818976dc3c89e11d2fd1256a7aecd7d8b63
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spdeletejobsteplog-transact-sql"></a>sp_delete_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove tutti i log dei passaggi di processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent specificati con gli argomenti. Utilizzare questa stored procedure per gestire il **sysjobstepslogs** tabella il **msdb** database.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
       [ , [ @step_id = ] step_id | [ @step_name = ] 'step_name' ]  
       [ , [ @older_than = ] 'date' ]  
       [ , [ @larger_than = ] 'size_in_bytes' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id =**] **'***job_id***'**  
 Numero di identificazione del processo in cui è contenuto il log dei passaggi di processo da rimuovere. *job_id* viene **int**, con un valore predefinito è NULL.  
  
 [ **@job_name =**] **'***job_name***'**  
 Nome del processo. *job_name* viene **sysname**, con un valore predefinito è NULL.  
  
> **Nota:** entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [ **@step_id =**] *step_id*  
 Numero di identificazione del passaggio del processo per cui si desidera eliminare il log dei passaggi di processo. Se viene omesso, vengono eliminati tutti i log dei passaggi del processo a meno che non **@older_than** o **@larger_than** specificati. *step_id* viene **int**, con un valore predefinito è NULL.  
  
 [  **@step_name =**] **'***step_name***'**  
 Nome del passaggio del processo per cui è necessario eliminare il log dei passaggi di processo. *step_name* viene **sysname**, con un valore predefinito è NULL.  
  
> **Nota:** entrambi *step_id* o *step_name* può essere specificato, ma non è possibile specificarli entrambi.  
  
 [  **@older_than =**] **'***data***'**  
 Data e ora del log dei passaggi di processo meno recente che si desidera mantenere. Verranno rimossi tutti i log dei passaggi di processo antecedenti questa data e ora. *Data* viene **datetime**, con un valore predefinito è NULL. Entrambi **@older_than** e **@larger_than** può essere specificato.  
  
 [  **@larger_than =**] **'***size_in_bytes***'**  
 Dimensione in byte del log dei passaggi di processo più grande che si desidera mantenere. Vengono rimossi tutti i log dei passaggi di processo la cui dimensione è maggiore rispetto a quella indicata. Entrambi **@larger_than** e **@older_than** può essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_delete_jobsteplog** è il **msdb** database.  
  
 Se nessun argomenti tranne che **@job_id** o **@job_name** specificato, vengono eliminati tutti i log dei passaggi di processo per il processo specificato.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Solo i membri di **sysadmin** possibile eliminare un log dei passaggi di processo che appartiene a un altro utente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-removing-all-job-step-logs-from-a-job"></a>A. Rimozione di tutti i log dei passaggi di processo da un processo  
 Nell'esempio seguente vengono rimossi tutti i log dei passaggi di processo del processo `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup';  
GO  
```  
  
### <a name="b-removing-the-job-step-log-for-a-particular-job-step"></a>B. Rimozione del log dei passaggi di processo per un passaggio di processo specifico  
 Nell'esempio seguente viene rimosso il log relativo al passaggio 2 del processo `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 2;  
GO  
```  
  
### <a name="c-removing-all-job-step-logs-based-on-age-and-size"></a>C. Rimozione di tutti i log dei passaggi di processo in base alla data di creazione e alle dimensioni  
 Nell'esempio seguente tutti i log dei passaggi di processo antecedenti le ore 12.00 del 25 ottobre 2005 e di dimensioni maggiori di 100 MB vengono rimossi dal processo `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @older_than = '10/25/2005 12:00:00',  
    @larger_than = 104857600;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_help_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [Stored procedure SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
