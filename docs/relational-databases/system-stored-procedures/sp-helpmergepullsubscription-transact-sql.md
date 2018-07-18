---
title: sp_helpmergepullsubscription (Transact-SQL) | Documenti Microsoft
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
- sp_helpmergepullsubscription
- sp_helpmergepullsubscription_TSQL
helpviewer_keywords:
- sp_helpmergepullsubscription
ms.assetid: 6f3125f3-0dfa-40bd-b725-8aa1591234f6
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 905ead01709a932639f72e874f1246228f2f9c21
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33003938"
---
# <a name="sphelpmergepullsubscription-transact-sql"></a>sp_helpmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle sottoscrizioni pull esistenti in un Sottoscrittore. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpmergepullsubscription [ [ @publication=] 'publication']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
```  
  
## <a name="argument"></a>Argomento  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, il valore predefinito è **%**. Se *pubblicazione* è **%**, vengono restituite informazioni su tutte le pubblicazioni di tipo merge e le sottoscrizioni nel database corrente.  
  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione*viene **sysname**, il valore predefinito è **%**.  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 Nome del database del server di pubblicazione. *publisher_db*viene **sysname**, il valore predefinito è **%**.  
  
 [  **@subscription_type=**] **'***subscription_type***'**  
 Indica se visualizzare le sottoscrizioni pull. *subscription_type*viene **nvarchar(10)**, il valore predefinito è **'pull'**. I valori validi sono **'push'**, **'pull'**, o **'both'**.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**nvarchar(1000)**|Nome della sottoscrizione.|  
|**Pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**subscriber**|**sysname**|Nome del Sottoscrittore.|  
|**subscriber_db**|**sysname**|Nome del database di sottoscrizione.|  
|**status**|**int**|Stato della sottoscrizione:<br /><br /> **0** = sottoscrizione inattiva<br /><br /> **1** = sottoscrizione attiva<br /><br /> **2** = sottoscrizione eliminata<br /><br /> **3** = sottoscrizione scollegata<br /><br /> **4** = sottoscrizione collegata<br /><br /> **5** = sottoscrizione contrassegnata per la reinizializzazione al caricamento<br /><br /> **6** = collegamento della sottoscrizione non riuscito<br /><br /> **7** = sottoscrizione ripristinata dal backup|  
|**subscriber_type**|**int**|Tipo di Sottoscrittore:<br /><br /> **1** = globale<br /><br /> **2** = locale<br /><br /> **3** = anonima|  
|**subscription_type**|**int**|Tipo di sottoscrizione:<br /><br /> **0** = push<br /><br /> **1** = pull<br /><br /> **2** = anonima|  
|**priority**|**float(8)**|Priorità della sottoscrizione. Il valore deve essere minore di **100,00**.|  
|**sync_type**|**tinyint**|Tipo di sincronizzazione per la sottoscrizione:<br /><br /> **1** = automatica<br /><br /> **2** = non viene utilizzato lo snapshot.|  
|**description**|**nvarchar(255)**|Breve descrizione della sottoscrizione pull.|  
|**merge_jobid**|**binary(16)**|ID di processo dell'agente di merge.|  
|**enabled_for_syncmgr**|**int**|Indica se è possibile sincronizzare la sottoscrizione tramite Gestione sincronizzazione [!INCLUDE[msCoName](../../includes/msconame-md.md)].|  
|**last_updated**|**nvarchar(26)**|Ora in cui l'agente di merge ha eseguito l'ultima sincronizzazione della sottoscrizione.|  
|**publisher_login**|**sysname**|Nome dell'account di accesso del server di pubblicazione.|  
|**publisher_password**|**sysname**|Password del server di pubblicazione.|  
|**publisher_security_mode**|**int**|Modalità di sicurezza del server di pubblicazione:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione<br /><br /> **1** = autenticazione di Windows|  
|**Server di distribuzione**|**sysname**|Nome del server di distribuzione.|  
|**distributor_login**|**sysname**|Nome dell'account di accesso del server di distribuzione.|  
|**distributor_password**|**sysname**|Password per il server di distribuzione.|  
|**distributor_security_mode**|**int**|Modalità di sicurezza del server di distribuzione:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione<br /><br /> **1** = autenticazione di Windows|  
|**ftp_address**|**sysname**|Disponibile per compatibilità con le versioni precedenti. Indirizzo di rete del servizio FTP per il server di distribuzione.|  
|**ftp_port**|**int**|Disponibile per compatibilità con le versioni precedenti. Numero di porta del servizio FTP per il database di distribuzione.|  
|**ftp_login**|**sysname**|Disponibile per compatibilità con le versioni precedenti. Nome utente utilizzato per la connessione al servizio FTP.|  
|**ftp_password**|**sysname**|Disponibile per compatibilità con le versioni precedenti. Password utente utilizzata per la connessione al servizio FTP.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Percorso di archiviazione della cartella snapshot, se diverso o aggiuntivo rispetto a quello predefinito.|  
|**working_directory**|**nvarchar(255)**|Percorso completo della directory in cui vengono trasferiti i file di snapshot tramite il servizio FTP, se l'opzione corrispondente è stata specificata.|  
|**use_ftp**|**bit**|Indica che la sottoscrizione viene inserita nella pubblicazione tramite Internet e che le proprietà di indirizzamento FTP sono configurate. Se **0**, la sottoscrizione non utilizza FTP. Se **1**, la sottoscrizione utilizza FTP.|  
|**offload_agent**|**bit**|Specifica se l'agente può essere attivato ed eseguito in remoto. Se **0**, l'agente non può essere attivato in remoto.|  
|**offload_server**|**sysname**|Nome del server utilizzato per l'attivazione remota.|  
|**use_interactive_resolver**|**int**|Specifica se durante la fase di riconciliazione viene utilizzato il sistema di risoluzione dei conflitti interattivo. Se **0**, non viene utilizzato il sistema di risoluzione interattivo.|  
|**subid**|**uniqueidentifier**|ID del Sottoscrittore.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Percorso della cartella in cui vengono salvati i file di snapshot.|  
|**last_sync_status**|**int**|Stato della sincronizzazione:<br /><br /> **1** = avvio in corso<br /><br /> **2** = ha avuto esito positivo<br /><br /> **3** = in corso<br /><br /> **4** = inattivo<br /><br /> **5** = nuovo tentativo dopo un precedente errore<br /><br /> **6** = non è riuscita<br /><br /> **7** = convalida non riuscita<br /><br /> **8** = convalida riuscita<br /><br /> **9** = richiesta di chiusura|  
|**last_sync_summary**|**sysname**|Descrizione dei risultati dell'ultima sincronizzazione.|  
|**use_web_sync**|**bit**|Specifica se la sottoscrizione può essere sincronizzata tramite HTTPS, dove il valore **1** indica che questa funzionalità è abilitata.|  
|**internet_url**|**nvarchar(260)**|URL che rappresenta la posizione del listener per la replica per la sincronizzazione Web.|  
|**internet_login**|**nvarchar(128)**|Account di accesso utilizzato dall'agente di merge per la connessione al server Web che ospita la sincronizzazione Web tramite l'autenticazione di base.|  
|**internet_password**|**nvarchar(524**|Password di accesso utilizzata dall'agente di merge per la connessione al server Web in cui viene eseguita la sincronizzazione Web tramite l'autenticazione di base.|  
|**internet_security_mode**|**int**|Modalità di autenticazione utilizzata per la connessione al server Web in cui viene eseguita la sincronizzazione Web. Il valore **1** indica l'autenticazione di Windows, mentre il valore di **0** significa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione.|  
|**internet_timeout**|**int**|Periodo di tempo, espresso in secondi, al termine del quale una richiesta di sincronizzazione Web scade.|  
|**Nome host**|**nvarchar(128)**|Specifica un valore di overload per [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) quando questa funzione viene utilizzata nella clausola WHERE di un filtro di riga con parametri.|  
|**job_login**|**nvarchar(512)**|È l'account di Windows con cui viene eseguito l'agente di Merge, viene restituito nel formato *dominio*\\*username*.|  
|**job_password**|**sysname**|Per motivi di sicurezza, il valore "**\*\*\*\*\*\*\*\*\*\***" è sempre restituito.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpmergepullsubscription** viene utilizzata nella replica di tipo merge. Nel set di risultati, la data restituita **last_updated** sia formattata come *YYYYMMDD hh*.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_helpmergepullsubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
