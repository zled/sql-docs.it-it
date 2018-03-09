---
title: sp_changepublication_snapshot (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changepublication_snapshot_TSQL
- sp_changepublication_snapshot
helpviewer_keywords:
- sp_changepublication_snapshot
ms.assetid: 518a4618-3592-4edc-8425-cbc33cdff891
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a0a7c888c4851a9bcb671823d0bd46309a00300
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spchangepublicationsnapshot-transact-sql"></a>sp_changepublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le proprietà dell'agente snapshot per la pubblicazione specificata. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
> [!IMPORTANT]  
>  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changepublication_snapshot [ @publication= ] 'publication'  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @snapshot_job_name = ] 'snapshot_agent_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@frequency_type =**] *frequency_type*  
 Frequenza per l'esecuzione pianificata dell'agente. *frequency_type* è **int**, e può essere uno dei valori seguenti.  
  
|Valore|Descrizione|  
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
  
 [  **@frequency_interval =**] *frequency_interval*  
 Specifica i giorni in cui viene eseguito l'agente. *frequency_interval* è **int**, e può essere uno dei valori seguenti.  
  
|Valore|Descrizione|  
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
  
 [  **@frequency_subday =**] *frequency_subday*  
 Unità di *freq_subday_interval*. *frequency_subday* è **int**, i possibili valori sono i seguenti.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Secondo|  
|**4**|Minuto|  
|**8**|Ora|  
|NULL (predefinito)||  
  
 [  **@frequency_subday_interval =**] *frequency_subday_interval*  
 Intervallo per *frequency_subday*. *frequency_subday_interval* è **int**, con un valore predefinito è NULL.  
  
 [  **@frequency_relative_interval =**] *frequency_relative_interval*  
 Data di esecuzione dell'agente snapshot. *frequency_relative_interval* è **int**, con un valore predefinito è NULL.  
  
 [  **@frequency_recurrence_factor =**] *frequency_recurrence_factor*  
 Fattore di occorrenza utilizzato da *frequency_type*. *frequency_recurrence_factor* è **int**, con un valore predefinito è NULL.  
  
 [  **@active_start_date =**] *active_start_date*  
 Data della prima esecuzione pianificata dell'agente snapshot, nel formato YYYYMMDD. *active_start_date* è **int**, con un valore predefinito è NULL.  
  
 [  **@active_end_date =**] *active_end_date*  
 Data dell'ultima esecuzione pianificata dell'agente snapshot, nel formato YYYYMMDD. *active_end_date* è **int**, con un valore predefinito è NULL.  
  
 [  **@active_start_time_of_day =**] *active_start_time_of_day*  
 Ora del giorno della prima esecuzione pianificata dell'agente snapshot, nel formato HHMMSS. *active_start_time_of_day* è **int**, con un valore predefinito è NULL.  
  
 [  **@active_end_time_of_day =**] *active_end_time_of_day*  
 Ora del giorno dell'ultima esecuzione pianificata dell'agente snapshot, nel formato HHMMSS. *active_end_time_of_day* è **int**, con un valore predefinito è NULL.  
  
 [  **@snapshot_job_name =** ] **'***snapshot_agent_name***'**  
 Nome di un processo dell'agente snapshot esistente se viene utilizzato un processo esistente. *snapshot_agent_name* è **nvarchar (100)** con un valore predefinito null.  
  
 [  **@publisher_security_mode =** ] *publisher_security_mode*  
 Modalità di sicurezza utilizzata dall'agente per la connessione al server di pubblicazione. *publisher_security_mode* è **smallint**, con un valore predefinito è NULL. **0** specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , autenticazione e **1** specifica l'autenticazione di Windows. Il valore **0** deve essere specificato per non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [  **@publisher_login =** ] **'***publisher_login***'**  
 Account di accesso utilizzato per la connessione al server di pubblicazione. *publisher_login* è **sysname**, con un valore predefinito è NULL. *publisher_login* deve essere specificato quando *publisher_security_mode* è **0**. Se *publisher_login* è NULL e *publisher_security_mode* è **1**, l'account Windows specificato *job_login* viene utilizzato quando connessione al server di pubblicazione.  
  
 [  **@publisher_password =** ] **'***publisher_password***'**  
 Password utilizzata per la connessione al server di pubblicazione. *publisher_password* è **sysname**, con un valore predefinito è NULL.  
  
> [!IMPORTANT]  
>  Non usare una password vuota. Usare una password complessa. Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@job_login**  =] **'***job_login***'**  
 Account di accesso per l'account di Windows utilizzato per l'esecuzione dell'agente. *job_login* è **nvarchar (257)**, con un valore predefinito è NULL. Questo account di Windows viene sempre utilizzato per le connessioni dell'agente al server di distribuzione. È necessario specificare questo parametro per la creazione di un nuovo processo per l'agente snapshot. Questo valore non può essere modificato per un server di pubblicazione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [  **@job_password =** ] **'***job_password***'**  
 Password dell'account di Windows utilizzato per l'esecuzione dell'agente. *job_password* è **sysname**, con un valore predefinito è NULL. È necessario specificare questo parametro per la creazione di un nuovo processo per l'agente snapshot.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@publisher =** ] **'***publisher***'**  
 Specifica un server di pubblicazione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *server di pubblicazione* è **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere utilizzato durante la creazione di un agente Snapshot in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_changepublication_snapshot** viene utilizzata nella replica snapshot, transazionale e di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_changepublication_snapshot**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Modificare le proprietà di pubblicazioni e articoli](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addpublication_snapshot &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
