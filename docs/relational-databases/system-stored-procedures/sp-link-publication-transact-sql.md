---
title: sp_link_publication (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_link_publication_TSQL
- sp_link_publication
helpviewer_keywords: sp_link_publication
ms.assetid: 1945ed24-f9f1-4af6-94ca-16d8e864706e
caps.latest.revision: "41"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d23e5dc68133f607d5058351bf8b620d13aaaa5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="splinkpublication-transact-sql"></a>sp_link_publication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta le informazioni di configurazione e sicurezza utilizzate dai trigger di sincronizzazione dei server di sottoscrizione ad aggiornamento immediato durante la connessione al server di pubblicazione. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
> [!IMPORTANT]  
>  Quando si configura un server di pubblicazione con un server di distribuzione remoto, i valori specificati per tutti i parametri, inclusi *job_login* e *job_password*, vengono inviati al server di distribuzione come testo normale. È consigliabile crittografare la connessione tra il server di pubblicazione e il server di distribuzione remoto prima di eseguire questa stored procedure. Per altre informazioni, vedere [Abilitare le connessioni crittografate al motore di database &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
> [!IMPORTANT]  
>  In determinate condizioni, questa stored procedure può non riuscire se il sottoscrittore esegue [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 o versione successivo e il server di pubblicazione è in esecuzione una versione precedente. In caso di esito negativo della stored procedure in questo scenario, aggiornare il server di pubblicazione a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 o versioni successive.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_link_publication [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'   
        , [ @publication = ] 'publication'   
        , [ @security_mode = ] security_mode  
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ]'password' ]  
    [ , [ @distributor = ] 'distributor' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione a cui collegarsi. *server di pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db** =] **'***publisher_db***'**  
 Nome del database del server di pubblicazione a cui collegarsi. *publisher_db* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione a cui collegarsi. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@security_mode** =] *security_mode*  
 Modalità di sicurezza utilizzata dal Sottoscrittore per la connessione a un server di pubblicazione remoto per l'aggiornamento immediato. *security_mode* è **int**, i possibili valori sono i seguenti. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**0**|Usa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione con l'account di accesso specificato in questa stored procedure come *accesso* e *password*.<br /><br /> Nota: nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], questa opzione viene utilizzata per specificare una chiamata dinamica di procedura remota (RPC).|  
|**1**|Utilizza il contesto di sicurezza (autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o autenticazione di Windows) dell'utente che esegue la modifica nel Sottoscrittore.<br /><br /> Nota: Questo account deve esistere anche nel server di pubblicazione disponga di privilegi sufficienti. Se si utilizza l'autenticazione di Windows è necessario che sia supportata la delega degli account di sicurezza.|  
|**2**|Usa un accesso server collegato esistente definito dall'utente creato utilizzando **sp_link_publication**.|  
  
 [  **@login** =] **'***accesso***'**  
 Account di accesso. *account di accesso* è **sysname**, con un valore predefinito è NULL. Questo parametro deve essere specificato quando *security_mode* è **0**.  
  
 [  **@password** =] **'***password***'**  
 Password. *password* è **sysname**, con un valore predefinito è NULL. Questo parametro deve essere specificato quando *security_mode* è **0**.  
  
 [  **@distributor=** ] **'***distributore***'**  
 Nome del server di distribuzione. *server di distribuzione* è **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_link_publication** viene utilizzato dalle sottoscrizioni ad aggiornamento immediato nella replica transazionale.  
  
 **sp_link_publication** può essere utilizzato per le sottoscrizioni push e pull. Questa stored procedure può essere chiamata prima o dopo la creazione della sottoscrizione. Una voce viene inserita o aggiornata nel [MSsubscription_properties &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) tabella di sistema.  
  
 Per le sottoscrizioni push, può essere rimossa la voce da [sp_subscription_cleanup &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md). Per le sottoscrizioni pull, può essere rimossa la voce da [sp_droppullsubscription &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md) o [sp_subscription_cleanup &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md). È inoltre possibile chiamare **sp_link_publication** con una password NULL per eliminare la voce di [MSsubscription_properties &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) tabella di sistema per motivi di sicurezza.  
  
 La modalità predefinita utilizzata in un Sottoscrittore ad aggiornamento immediato per la connessione al server di pubblicazione non consente la connessione tramite l'autenticazione di Windows. Per eseguire la connessione con questa modalità di autenticazione, è necessario configurare un server collegato per il server di pubblicazione e il Sottoscrittore ad aggiornamento immediato deve utilizzare questa connessione per l'aggiornamento del Sottoscrittore. Questa operazione richiede il **sp_link_publication** può essere eseguito con *security_mode* = **2**. Se si utilizza l'autenticazione di Windows è necessario che sia supportata la delega degli account di sicurezza.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent_failover](../../relational-databases/replication/codesnippet/tsql/sp-link-publication-tran_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_link_publication**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_droppullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [sp_subscription_cleanup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
