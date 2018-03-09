---
title: sp_changemergesubscription (Transact-SQL) | Documenti Microsoft
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
f1_keywords:
- sp_changemergesubscription_TSQL
- sp_changemergesubscription
helpviewer_keywords:
- sp_changemergesubscription
ms.assetid: fd820f35-c189-4e2d-884d-b60c1c469f58
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3fef5efe16fbc6a3684e077ef8dfca38b839753
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spchangemergesubscription-transact-sql"></a>sp_changemergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le proprietà selezionate di una sottoscrizione push di tipo merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
> [!IMPORTANT]  
>  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changemergesubscription [ [ @publication= ] 'publication' ]  
    [ , [ @subscriber= ] 'subscriber'  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione da modificare. *pubblicazione* è **sysname**, con un valore predefinito è NULL. La pubblicazione deve essere già esistente e conforme alle regole per gli identificatori.  
  
 [  **@subscriber=**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_db=**] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscriber_db*è **sysname**, con un valore predefinito è NULL.  
  
 [  **@property=**] **'***proprietà***'**  
 Proprietà da modificare per la pubblicazione specificata. *proprietà* è **sysname**, e può essere uno dei valori nella tabella.  
  
 [  **@value=**] **'***valore***'**  
 Nuovo valore per l'oggetto specificato *proprietà*. *valore* è **nvarchar (255)**, e può essere uno dei valori nella tabella.  
  
|Proprietà|Valore|Description|  
|--------------|-----------|-----------------|  
|**Descrizione**||Descrizione della sottoscrizione di tipo merge.|  
|**priorità**||Priorità della sottoscrizione. La priorità viene utilizzata dal sistema di risoluzione predefinito per eseguire una selezione in caso di conflitti.|  
|**merge_job_login**||Account di accesso per l'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows utilizzato per l'esecuzione dell'agente.|  
|**merge_job_password**||Password dell'account di Windows utilizzato per l'esecuzione dell'agente.|  
|**publisher_security_mode**|**1**|Esegue la connessione al server di pubblicazione utilizzando l'autenticazione di Windows.|  
||**0**|Esegue la connessione al server di pubblicazione utilizzando l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_login**||Nome dell'account di accesso al server di pubblicazione.|  
|**publisher_password**||Password complessa per l'account di accesso fornito per il server di pubblicazione.|  
|**subscriber_security_mode**|**1**|Esegue la connessione al Sottoscrittore utilizzando l'autenticazione di Windows.|  
||**0**|Esegue la connessione al Sottoscrittore utilizzando l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**subscriber_login**||Nome dell'account di accesso nel Sottoscrittore.|  
|**subscriber_password**||Password complessa per l'account di accesso fornito per il Sottoscrittore.|  
|**sync_type**|**Automatico**|Lo schema e i dati iniziali per le tabelle pubblicate vengono trasferiti per primi nel Sottoscrittore.|  
||**Nessuno**|Il Sottoscrittore dispone già dello schema e dei dati iniziali per le tabelle pubblicate. Le tabelle di sistema e i dati vengono sempre trasferiti.|  
|**use_interactive_resolver**|**true**|Consente la risoluzione interattiva dei conflitti per tutti gli articoli che la prevedono.|  
||**false**|I conflitti vengono risolti automaticamente utilizzando un sistema di risoluzione predefinito o personalizzato.|  
|NULL (predefinito)|NULL (predefinito)||  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_changemergesubscription** viene utilizzata nella replica di tipo merge.  
  
 Dopo la modifica dell'account di accesso o della password di un agente, è necessario arrestare e riavviare l'agente per rendere effettiva la modifica.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_changemergesubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
