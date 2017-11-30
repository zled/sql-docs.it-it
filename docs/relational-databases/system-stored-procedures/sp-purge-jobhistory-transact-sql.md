---
title: sp_purge_jobhistory (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_purge_jobhistory_TSQL
- sp_purge_jobhistory
dev_langs: TSQL
helpviewer_keywords: sp_purge_jobhistory
ms.assetid: 237f9bad-636d-4262-9bfb-66c034a43e88
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e147f4061914314c4ec4c63e5a1808cff4c5608d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sppurgejobhistory-transact-sql"></a>sp_purge_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove i record della cronologia relativi a un processo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_purge_jobhistory   
   {   [ @job_name = ] 'job_name' |   
     | [ @job_id = ] job_id }  
   [ , [ @oldest_date = ] oldest_date ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@job_name=** ] **'***job_name***'**  
 Nome del processo di cui si desidera eliminare i record della cronologia. *job_name*è **sysname**, con un valore predefinito è NULL. Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
> [!NOTE]  
>  I membri del **sysadmin** fisso di server o del ruolo di **SQLAgentOperatorRole** ruolo predefinito del database possono eseguire **sp_purge_jobhistory** senza specificare un *job_name* o *job_id*. Quando **sysadmin** gli utenti specificano questi argomenti, la cronologia processo per tutti i processi locali e multiserver viene eliminata entro il tempo specificato da *oldest_date*. Quando **SQLAgentOperatorRole** gli utenti specificano questi argomenti, la cronologia processo per tutti i processi locali verrà eliminata entro il tempo specificato da *oldest_date*.  
  
 [  **@job_id=** ] *job_id*  
 Numero di identificazione del processo dei record da eliminare. *job_id*è **uniqueidentifier**, con un valore predefinito è NULL. Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi. Vedere la nota nella sezione Descrizione del  **@job_name**  per informazioni su come **sysadmin** o **SQLAgentOperatorRole** gli utenti possono utilizzare questo argomento.  
  
 [  **@oldest_date**  =] *oldest_date*  
 Il record meno recente da conservare nella cronologia. *oldest_date* è **datetime**, con un valore predefinito è NULL. Quando *oldest_date* è specificato, **sp_purge_jobhistory** rimuove solo i record precedenti rispetto al valore specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Quando **sp_purge_jobhistory** viene completato correttamente, viene restituito un messaggio.  
  
## <a name="permissions"></a>Permissions  
 Per impostazione predefinita, solo i membri del **sysadmin** ruolo predefinito del server o **SQLAgentOperatorRole** ruolo predefinito del database può eseguire questa stored procedure. I membri di **sysadmin** possono eliminare la cronologia processo per tutti i processi locali e multiserver. I membri di **SQLAgentOperatorRole** possono eliminare la cronologia processo per tutti i processi locali solo.  
  
 Altri utenti, inclusi i membri di **SQLAgentUserRole** e i membri di **SQLAgentReaderRole**, deve essere concessa esplicitamente l'autorizzazione EXECUTE su **sp_purge_jobhistory**. Dopo la concessione dell'autorizzazione EXECUTE per questa stored procedure, a tali utenti è consentito eliminare solo la cronologia dei processi di cui sono proprietari.  
  
 Il **SQLAgentUserRole**, **SQLAgentReaderRole**, e **SQLAgentOperatorRole** ruoli predefiniti del database sono presenti il **msdb** database. Per informazioni dettagliate sulle relative autorizzazioni, vedere [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-remove-history-for-a-specific-job"></a>A. Rimozione della cronologia di un processo specifico  
 Nell'esempio seguente viene rimossa la cronologia per un processo denominato `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-remove-history-for-all-jobs"></a>B. Rimozione della cronologia di tutti i processi  
  
> [!NOTE]  
>  Solo i membri del **sysadmin** fisso di server e del ruolo di **SQLAgentOperatorRole** possono rimuovere la cronologia per tutti i processi. Quando **sysadmin** agli utenti di eseguire questa stored procedure senza parametri, viene eliminata la cronologia processo per tutti i processi locali e multiserver. Quando **SQLAgentOperatorRole** agli utenti di eseguire questa stored procedure senza parametri, viene eliminata solo la cronologia processo per tutti i processi locali.  
  
 Nell'esempio seguente la procedura viene eseguita senza alcun parametro in modo da rimuovere tutti i record della cronologia.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_help_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobhistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [CONCEDERE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
  
