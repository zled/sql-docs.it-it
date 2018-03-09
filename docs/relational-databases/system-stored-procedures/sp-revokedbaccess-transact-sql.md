---
title: sp_revokedbaccess (Transact-SQL) | Documenti Microsoft
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
- sp_revokedbaccess_TSQL
- sp_revokedbaccess
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokedbaccess
ms.assetid: c997cfa1-539d-485c-a664-9c6f76bfe0c2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3ecca338697b8dc858cfecc0919fd27929066ba
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sprevokedbaccess-transact-sql"></a>sp_revokedbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un utente di database dal database corrente.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_revokedbaccess [ @name_in_db = ] 'name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name_in_db =** ] **'***nome***'**  
 Nome dell'utente di database da rimuovere. *nome* è un **sysname** prevede alcun valore predefinito. *nome* può essere il nome di un account di accesso del server, un account di accesso di Windows o un gruppo di Windows e deve esistere nel database corrente. Se si specifica un account di accesso o un gruppo di Windows, specificare il nome con cui è noto nel database.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Quando si rimuove l'utente di database, vengono rimossi anche le autorizzazioni e gli alias che dipendono dall'utente.  
  
 **sp_revokedbaccess** possibile rimuovere solo gli utenti del database dal database corrente. Prima di rimuovere un utente di database proprietario di oggetti nel database corrente è necessario trasferire la proprietà degli oggetti o rimuoverli dal database. Per ulteriori informazioni, vedere [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 **sp_revokedbaccess** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY USER per il database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'utente di database sul quale è stato eseguito il mapping a `Edmonds\LolanSo` viene rimosso dal database corrente.  
  
```  
EXEC sp_revokedbaccess 'Edmonds\LolanSo';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [DROP USER &#40; Transact-SQL &#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
