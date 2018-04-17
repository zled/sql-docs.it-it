---
title: sp_helpdistpublisher (Transact-SQL) | Documenti Microsoft
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
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce3c9b89c29bb9e387819ddbc15996d6d072b979
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpdistpublisher-transact-sql"></a>sp_helpdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le proprietà dei server di pubblicazione utilizzando un server di distribuzione. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdistpublisher [ [ @publisher=] 'publisher']   
    [ , [ @check_user = ] check_user  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=** ] **'***publisher***'**  
 Server di pubblicazione per il quale vengono restituite le proprietà. *server di pubblicazione* viene **sysname**, il valore predefinito è **%**.  
  
 [  **@check_user=** ] *check_user*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del server di pubblicazione.|  
|**distribution_db**|**sysname**|Database di distribuzione per il server di pubblicazione specificato.|  
|**security_mode**|**int**|Modalità di sicurezza utilizzata dagli agenti di replica per connettersi al server di pubblicazione per le sottoscrizioni ad aggiornamento in coda o a un server di pubblicazione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione<br /><br /> **1** = autenticazione di Windows|  
|**login**|**sysname**|Nome account di accesso utilizzato dagli agenti di replica per connettersi al server di pubblicazione per le sottoscrizioni ad aggiornamento in coda o a un server di pubblicazione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524**|Password restituita in formato crittografato semplice. La password è diverso da NULL per gli utenti **sysadmin**.|  
|**Attiva**|**bit**|Indica se un server di pubblicazione remoto utilizza il server locale come server di distribuzione:<br /><br /> **0** = No<br /><br /> **1** = Sì|  
|**working_directory**|**nvarchar(255)**|Nome della directory di lavoro.|  
|**attendibile**|**bit**|Indica se la password è obbligatoria per la connessione del server di pubblicazione al server di distribuzione. Per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive, deve sempre restituire **0**, il che significa che la password è obbligatoria.|  
|**thirdparty_flag**|**bit**|Indica se la pubblicazione è abilitata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o da un'applicazione di terze parti:<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oracle o server di pubblicazione Oracle Gateway.<br /><br /> **1** = server di pubblicazione è stato integrato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite un'applicazione di terze parti.|  
|**publisher_type**|**sysname**|Tipo di server di pubblicazione. Può essere uno dei tipi seguenti:<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
|**publisher_data_source**|**nvarchar(4000)**|Nome dell'origine dati OLE DB nel server di pubblicazione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpdistpublisher** viene utilizzata in tutti i tipi di replica.  
  
 **sp_helpdistpublisher** non verrà visualizzato l'account di accesso del server di pubblicazione o per impostare una password nel risultato non -**sysadmin** gli account di accesso.  
  
## <a name="permissions"></a>Autorizzazioni  
 I membri del **sysadmin** ruolo predefinito del server può essere eseguita **sp_helpdistpublisher** per qualsiasi server di pubblicazione utilizzando il server locale come server di distribuzione. I membri del **db_owner** ruolo predefinito del database o **replmonitor** può essere eseguita in un database di distribuzione **sp_helpdistpublisher** per qualsiasi server di pubblicazione che utilizza quel database di distribuzione. Elenco di utenti l'accesso alla pubblicazione per una pubblicazione specificato *publisher* possono eseguire **sp_helpdistpublisher**. Se *publisher* viene omesso, vengono restituite informazioni per tutti i server di pubblicazione che l'utente disponga dei diritti di accesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
