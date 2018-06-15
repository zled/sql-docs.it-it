---
title: sp_add_proxy (Transact-SQL) | Microsoft Docs
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
- sp_add_proxy
- sp_add_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE PROXY statement
- sp_add_proxy
ms.assetid: cb59df37-f103-439b-bec1-2871fb669a8b
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a6b46ca35bc88c0e8d1677ca83bcb1da9af1e640
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238941"
---
# <a name="spaddproxy-transact-sql"></a>sp_add_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge il proxy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_proxy  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description' ,  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @proxy_id = ] id OUTPUT   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@proxy_name**=] **'***proxy_name***'**  
 Nome del proxy da creare. Il *proxy_name* è **sysname**, con un valore predefinito è NULL. Quando il *proxy_name* è NULL o una stringa vuota, il nome delle impostazioni predefinite del proxy per il *nome_utente* fornito.  
  
 [ **@enabled** =] *is_enabled*  
 Specifica se il proxy è attivato. Il *is_enabled* flag **tinyint**, con un valore predefinito è 1. Quando *is_enabled* è **0**, il proxy non è abilitato e non può essere utilizzato da un passaggio di processo.  
  
 [ **@description**=] **'***descrizione***'**  
 Descrizione del proxy. La descrizione è **nvarchar (512)**, con un valore predefinito è NULL. La descrizione consente di documentare il proxy, ma non viene altrimenti utilizzata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Questo argomento è pertanto facoltativo.  
  
 [ **@credential_name** =] **'***credential_name***'**  
 Nome delle credenziali per il proxy. Il *credential_name* è **sysname**, con un valore predefinito è NULL. Entrambi *credential_name* o *credential_id* deve essere specificato.  
  
 [ **@credential_id** =] *credential_id*  
 Numero di identificazione delle credenziali per il proxy. Il *credential_id* è **int**, con un valore predefinito è NULL. Entrambi *credential_name* o *credential_id* deve essere specificato.  
  
 [ **@proxy_id**=] *id* OUTPUT  
 Numero di identificazione assegnato al proxy se viene creato correttamente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Questa stored procedure deve essere eseguita **msdb** database.  
  
 Un proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent gestisce la sicurezza per i passaggi di processo che implicano i sottosistemi diversi da [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ogni proxy corrisponde a una credenziale di sicurezza Un proxy può avere accesso a qualsiasi numero di sottosistemi.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo di sicurezza predefinito può eseguire questa procedura.  
  
 I membri del **sysadmin** ruolo di sicurezza predefinito può creare passaggi di processo che utilizzano qualsiasi proxy. Utilizzare la stored procedure [sp_grant_login_to_proxy &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md) per concedere l'accesso altri account di accesso al proxy.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene creato un proxy per le credenziali `CatalogApplicationCredential`. Nel codice si presuppone che le credenziali esistano già. Per ulteriori informazioni sulle credenziali, vedere [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 1,  
    @description = 'Maintenance tasks on catalog application.',  
    @credential_name = 'CatalogApplicationCredential' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
