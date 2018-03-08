---
title: sp_grant_login_to_proxy (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_proxy
- sp_grant_login_to_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_login_to_proxy
ms.assetid: 90e1a6d5-a692-4462-a163-4b0709d83150
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5a4788da049ef1d3c69f604aacdf9000f9ed624
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spgrantlogintoproxy-transact-sql"></a>sp_grant_login_to_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Concede a un'entità di sicurezza l'accesso a un proxy.  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_grant_login_to_proxy   
     { [ @login_name = ] 'login_name'   
     | [ @fixed_server_role = ] 'fixed_server_role'   
     | [ @msdb_role = ] 'msdb_role' } ,   
     { [ @proxy_id = ] id | [ @proxy_name = ] 'proxy_name' }  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@login_name** = ] **'***login_name***'**  
 Nome dell'account di accesso al quale concedere l'accesso. Il *login_name* è **nvarchar (256)**, con un valore predefinito è NULL. Uno dei  **@login_name** ,  **@fixed_server_role** , o  **@msdb_role**  devono essere specificati, o la stored procedure ha esito negativo.  
  
 [ **@fixed_server_role**= ] **'***fixed_server_role***'**  
 Ruolo predefinito del server al quale concedere l'accesso. Il *fixed_server_role* è **nvarchar (256)**, con un valore predefinito è NULL. Uno dei  **@login_name** ,  **@fixed_server_role** , o  **@msdb_role**  devono essere specificati, o la stored procedure ha esito negativo.  
  
 [ **@msdb_role**= ] '*msdb_role*'  
 Il ruolo del database nel **msdb** concedere l'accesso al database. Il *msdb_role* è **nvarchar (256)**, con un valore predefinito è NULL. Uno dei  **@login_name** ,  **@fixed_server_role** , o  **@msdb_role**  devono essere specificati, o la stored procedure ha esito negativo.  
  
 [ **@proxy_id**= ] *id*  
 Identificatore del proxy per il quale concedere l'accesso. Il *id* è **int**, con un valore predefinito è NULL. Uno dei  **@proxy_id**  o  **@proxy_name**  devono essere specificati, o la stored procedure ha esito negativo.  
  
 [ **@proxy_name**= ] **'***proxy_name***'**  
 Nome del proxy per il quale concedere l'accesso. Il *proxy_name* è **nvarchar (256)**, con un valore predefinito è NULL. Uno dei  **@proxy_id**  o  **@proxy_name**  devono essere specificati, o la stored procedure ha esito negativo.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_grant_login_to_proxy** deve essere eseguita la **msdb** database.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server può essere eseguita **sp_grant_login_to_proxy**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene consentito all'account di accesso `adventure-works\terrid` di utilizzare il proxy `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_login_to_proxy  
    @login_name = N'adventure-works\terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
