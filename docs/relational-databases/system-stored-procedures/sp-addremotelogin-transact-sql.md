---
title: sp_addremotelogin (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addremotelogin_TSQL
- sp_addremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addremotelogin
ms.assetid: 71b7cd36-a17d-4b12-b102-10aeb0f9268b
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ec988334611350fdf736b69100b27d79d5374342
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238821"
---
# <a name="spaddremotelogin-transact-sql"></a>sp_addremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un nuovo ID di accesso remoto nel server locale. Ciò consente ai server remoti di connettersi ed eseguire chiamate di procedure remote.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilizzare i server collegati e le stored procedure per i server collegati in alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @remoteserver **=** ] **'***remoteserver***'**  
 Nome del server remoto a cui fa riferimento l'account di accesso remoto. *remoteserver* viene **sysname**, non prevede alcun valore predefinito. Se solo *remoteserver* è specificato, tutti gli utenti *remoteserver* vengono mappati a un account di accesso esistenti con lo stesso nome nel server locale. Il server deve essere noto al server locale. Viene aggiunto tramite sp_addserver. Quando gli utenti di *remoteserver* connettersi al server locale in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire una stored procedure remota, si connettono all'account di accesso locale corrispondente al proprio account di accesso in *remoteserver* . *remoteserver* è il server che avvia la chiamata di procedura remota.  
  
 [ @loginame **=** ] **'***accesso***'**  
 ID dell'account di accesso dell'utente nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *login* è di tipo **sysname** e il valore predefinito è NULL. *account di accesso*deve esistere già nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se *accesso* è specificato, tutti gli utenti *remoteserver* vengono mappate a tale account di accesso locale specifico. Quando gli utenti di *remoteserver* connettersi all'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire una stored procedure remota, si connettono come *accesso*.  
  
 [ @remotename **=** ] **'***remote_name***'**  
 ID dell'account di accesso dell'utente nel server remoto. *remote_name* viene **sysname**, con un valore predefinito è NULL. *remote_name* deve essere presente nel *remoteserver*. Se *remote_name* è specificato, l'utente specifico *remote_name* viene eseguito il mapping a *accesso* nel server locale. Quando *remote_name* su *remoteserver* si connette all'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire una stored procedure remota, si connette come *accesso*. L'ID di accesso di *remote_name* può essere diverso dall'ID di accesso nel server remoto, *accesso*.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Per eseguire query distribuite, utilizzare la procedura sp_addlinkedsrvlogin.  
  
 sp_addremotelogin non può essere utilizzata all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo sysadmin e ruoli predefiniti del server securityadmin possono eseguire sp_addremotelogin.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-mapping-one-to-one"></a>A. Mapping uno-a-uno  
 Nell'esempio seguente viene eseguito il mapping dei nomi remoti ai nomi locali quando nel server remoto `ACCOUNTS` e in quello locale sono disponibili gli stessi account di accesso.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-mapping-many-to-one"></a>B. Mapping molti-a-uno  
 Nell'esempio seguente viene creata una voce per mappare tutti gli utenti del server remoto `ACCOUNTS` all'ID di accesso locale `Albert`.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-using-explicit-one-to-one-mapping"></a>C. Utilizzo del mapping uno-a-uno esplicito  
 Nell'esempio seguente un account di accesso dell'utente remoto `Chris` nel server remoto `ACCOUNTS` viene mappato all'utente locale `salesmgr`.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
