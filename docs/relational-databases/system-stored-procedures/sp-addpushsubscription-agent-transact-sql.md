---
title: sp_addpushsubscription_agent (Transact-SQL) | Documenti Microsoft
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
- sp_addpushsubscription_agent_TSQL
- sp_addpushsubscription_agent
helpviewer_keywords:
- sp_addpushsubscription_agent
ms.assetid: 1fdd2052-50d8-4318-8aa7-fc635d5cad18
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2730a5ceb1f976605f4a784b71194f4b9caceea5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spaddpushsubscriptionagent-transact-sql"></a>sp_addpushsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un nuovo processo di agente pianificato per sincronizzare una sottoscrizione push di una pubblicazione transazionale. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
> [!IMPORTANT]  
>  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addpushsubscription_agent [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
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
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @distribution_job_name = ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @subscriber_provider = ] 'subscriber_provider' ]   
    [ , [ @subscriber_datasrc = ] 'subscriber_datasrc' ]   
    [ , [ @subscriber_location = ] 'subscriber_location' ]  
    [ , [ @subscriber_provider_string = ] 'subscriber_provider_string' ]   
    [ , [ @subscriber_catalog = ] 'subscriber_catalog' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@subscriber =**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_db =**] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscriber_db* viene **sysname**, con un valore predefinito è NULL. Per un non - Sottoscrittore SQL Server, specificare un valore di **(destinazione predefinita)** per *subscriber_db*.  
  
 [  **@subscriber_security_mode =**] *subscriber_security_mode*  
 Modalità di sicurezza da utilizzare quando si effettua la connessione a un Sottoscrittore per la sincronizzazione. *subscriber_security_mode* viene **int**, con un valore predefinito è 1. **0** specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. **1** specifica l'autenticazione di Windows.  
  
> [!IMPORTANT]  
>  Per le sottoscrizioni ad aggiornamento in coda utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le connessioni ai Sottoscrittori e specificare un account diverso per la connessione a ogni Sottoscrittore. Per tutte le altre sottoscrizioni utilizzare l'autenticazione di Windows.  
  
 [  **@subscriber_login =**] **'***subscriber_login***'**  
 Account di accesso da utilizzare quando ci si connette a un Sottoscrittore per la sincronizzazione. *subscriber_login* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_password =**] **'***subscriber_password***'**  
 Password del Sottoscrittore. *subscriber_password* è obbligatorio se *subscriber_security_mode* è impostata su **0**. *subscriber_password* viene **sysname**, con un valore predefinito è NULL. Le password del Sottoscrittore vengono crittografate automaticamente.  
  
> [!IMPORTANT]  
>  Non usare una password vuota. Usare una password complessa. Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@job_login =** ] **'***job_login***'**  
 Account di accesso per l'account di Windows utilizzato per l'esecuzione dell'agente. *job_login* viene **nvarchar(257)**, con valore predefinito è NULL. Questo account di Windows viene sempre utilizzato per le connessioni dell'agente al server di distribuzione e per le connessioni al Sottoscrittore quando si utilizza l'autenticazione integrata di Windows.  
  
 [  **@job_password =** ] **'***job_password***'**  
 Password dell'account di Windows utilizzato per l'esecuzione dell'agente. *job_password* viene **sysname**, non prevede alcun valore predefinito.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [ **@job_name =** ] **'***job_name***'**  
 Nome di un processo esistente dell'agente. *job_name* viene **sysname**, con valore predefinito è NULL. Questo parametro viene specificato solo quando la sottoscrizione verrà sincronizzata mediante un processo esistente anziché un nuovo processo creato (impostazione predefinita). Se non si è un membro del **sysadmin** ruolo predefinito del server, è necessario specificare *job_login* e *job_password* quando si specifica *job_name*.  
  
 [  **@frequency_type =** ] *frequency_type*  
 Frequenza di pianificazione dell'agente di distribuzione. *frequency_type* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Su richiesta|  
|**4**|Ogni giorno|  
|**8**|Settimanale|  
|**16**|Mensile|  
|**32**|Mensile relativa|  
|**64** (impostazione predefinita)|Avvio automatico|  
|**128**|Periodica|  
  
> [!NOTE]  
>  Se si specifica un valore **64** fa sì che l'agente di distribuzione per l'esecuzione in modalità continua. Corrisponde all'impostazione di **-continua** parametro per l'agente. Per altre informazioni, vedere [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 È il valore da applicare alla frequenza impostata da *frequency_type*. *frequency_interval* viene **int**, con un valore predefinito è 1.  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 Data dell'agente di distribuzione. Questo parametro viene utilizzato quando *frequency_type* è impostato su **32** (frequenza mensile relativa). *frequency_relative_interval* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**1** (impostazione predefinita)|Primo|  
|**2**|Secondo|  
|**4**|Terzo|  
|**8**|Quarto|  
|**16**|Ultimo|  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 Fattore di occorrenza utilizzato da *frequency_type*. *frequency_recurrence_factor* viene **int**, con un valore predefinito è 0.  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 Frequenza di ripianificazione durante il periodo definito. *frequency_subday* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Secondo|  
|**4** (impostazione predefinita)|Minuto|  
|**8**|Ora|  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 Intervallo per *frequency_subday*. *frequency_subday_interval* viene **int**, con un valore predefinito è 5.  
  
 [  **@active_start_time_of_day =** ] *active_start_time_of_day*  
 Ora del giorno della prima esecuzione pianificata dell'agente di distribuzione nel formato HHMMSS. *active_start_time_of_day* viene **int**, con un valore predefinito è 0.  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 Ora del giorno dell'ultima esecuzione pianificata dell'agente di distribuzione, nel formato HHMMSS. *active_end_time_of_day* viene **int**, con un valore predefinito è 235959.  
  
 [ **@active_start_date =** ] *active_start_date*  
 Data della prima esecuzione pianificata dell'agente di distribuzione nel formato AAAAMMGG. *active_start_date* viene **int**, con un valore predefinito è 0.  
  
 [ **@active_end_date =** ] *active_end_date*  
 Data dell'ultima esecuzione pianificata dell'agente di distribuzione, nel formato AAAAMMGG. *active_end_date* viene **int**, con un valore predefinito è 99991231.  
  
 [  **@dts_package_name =** ] **'***dts_package_name***'**  
 Specifica il nome del pacchetto Data Transformation Services (DTS). *dts_package_name* è un **sysname** con un valore predefinito è NULL. Per specificare, ad esempio, il nome di pacchetto `DTSPub_Package`, il parametro deve essere `@dts_package_name = N'DTSPub_Package'`.  
  
 [  **@dts_package_password =** ] **'***dts_package_password***'**  
 Password necessaria per l'esecuzione del pacchetto. *dts_package_password* viene **sysname** con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Se è necessario specificare una password *dts_package_name* specificato.  
  
 [  **@dts_package_location =** ] **'***dts_package_location***'**  
 Specifica la posizione del pacchetto. *dts_package_location* è un **nvarchar(12**, con un valore predefinito è DISTRIBUTOR. Il percorso del pacchetto può essere **distributore** o **sottoscrittore**.  
  
 [  **@enabled_for_syncmgr =** ] **'***enabled_for_syncmgr***'**  
 È se è possibile sincronizzare la sottoscrizione tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Gestione sincronizzazione. *enabled_for_syncmgr* viene **nvarchar(5**, con un valore predefinito è FALSE. Se **false**, la sottoscrizione non è registrata con Gestione sincronizzazione. Se **true**, la sottoscrizione viene registrata con Gestione sincronizzazione e può essere sincronizzata senza avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 [  **@distribution_job_name =** ] **'***job_name***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@publisher =** ] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, con valore predefinito è NULL.  
  
 [  **@subscriber_provider=** ] **'***subscriber_provider***'**  
 ProgID univoco con cui è registrato il provider OLE DB per l'origine dati non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *subscriber_provider* viene **sysname**, con valore predefinito è NULL. *subscriber_provider* deve essere univoco per il provider OLE DB installato nel server di distribuzione. *subscriber_provider* è supportata solo per non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori.  
  
 [  **@subscriber_datasrc=** ] **'***subscriber_datasrc***'**  
 Nome dell'origine dei dati riconosciuto dal provider OLE DB. *subscriber_datasrc* viene **nvarchar(4000**, con valore predefinito è NULL. *subscriber_datasrc* viene passato come proprietà DBPROP_INIT_DATASOURCE per inizializzare il provider OLE DB. *subscriber_datasrc* è supportata solo per non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori.  
  
 [  **@subscriber_location=** ] **'***subscriber_location***'**  
 Percorso del database riconosciuto dal provider OLE DB. *subscriber_location* viene **nvarchar(4000**, con valore predefinito è NULL. *subscriber_location* viene passato come proprietà DBPROP_INIT_LOCATION per inizializzare il provider OLE DB. *subscriber_location* è supportata solo per non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori.  
  
 [  **@subscriber_provider_string=** ] **'***subscriber_provider_string***'**  
 Stringa di connessione specifica del provider OLE DB che consente di identificare l'origine dei dati. *subscriber_provider_string* viene **nvarchar(4000**, con valore predefinito è NULL. *subscriber_provider_string* è passato a IDataInitialize o impostato come proprietà DBPROP_INIT_PROVIDERSTRING per inizializzare il provider OLE DB. *subscriber_provider_string* è supportata solo per non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori.  
  
 [  **@subscriber_catalog=** ] **'***subscriber_catalog***'**  
 Catalogo da utilizzare per stabilire una connessione al provider OLE DB *subscriber_catalog* viene **sysname**, con valore predefinito è NULL. *subscriber_catalog* viene passato come proprietà DBPROP_INIT_CATALOG per inizializzare il provider OLE DB. *subscriber_catalog* è supportata solo per non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addpushsubscription_agent** viene utilizzata nella replica snapshot e transazionale.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addpushsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addpushsubscription_agent**.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Creare una sottoscrizione per un Sottoscrittore non SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [stored procedure sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
