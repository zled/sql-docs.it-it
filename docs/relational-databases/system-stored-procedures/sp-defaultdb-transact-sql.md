---
title: sp_defaultdb (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sp_defaultdb_TSQL
- sp_defaultdb
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultdb
ms.assetid: 663b859f-c6da-4942-95a6-60b93d05654e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c44a3f1f26861e3e78e936aeb642e33ead4a4786
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spdefaultdb-transact-sql"></a>sp_defaultdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica il database predefinito per un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_defaultdb [ @loginame = ] 'login', [ @defdb = ] 'database'   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@loginame=**] **'***accesso***'**  
 Nome dell'account di accesso. *account di accesso* è **sysname**, non prevede alcun valore predefinito. *account di accesso* può essere un oggetto esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso o un utente di Windows o un gruppo. Se un account di accesso per l'utente o il gruppo di Windows non esiste in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ne verrà automaticamente creato uno.  
  
 [  **@defdb=**] **'***database***'**  
 Nome del nuovo database predefinito. *database* è **sysname**, non prevede alcun valore predefinito. *database* deve essere già esistente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_defaultdb** chiama ALTER LOGIN. che supporta opzioni aggiuntive. Per informazioni sulla modifica del database predefinito, vedere [ALTER LOGIN &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-login-transact-sql.md).  
  
 **sp_defaultdb** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY LOGIN.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] viene impostato come database predefinito per l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Victoria`.  
  
```  
EXEC sp_defaultdb 'Victoria', 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
