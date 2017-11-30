---
title: sp_dropremotelogin (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_dropremotelogin
- sp_dropremotelogin_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_dropremotelogin
ms.assetid: 9f097652-a286-40b2-be73-568d77ada698
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9edb5db6819950e517f26bee0d144ef3cf567bc
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spdropremotelogin-transact-sql"></a>sp_dropremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un account di accesso remoto di cui è stato eseguito il mapping a un account di accesso locale utilizzato per eseguire stored procedure remote nel server locale in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilizzare i server collegati e le stored procedure per i server collegati in alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dropremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@remoteserver =** ] **'***remoteserver***'**  
 Nome del server remoto di cui è stato eseguito il mapping all'account di accesso remoto che si desidera rimuovere. *remoteserver* è **sysname**, non prevede alcun valore predefinito. *remoteserver* deve essere già esistente.  
  
 [  **@loginame =** ] **'***accesso***'**  
 Nome facoltativo dell'account di accesso nel server locale associato al server remoto. *account di accesso* è **sysname**, con un valore predefinito è NULL. *account di accesso* deve già esistere se specificato.  
  
 [  **@remotename =** ] **'***remote_name***'**  
 Nome facoltativo dell'account di accesso remoto che viene eseguito il mapping a *accesso* durante l'accesso dal server remoto. *remote_name* è **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Se solo *remoteserver* viene specificato, vengono rimossi tutti gli account di accesso remoto per il server remoto dal server locale. Se *accesso* è specificato, tutti remoto agli account di accesso *remoteserver* mappato allo specifico account di accesso locale vengono rimosse dal server locale. Se *remote_name* viene anche specificato solo l'account di accesso remoto per l'utente remoto da *remoteserver* viene rimosso dal server locale.  
  
 Per aggiungere utenti al server locale, utilizzare **sp_addlogin**. Per rimuovere utenti dal server locale, utilizzare **sp_droplogin**.  
  
 Gli account di accesso remoti sono necessari solo in caso di utilizzo di versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 e versioni successive utilizzano invece account di accesso dei server collegati. Utilizzare **sp_addlinkedsrvlogin** e **sp_droplinkedsrvlogin** per aggiungere e rimuovere gli accessi server collegato.  
  
 **sp_dropremotelogin** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **sysadmin** o **securityadmin** ruoli predefiniti del server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-all-remote-logins-for-a-remote-server"></a>A. Eliminazione di tutti gli account di accesso remoti per un server remoto  
 Nell'esempio seguente viene rimossa la voce relativa al server remoto `ACCOUNTS`, con la conseguente rimozione di tutti i mapping tra gli account di accesso nel server locale e gli account di accesso remoti nel server remoto.  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-dropping-a-login-mapping"></a>B. Eliminazione di un mapping tra account di accesso  
 Nell'esempio seguente viene rimossa la voce per il mapping degli account di accesso remoti tra il server remoto `ACCOUNTS` e l'account di accesso locale `Albert`.  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-dropping-a-remote-user"></a>C. Eliminazione di un utente remoto  
 Nell'esempio seguente viene rimosso l'account di accesso remoto `Chris` del server remoto `ACCOUNTS` sul quale è stato eseguito il mapping all'account di accesso locale `salesmgr`.  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [la procedura sp_addlinkedsrvlogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_addserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [la procedura sp_droplinkedsrvlogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
