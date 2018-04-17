---
title: sp_MSchange_snapshot_agent_properties (Transact-SQL) | Documenti Microsoft
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
- sp_MSchange_snapshot_agent_properties_TSQL
- sp_MSchange_snapshot_agent_properties
helpviewer_keywords:
- sp_MSchange_snapshot_agent_properties
ms.assetid: 7947a788-3fd7-469f-84db-b03ba89a153c
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3219fc1832d781e3156ec4a2284c3a8e861db67
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spmschangesnapshotagentproperties-transact-sql"></a>sp_MSchange_snapshot_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le proprietà di un processo dell'agente Snapshot eseguita a un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva del server di distribuzione. Questa stored procedure viene utilizzata per modificare le proprietà quando il server di pubblicazione viene eseguito in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. La stored procedure viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_MSchange_snapshot_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @frequency_type= ] frequency_type  
        , [ @frequency_interval= ] frequency_interval  
        , [ @frequency_subday= ] frequency_subday  
        , [ @frequency_subday_interval= ] frequency_subday_interval  
        , [ @frequency_relative_interval= ] frequency_relative_interval  
        , [ @frequency_recurrence_factor= ] frequency_recurrence_factor  
        , [ @active_start_date= ] active_start_date  
        , [ @active_end_date= ] active_end_date  
        , [ @active_start_time_of_day= ] active_start_time_of_day  
        , [ @active_end_time_of_day= ] active_end_time_of_day  
        , [ @snapshot_job_name = ] 'snapshot_agent_name'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nome del database di pubblicazione. *publisher_db* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publication =** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@frequency_type =** ] *frequency_type*  
 Frequenza di esecuzione dell'agente snapshot. *frequency_type* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Su richiesta|  
|**4**|Ogni giorno|  
|**8**|Settimanale|  
|**10**|Mensile|  
|**20**|Mensile, in base all'intervallo di frequenza|  
|**40**|All'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent|  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 È il valore da applicare alla frequenza impostata da *frequency_type*. *frequency_interval* viene **int**, non prevede alcun valore predefinito.  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 Unità di *freq_subday_interval*. *frequency_subday* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Secondo|  
|**4**|Minuto|  
|**8**|Ora|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Intervallo per *frequency_subday*. *frequency_subday_interval* viene **int**, non prevede alcun valore predefinito.  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 Data di esecuzione dell'agente snapshot. *frequency_relative_interval* viene **int**, non prevede alcun valore predefinito.  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 Fattore di occorrenza utilizzato da *frequency_type*. *frequency_recurrence_factor* viene **int**, non prevede alcun valore predefinito.  
  
 [ **@active_start_date =** ] *active_start_date*  
 Data della prima esecuzione pianificata dell'agente snapshot, nel formato YYYYMMDD. *active_start_date* viene **int**, non prevede alcun valore predefinito.  
  
 [ **@active_end_date =** ] *active_end_date*  
 Data dell'ultima esecuzione pianificata dell'agente snapshot, nel formato YYYYMMDD. *active_end_date* viene **int**, non prevede alcun valore predefinito.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Ora del giorno della prima esecuzione pianificata dell'agente snapshot, nel formato HHMMSS. *active_start_time_of_day* viene **int**, non prevede alcun valore predefinito.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Ora del giorno dell'ultima esecuzione pianificata dell'agente snapshot, nel formato HHMMSS. *active_end_time_of_day* viene **int**, non prevede alcun valore predefinito.  
  
 [  **@snapshot_job_name =** ] **'***snapshot_agent_name***'**  
 Nome di un processo dell'agente snapshot esistente se viene utilizzato un processo esistente. *snapshot_agent_name* viene **nvarchar(100)**, non prevede alcun valore predefinito.  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 Modalità di sicurezza utilizzata dall'agente per la connessione al server di pubblicazione. *publisher_security_mode* viene **int**, non prevede alcun valore predefinito. **0** specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione, e **1** specifica l'autenticazione di Windows. Il valore **0** deve essere specificato per non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [ **@publisher_login**=] **'***publisher_login***'**  
 Account di accesso utilizzato per la connessione al server di pubblicazione. *publisher_login* viene **sysname**, non prevede alcun valore predefinito. *publisher_login* deve essere specificato quando *publisher_security_mode* viene **0**. Se *publisher_login* è NULL e server di pubblicazione*_ * * security_mode* è **1**, l'account Windows specificato *job_login* sarà utilizzato durante la connessione al server di pubblicazione.  
  
 [ **@publisher_password**=] **'***publisher_password***'**  
 Password utilizzata per la connessione al server di pubblicazione. *publisher_password* viene **nvarchar(524**, non prevede alcun valore predefinito.  
  
> [!IMPORTANT]  
>  Non archiviare informazioni di autenticazione in file script. Per migliorare la sicurezza, si consiglia di specificare nomi e password di accesso in fase di esecuzione.  
  
 [ **@job_login**=] **'***job_login***'**  
 Account di accesso per l'account di Windows utilizzato per l'esecuzione dell'agente. *job_login* viene **nvarchar(257)**, non prevede alcun valore predefinito. Questo account di Windows viene sempre utilizzato per le connessioni dell'agente al server di distribuzione. È necessario specificare questo parametro per la creazione di un nuovo processo per l'agente snapshot. *Non può essere modificato per non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *server di pubblicazione.*  
  
 [ **@job_password**=] **'***job_password***'**  
 Password dell'account di Windows utilizzato per l'esecuzione dell'agente. *job_password* viene **sysname**, non prevede alcun valore predefinito. È necessario specificare questo parametro per la creazione di un nuovo processo per l'agente snapshot.  
  
> [!IMPORTANT]  
>  Non archiviare informazioni di autenticazione in file script. Per migliorare la sicurezza, si consiglia di specificare nomi e password di accesso in fase di esecuzione.  
  
 [ **@publisher_type**=] **'***publisher_type***'**  
 Specifica il tipo di server di pubblicazione nei casi in cui il server di pubblicazione non sia in esecuzione in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *publisher_type* viene **sysname**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Specifica un server di pubblicazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Specifica un server di pubblicazione Oracle standard.|  
|**ORACLE GATEWAY**|Specifica un server di pubblicazione Oracle Gateway.|  
  
 Per ulteriori informazioni sulle differenze tra un server di pubblicazione Oracle e un server di pubblicazione Oracle Gateway, vedere [Cenni preliminari sulla pubblicazione Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_MSchange_snapshot_agent_properties** viene utilizzata nella replica snapshot, transazionale e di tipo merge.  
  
 È necessario specificare tutti i parametri durante l'esecuzione **sp_MSchange_snapshot_agent_properties**. Eseguire [sp_helppublication_snapshot](../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md) per restituire le proprietà correnti del processo dell'agente Snapshot.  
  
 Quando il server di pubblicazione viene eseguito in un'istanza di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva, è necessario utilizzare [sp_changepublication_snapshot](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) per modificare le proprietà di un processo dell'agente Snapshot.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server nel server di distribuzione possono eseguire **sp_MSchange_snapshot_agent_properties**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
  
