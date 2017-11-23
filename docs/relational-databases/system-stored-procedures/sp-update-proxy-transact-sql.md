---
title: sp_update_proxy (Transact-SQL) | Documenti Microsoft
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
- sp_update_proxy
- sp_update_proxy_TSQL
dev_langs: TSQL
helpviewer_keywords:
- ALTER PROXY statement
- sp_update_proxy
ms.assetid: 864fd0e6-9d61-4f07-92ef-145318d2f881
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0e81e23e501bac52de7491efc367c43d6fb5121
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spupdateproxy-transact-sql"></a>sp_update_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le proprietà di un proxy già esistente.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_update_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @new_name = ] 'new_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@proxy_id** =] *id*  
 Numero di identificazione del proxy da modificare. Il *proxy_id* è **int**, con un valore predefinito è NULL.  
  
 [  **@proxy_name** =] **'***proxy_name***'**  
 Nome del proxy da modificare. Il *proxy_name* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@credential_name**  =] **'***credential_name***'**  
 Nome delle nuove credenziali per il proxy. Il *credential_name* è **sysname**, con un valore predefinito è NULL. Entrambi *credential_name* o *credential_id* può essere specificato.  
  
 [  **@credential_id**  =] *credential_id*  
 Numero di identificazione delle nuove credenziali per il proxy. Il *credential_id* è **int**, con un valore predefinito è NULL. Entrambi *credential_name* o *credential_id* può essere specificato.  
  
 [  **@new_name** =] **'***nuovo_nome***'**  
 Nuove nome del proxy. Il *nuovo_nome* è **sysname**, con un valore predefinito è NULL. Quando viene fornito, la procedura modifica il nome del proxy da *nuovo_nome*. Quando questo argomento è NULL, il nome del proxy rimane invariato.  
  
 [  **@enabled**  =] *is_enabled*  
 Specifica se il proxy è abilitato. Il *is_enabled* flag **tinyint**, con un valore predefinito è NULL. Quando *is_enabled* è **0**, il proxy non è abilitato e non può essere utilizzato da un passaggio di processo. Quando questo argomento è NULL, lo stato del proxy rimane invariato.  
  
 [  **@description** =] **'***descrizione***'**  
 Nuova descrizione del proxy. Il *descrizione* è **nvarchar (512)**, con un valore predefinito è NULL. Quando questo argomento è NULL, la descrizione del proxy rimane invariata.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 Entrambi  **@proxy_name**  o  **@proxy_id**  deve essere specificato. Se si specificano entrambi gli argomenti, devono riferirsi tutti e due allo stesso proxy per consentire la corretta esecuzione della stored procedure.  
  
 Entrambi  **@credential_name**  o  **@credential_id**  deve essere specificato per modificare le credenziali per il proxy. Se si specificano entrambi gli argomenti, devono riferirsi alle stesse credenziali per consentire la corretta esecuzione della stored procedure.  
  
 Questa procedura modifica il proxy, ma non modifica l'accesso al proxy. Per modificare l'accesso a un proxy, utilizzare **sp_grant_login_to_proxy** e **sp_revoke_login_from_proxy**.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo di sicurezza predefinito può eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene impostato il valore abilitato per il proxy `Catalog application proxy` su `0`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 0;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Agent Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Implementazione della sicurezza SQL Server Agent](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_add_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  