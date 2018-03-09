---
title: sp_addsrvrolemember (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/20/2017
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
- sp_addsrvrolemember
- sp_addsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addsrvrolemember
ms.assetid: 777f0e09-8ee5-4cb2-a3ac-939d02c3cd22
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c8159218d405cbd09861938393fd054ab8aea6e9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spaddsrvrolemember-transact-sql"></a>sp_addsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un account di accesso come membro di un ruolo predefinito del server.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addsrvrolemember [ @loginame= ] 'login'   
    , [ @rolename = ] 'role'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @loginame  **=**  ] **'***accesso***'**  
 Nome dell'account di accesso aggiunto al ruolo predefinito del server. *account di accesso* è **sysname**, non prevede alcun valore predefinito. *account di accesso* può essere un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso o un account di accesso di Windows. Gli account di Windows che non dispongono ancora dell'accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ricevono automaticamente l'autorizzazione di accesso.  
  
 [ @rolename  **=**  ] **'***ruolo***'**  
 Nome del ruolo predefinito del server a cui verrà aggiunto l'account di accesso. *ruolo* è **sysname**, con un valore predefinito è NULL e deve essere uno dei valori seguenti:  
  
-   sysadmin  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin  

## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Se si aggiunge un account di accesso a un ruolo predefinito del server, tale account eredita le autorizzazioni associate al ruolo.  
  
 Impossibile modificare l'appartenenza al ruolo dell'account di accesso sa e pubblici.  
  
 Utilizzare sp_addrolemember per aggiungere un membro a un database predefinito o un ruolo definito dall'utente.  
  
 sp_addsrvrolemember non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo a cui viene aggiunto il nuovo membro.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'account di accesso di Windows `Corporate\HelenS` viene aggiunto al ruolo predefinito del server `sysadmin`.  
  
```  
EXEC sp_addsrvrolemember 'Corporate\HelenS', 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [CREATE SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-role-transact-sql.md)  
  
  
