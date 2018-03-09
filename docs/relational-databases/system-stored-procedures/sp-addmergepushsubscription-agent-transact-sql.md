---
title: sp_addmergepushsubscription_agent (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
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
- sp_addmergepushsubscription_agent_TSQL
- sp_addmergepushsubscription_agent
helpviewer_keywords:
- sp_addmergepushsubscription_agent
ms.assetid: 808a1925-be46-4999-8d69-b3a83010ec81
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9692ecde71557a4898d7fb9892cdffdd37cbbcd2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spaddmergepushsubscriptionagent-transact-sql"></a>sp_addmergepushsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un nuovo processo dell'agente utilizzato per la pianificazione della sincronizzazione di una sottoscrizione push in una replica di tipo merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
> [!IMPORTANT]  
>  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addmergepushsubscription_agent [ @publication =] 'publication'   
    [ , [ @subscriber = ] 'subscriber' ]   
    [ , [ @subscriber_db = ] 'subscriber_db' ]   
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]   
    [ , [ @subscriber_login = ] 'subscriber_login' ]   
    [ , [ @subscriber_password = ] 'subscriber_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @frequency_type = ] frequency_type ]   
    [ , [ @frequency_interval = ] frequency_interval ]   
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]   
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]   
    [ , [ @frequency_subday = ] frequency_subday ]   
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]   
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]   
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@subscriber =** ] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_db =** ] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscriber_db* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_security_mode =** ] *subscriber_security_mode*  
 Modalità di sicurezza da utilizzare quando si effettua la connessione a un Sottoscrittore per la sincronizzazione. *subscriber_security_mode* è **int**, con un valore predefinito è 1. Se **0**, specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. Se **1**, specifica l'autenticazione di Windows.  
  
 [  **@subscriber_login =** ] **'***subscriber_login***'**  
 Account di accesso da utilizzare quando ci si connette a un Sottoscrittore per la sincronizzazione. *subscriber_login* è obbligatorio se *subscriber_security_mode* è impostato su **0**. *subscriber_login* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_password =** ] **'***subscriber_password***'**  
 Password del Sottoscrittore per l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *subscriber_password* è obbligatorio se *subscriber_security_mode* è impostato su **0**. *subscriber_password* è **sysname**, con un valore predefinito è NULL. Le password del Sottoscrittore vengono crittografate automaticamente.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@publisher_security_mode =** ] *publisher_security_mode*  
 Modalità di sicurezza da utilizzare quando si effettua la connessione a un server di pubblicazione per la sincronizzazione. *publisher_security_mode* è **int**, con un valore predefinito è 1. Se **0**, specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. Se **1**, specifica l'autenticazione di Windows.  
  
 [  **@publisher_login =** ] **'***publisher_login***'**  
 Account di accesso da utilizzare per la connessione a un server di pubblicazione in fase di sincronizzazione. *publisher_login* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@publisher_password =** ] **'***publisher_password***'**  
 Password utilizzata per la connessione al server di pubblicazione. *publisher_password* è **sysname**, con un valore predefinito è NULL.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@job_login =** ] **'***job_login***'**  
 Account di accesso per l'account di Windows utilizzato per l'esecuzione dell'agente. *job_login* è **nvarchar (257)**, con un valore predefinito null. Questo account di Windows viene sempre utilizzato per le connessioni dell'agente al server di distribuzione e per le connessioni al Sottoscrittore e al server di pubblicazione in caso di utilizzo dell'autenticazione integrata di Windows.  
  
 [  **@job_password =** ] **'***job_password***'**  
 Password dell'account di Windows utilizzato per l'esecuzione dell'agente. *job_password* è **sysname**, non prevede alcun valore predefinito.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@job_name =** ] **'***job_name***'**  
 Nome di un processo esistente dell'agente. *job_name* è **sysname**, con un valore predefinito null. Questo parametro viene specificato solo quando la sottoscrizione viene sincronizzata utilizzando un processo esistente anziché un nuovo processo (impostazione predefinita). Se non si è un membro del **sysadmin** ruolo predefinito del server, è necessario specificare *job_login* e *job_password* quando si specifica *job_name*.  
  
 [  **@frequency_type =** ] *frequency_type*  
 Frequenza per l'esecuzione pianificata dell'agente di merge. *frequency_type* è **int**, e può essere uno dei valori seguenti.  
  
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
  
> [!NOTE]  
>  Se si specifica un valore **64** fa sì che l'agente di Merge per l'esecuzione in modalità continua. Corrisponde all'impostazione di **-continua** parametro per l'agente. Per altre informazioni, vedere [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 Giorni in cui viene eseguito l'agente di merge. *frequency_interval* è **int**, e può essere uno dei valori seguenti.  
  
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
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 Data dell'agente di merge. Questo parametro viene utilizzato quando *frequency_type* è impostato su **32** (frequenza mensile relativa). *frequency_relative_interval* è **int**, e può essere uno dei valori seguenti.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**1**|Primo|  
|**2**|Secondo|  
|**4**|Terzo|  
|**8**|Quarto|  
|**16**|Ultimo|  
|NULL (predefinito)||  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 Fattore di occorrenza utilizzato da *frequency_type*. *frequency_recurrence_factor* è **int**, con un valore predefinito è NULL.  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 Frequenza di ripianificazione durante il periodo definito. *frequency_subday* è **int**, e può essere uno dei valori seguenti.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Secondo|  
|**4**|Minuto|  
|**8**|Ora|  
|NULL (predefinito)||  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 Intervallo per *frequency_subday*. *frequency_subday_interval* è **int**, con un valore predefinito è NULL.  
  
 [  **@active_start_time_of_day =** ] *active_start_time_of_day*  
 Ora del giorno della prima esecuzione pianificata dell'agente di merge, nel formato HHMMSS. *active_start_time_of_day* è **int**, con un valore predefinito è NULL.  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 Ora del giorno dell'ultima esecuzione pianificata dell'agente di merge, nel formato HHMMSS. *active_end_time_of_day* è **int**, con un valore predefinito è NULL.  
  
 [  **@active_start_date =** ] *active_start_date*  
 Data della prima esecuzione pianificata dell'agente di merge, nel formato AAAAMMGG. *active_start_date* è **int**, con un valore predefinito è NULL.  
  
 [  **@active_end_date =** ] *active_end_date*  
 Data dell'ultima esecuzione pianificata dell'agente di merge, nel formato AAAAMMGG. *active_end_date* è **int**, con un valore predefinito è NULL.  
  
 [  **@enabled_for_syncmgr =** ] **'***enabled_for_syncmgr***'**  
 Specifica se la sottoscrizione può essere sincronizzata tramite Gestione sincronizzazione Microsoft Windows. *enabled_for_syncmgr* è **nvarchar (5)**, con un valore predefinito è FALSE. Se **false**, la sottoscrizione non è registrata con Gestione sincronizzazione. Se **true**, la sottoscrizione viene registrata con Gestione sincronizzazione e può essere sincronizzata senza avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addmergepushsubscription_agent** viene utilizzata nella replica di tipo merge e utilizza funzionalità simili a [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepushsubscript_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addmergepushsubscription_agent**.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
