---
title: sp_addpullsubscription_agent (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_addpullsubscription_agent
- sp_addpullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addpullsubscription_agent
ms.assetid: b9c2eaed-6d2d-4b78-ae9b-73633133180b
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 82689b234a6294ef4c13c801ba88a7d700b0db44
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32993168"
---
# <a name="spaddpullsubscriptionagent-transact-sql"></a>sp_addpullsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
 
  Aggiunge un nuovo processo pianificato dell'agente per la sincronizzazione di una sottoscrizione pull con una pubblicazione transazionale. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addpullsubscription_agent [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]          , [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor = ] 'distributor' ]  
    [ , [ @distribution_db = ] 'distribution_db' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]  
    [ , [ @distributor_login = ] 'distributor_login' ]  
    [ , [ @distributor_password = ] 'distributor_password' ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
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
    [ , [ @distribution_jobid = ] distribution_jobid OUTPUT ]  
    [ , [ @encrypted_distributor_password = ] encrypted_distributor_password ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port = ] ftp_port ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]  
    [ , [ @working_directory = ] 'working_directory' ]  
    [ , [ @use_ftp = ] 'use_ftp' ]  
    [ , [ @publication_type = ] publication_type ]  
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @offloadagent = ] 'remote_agent_activation' ]  
    [ , [ @offloadserver = ] 'remote_agent_server_name']  
    [ , [ @job_name = ] 'job_name' ]  
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db=**] **' * * * publisher_db'*  
 Nome del database del server di pubblicazione. *publisher_db* viene **sysname**, con valore predefinito è NULL. *publisher_db* viene ignorata dal server di pubblicazione Oracle.  
  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@subscriber=**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Questo parametro è deprecato ed è ancora disponibile per compatibilità con gli script di versioni precedenti.  
  
 [  **@subscriber_db=**] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscriber_db* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Questo parametro è deprecato ed è ancora disponibile per compatibilità con gli script di versioni precedenti.  
  
 [  **@subscriber_security_mode=**] *subscriber_security_mode*  
 Modalità di sicurezza da utilizzare quando si effettua la connessione a un Sottoscrittore per la sincronizzazione. *subscriber_security_mode* viene **int,** con un valore predefinito è NULL. **0** specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. **1** specifica l'autenticazione di Windows.  
  
> [!NOTE]  
>  Questo parametro è deprecato ed è ancora disponibile per compatibilità con gli script di versioni precedenti. L'agente di distribuzione si connette sempre al Sottoscrittore locale utilizzando l'autenticazione di Windows. Se un valore diverso da NULL o **1** specificato per questo parametro, viene restituito un messaggio di avviso.  
  
 [  **@subscriber_login =**] **'***subscriber_login***'**  
 È l'account di accesso da utilizzare quando ci si connette a un sottoscrittore per la sincronizzazione. *subscriber_login* è **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Questo parametro è deprecato ed è ancora disponibile per compatibilità con gli script di versioni precedenti. Se viene specificato un valore per questo parametro, viene visualizzato un messaggio di avviso, ma il valore viene ignorato.  
  
 [  **@subscriber_password=**] **'***subscriber_password***'**  
 Password del Sottoscrittore. *subscriber_password* è obbligatorio se *subscriber_security_mode* è impostata su **0**. *subscriber_password* viene **sysname**, con un valore predefinito è NULL. Le password del Sottoscrittore vengono crittografate automaticamente.  
  
> [!NOTE]  
>  Questo parametro è deprecato ed è ancora disponibile per compatibilità con gli script di versioni precedenti. Se viene specificato un valore per questo parametro, viene visualizzato un messaggio di avviso, ma il valore viene ignorato.  
  
 [  **@distributor=**] **'***distributore***'**  
 Nome del server di distribuzione. *server di distribuzione* viene **sysname**, con un valore predefinito del valore specificato da *publisher*.  
  
 [  **@distribution_db=**] **'***distribution_db***'**  
 Nome del database di distribuzione. *distribution_db* viene **sysname**, con valore predefinito è NULL.  
  
 [  **@distributor_security_mode=**] *distributor_security_mode*  
 Modalità di sicurezza da utilizzare quando si effettua la connessione a un server di distribuzione per la sincronizzazione. *distributor_security_mode* viene **int**, il valore predefinito è **1**. **0** specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. **1** specifica l'autenticazione di Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [  **@distributor_login=**] **'***distributor_login***'**  
 Account di accesso da utilizzare quando ci si connette a un server di distribuzione per la sincronizzazione. *distributor_login* è obbligatorio se *distributor_security_mode* è impostata su **0**. *distributor_login* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@distributor_password =**] **'***distributor_password***'**  
 Password del database di distribuzione. *distributor_password* è obbligatorio se *distributor_security_mode* è impostata su **0**. *distributor_password* viene **sysname**, con un valore predefinito è NULL.  
  
> [!IMPORTANT]  
>  Non usare una password vuota. Usare una password complessa. Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@optional_command_line=**] **'***optional_command_line***'**  
 Riga di comando facoltativa fornita all'agente di distribuzione, Ad esempio, **- DefinitionFile** C:\Distdef.txt o **- CommitBatchSize** 10. *optional_command_line* viene **nvarchar(4000**, con un valore predefinito di una stringa vuota.  
  
 [  **@frequency_type=**] *frequency_type*  
 Frequenza di pianificazione dell'agente di distribuzione. *frequency_type* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2** (impostazione predefinita)|Su richiesta|  
|**4**|Ogni giorno|  
|**8**|Settimanale|  
|**16**|Mensile|  
|**32**|Mensile relativa|  
|**64**|Avvio automatico|  
|**128**|Periodica|  
  
> [!NOTE]  
>  Se si specifica un valore **64** fa sì che l'agente di distribuzione per l'esecuzione in modalità continua. Corrisponde all'impostazione di **-continua** parametro per l'agente. Per altre informazioni, vedere [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
 [  **@frequency_interval=**] *frequency_interval*  
 È il valore da applicare alla frequenza impostata da *frequency_type*. *frequency_interval* viene **int**, con un valore predefinito è 1.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Data dell'agente di distribuzione. Questo parametro viene utilizzato quando *frequency_type* è impostato su **32** (frequenza mensile relativa). *frequency_relative_interval* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**1** (impostazione predefinita)|Primo|  
|**2**|Secondo|  
|**4**|Terzo|  
|**8**|Quarto|  
|**16**|Ultimo|  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Fattore di occorrenza utilizzato da *frequency_type*. *frequency_recurrence_factor* viene **int**, il valore predefinito è **1**.  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Frequenza di ripianificazione durante il periodo definito. *frequency_subday* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**1** (impostazione predefinita)|Una volta|  
|**2**|Secondo|  
|**4**|Minuto|  
|**8**|Ora|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Intervallo per *frequency_subday*. *frequency_subday_interval* viene **int**, il valore predefinito è **1**.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Ora del giorno della prima esecuzione pianificata dell'agente di distribuzione nel formato HHMMSS. *active_start_time_of_day* viene **int**, il valore predefinito è **0**.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Ora del giorno dell'ultima esecuzione pianificata dell'agente di distribuzione, nel formato HHMMSS. *active_end_time_of_day* viene **int**, il valore predefinito è **0**.  
  
 [  **@active_start_date=**] *active_start_date*  
 Data della prima esecuzione pianificata dell'agente di distribuzione nel formato AAAAMMGG. *active_start_date* viene **int**, il valore predefinito è **0**.  
  
 [  **@active_end_date=**] *active_end_date*  
 Data dell'ultima esecuzione pianificata dell'agente di distribuzione, nel formato AAAAMMGG. *active_end_date* viene **int**, il valore predefinito è **0**.  
  
 [  **@distribution_jobid =**] *distribution_jobid * * * OUTPUT**  
 ID dell'agente di distribuzione per il processo. *distribution_jobid* viene **Binary (16)**, con valore NULL predefinito è un parametro di OUTPUT.  
  
 [  **@encrypted_distributor_password=**] *encrypted_distributor_password*  
 Impostazione *encrypted_distributor_password* non è più supportata. Il tentativo di impostare questo valore **bit** parametro **1** si verificherà un errore.  
  
 [  **@enabled_for_syncmgr=**] **'***enabled_for_syncmgr***'**  
 È se è possibile sincronizzare la sottoscrizione tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Gestione sincronizzazione. *enabled_for_syncmgr* viene **nvarchar(5**, con un valore predefinito è FALSE. Se **false**, la sottoscrizione non è registrata con Gestione sincronizzazione. Se **true**, la sottoscrizione viene registrata con Gestione sincronizzazione e può essere sincronizzata senza avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 [  **@ftp_address=**] **'***ftp_address***'**  
 Disponibile solo per compatibilità con le versioni precedenti.  
  
 [  **@ftp_port=**] *ftp_port*  
 Disponibile solo per compatibilità con le versioni precedenti.  
  
 [  **@ftp_login=**] **'***ftp_login***'**  
 Disponibile solo per compatibilità con le versioni precedenti.  
  
 [  **@ftp_password=**] **'***ftp_password***'**  
 Disponibile solo per compatibilità con le versioni precedenti.  
  
 [  **@alt_snapshot_folder=** ] **' * * * alternate_snapshot_folder'*  
 Specifica la posizione della cartella alternativa per lo snapshot. *alternate_snapshot_folder* viene **nvarchar(255**, con un valore predefinito è NULL.  
  
 [ **@working_directory**=] **'***working_director***'**  
 Nome della directory di lavoro utilizzata per archiviare i file dei dati e di schema per la pubblicazione *working_directory* viene **nvarchar(255**, con un valore predefinito è NULL. Il nome deve essere specificato in formato UNC.  
  
 [ **@use_ftp**=] **'***use_ftp***'**  
 Specifica l'utilizzo di FTP anziché del protocollo normale per il recupero di snapshot. *use_ftp* viene **nvarchar(5**, con un valore predefinito è FALSE.  
  
 [ **@publication_type**=] *publication_type*  
 Specifica il tipo di replica della pubblicazione. *publication_type* è un **tinyint** con valore predefinito è **0**. Se **0**, pubblicazione è un tipo di transazione. Se **1**, pubblicazione è di tipo snapshot. Se **2**, pubblicazione è di tipo merge.  
  
 [ **@dts_package_name**=] **'***dts_package_name***'**  
 Nome del pacchetto DTS. *dts_package_name* è un **sysname** con un valore predefinito è NULL. Per specificare, ad esempio, il nome di pacchetto `DTSPub_Package`, il parametro deve essere `@dts_package_name = N'DTSPub_Package'`.  
  
 [ **@dts_package_password**=] **'***dts_package_password***'**  
 Password del pacchetto, se è disponibile. *dts_package_password* viene **sysname** con un valore predefinito è NULL, ovvero una password non è incluso nel pacchetto.  
  
> [!NOTE]  
>  Se è necessario specificare una password *dts_package_name* specificato.  
  
 [ **@dts_package_location**=] **'***dts_package_location***'**  
 Specifica la posizione del pacchetto. *dts_package_location* è un **nvarchar(12**, il valore predefinito è **sottoscrittore**. Il percorso del pacchetto può essere **distributore** o **sottoscrittore**.  
  
 [ **@reserved**=] **'***riservato***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@offloadagent**=] '*remote_agent_activation*'  
 > [!NOTE]  
>  L'attivazione remota dell'agente è deprecata e non è più supportata. Questo parametro è supportato solo per compatibilità con gli script di versioni precedenti. Impostazione *remote_agent_activation* su un valore diverso da **false** genererà un errore.  
  
 [ **@offloadserver**=] '*remote_agent_server_name*'  
 > [!NOTE]  
>  L'attivazione remota dell'agente è deprecata e non è più supportata. Questo parametro è supportato solo per compatibilità con gli script di versioni precedenti. Impostazione *remote_agent_server_name* su qualsiasi valore diverso da NULL, verrà generato un errore.  
  
 [ **@job_name**=] '*job_name*'  
 Nome di un processo esistente dell'agente. *job_name* viene **sysname**, con valore predefinito è NULL. Questo parametro viene specificato solo quando la sottoscrizione verrà sincronizzata mediante un processo esistente anziché un nuovo processo creato (impostazione predefinita). Se non si è un membro del **sysadmin** ruolo predefinito del server, è necessario specificare *job_login* e *job_password* quando si specifica *job_name*.  
  
 [ **@job_login**=] **'***job_login***'**  
 Account di accesso per l'account di Windows utilizzato per l'esecuzione dell'agente. *job_login* viene **nvarchar(257)**, non prevede alcun valore predefinito. Questo account di Windows viene sempre utilizzato per le connessioni dell'agente al Sottoscrittore.  
  
 [ **@job_password**=] **'***job_password***'**  
 Password dell'account di Windows utilizzato per l'esecuzione dell'agente. *job_password* viene **sysname**, non prevede alcun valore predefinito.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addpullsubscription_agent** viene utilizzata nella replica snapshot e transazionale.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addpullsubscription_agent**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una sottoscrizione pull](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
