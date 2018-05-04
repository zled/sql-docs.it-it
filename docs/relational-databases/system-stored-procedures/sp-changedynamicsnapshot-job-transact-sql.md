---
title: sp_changedynamicsnapshot_job (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changedynamicsnapshot_job
- sp_changedynamicsnapshot_job_TSQL
helpviewer_keywords:
- sp_changedynamicsnapshot_job
ms.assetid: ea0dacd2-a5fd-42f4-88dd-7d289b0ae017
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 516bc9fdac1100613147d8dd66e429acd3b9f807
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spchangedynamicsnapshotjob-transact-sql"></a>sp_changedynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di modificare il processo di agente che genera lo snapshot per una sottoscrizione di una pubblicazione con un filtro di riga con parametri. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changedynamicsnapshot_job [ @publication = ] 'publication'  
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]  
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]  
    [ , [ @frequency_type = ] frequency_type ]   
    [ , [ @frequency_interval = ] frequency_interval ]   
    [ , [ @frequency_subday = ] frequency_subday ]   
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]   
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]   
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]   
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@dynamic_snapshot_jobname =** ] **'***dynamic_snapshot_jobname***'**  
 Nome del processo di snapshot da modificare. *dynamic_snapshot_jobname*viene **sysname**, con valore predefinito di N '% s'. Se *dynamic_snapshot_jobid* è specificato, è necessario utilizzare il valore predefinito per *dynamic_snapshot_jobname*.  
  
 [  **@dynamic_snapshot_jobid =** ] **'***dynamic_snapshot_jobid***'**  
 ID del processo di snapshot da modificare. *dynamic_snapshot_jobid* viene **uniqueidentifier**, con valore predefinito è NULL. Se *dynamic_snapshot_jobname*è specificato, è necessario utilizzare il valore predefinito per *dynamic_snapshot_jobid*.  
  
 [  **@frequency_type =** ] *frequency_type*  
 Frequenza per l'esecuzione pianificata dell'agente. *frequency_type* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Su richiesta|  
|**4**|Ogni giorno|  
|**8**|Settimanale|  
|**16**|Mensile|  
|**32**|Mensile relativa|  
|**64**|Avvio automatico|  
|**128**|Periodica|  
|NULL (predefinito)||  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 Giorni in cui viene eseguito l'agente. *frequency_interval* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Domenica|  
|**2**|Lunedì|  
|**3**|Martedì|  
|**4**|Mercoledì|  
|**5**|Giovedì|  
|**6**|Venerdì|  
|**7**|Sabato|  
|**8**|Day|  
|**9**|Giorni feriali|  
|**10**|Giorni festivi|  
|NULL (predefinito)||  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 Frequenza di ripianificazione durante il periodo definito. *frequency_subday* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Secondo|  
|**4**|Minuto|  
|**8**|Ora|  
|NULL (predefinito)||  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 Intervallo per *frequency_subday*. *frequency_subday_interval* viene **int**, con un valore predefinito è NULL.  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 Data di esecuzione dell'agente di merge. Questo parametro viene utilizzato quando *frequency_type* è impostato su **32** (frequenza mensile relativa). *frequency_relative_interval* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Primo|  
|**2**|Secondo|  
|**4**|Terzo|  
|**8**|Quarto|  
|**16**|Ultimo|  
|NULL (predefinito)||  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 Fattore di occorrenza utilizzato da *frequency_type*. *frequency_recurrence_factor* viene **int**, con un valore predefinito è NULL.  
  
 [ **@active_start_date =** ] *active_start_date*  
 Data della prima esecuzione pianificata dell'agente di merge, nel formato AAAAMMGG. *active_start_date* viene **int**, con un valore predefinito è NULL.  
  
 [ **@active_end_date =** ] *active_end_date*  
 Data dell'ultima esecuzione pianificata dell'agente di merge, nel formato AAAAMMGG. *active_end_date* viene **int**, con un valore predefinito è NULL.  
  
 [  **@active_start_time_of_day =** ] *active_start_time_of_day*  
 Ora del giorno della prima esecuzione pianificata dell'agente di merge, nel formato HHMMSS. *active_start_time_of_day* viene **int**, con un valore predefinito è NULL.  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 Ora del giorno dell'ultima esecuzione pianificata dell'agente di merge, nel formato HHMMSS. *active_end_time_of_day* viene **int**, con un valore predefinito è NULL.  
  
 [  **@job_login=** ] **'***job_login***'**  
 Account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows utilizzato per l'esecuzione dell'agente snapshot durante la generazione dello snapshot per una sottoscrizione con un filtro di riga con parametri. *job_login* viene **nvarchar(257)**, con valore predefinito è NULL.  
  
 [  **@job_password=** ] **'***job_password***'**  
 Password dell'account di Windows utilizzato per l'esecuzione dell'agente snapshot durante la generazione dello snapshot per una sottoscrizione con un filtro di riga con parametri. *job_password* viene **nvarchar(257)**, con valore predefinito è NULL.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_changedynamicsnapshot_job** viene utilizzata nella replica di tipo merge per le pubblicazioni con filtri di riga con parametri.  
  
 Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_changedynamicsnapshot_job**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le impostazioni di sicurezza della replica](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
