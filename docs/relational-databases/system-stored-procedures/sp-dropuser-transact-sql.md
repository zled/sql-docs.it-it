---
title: sp_dropuser (Transact-SQL) | Documenti Microsoft
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
- sp_dropuser
- sp_dropuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropuser
ms.assetid: e28f18f9-7ecf-4568-89f4-fe5c520df386
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9af8a740ae349f748acc6c8385d95b97a0e2490d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spdropuser-transact-sql"></a>sp_dropuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un utente di database dal database corrente. **sp_dropuser** garantisce la compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Uso [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dropuser [ @name_in_db = ] 'user'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name_in_db =**] **'***utente***'**  
 Nome dell'utente da rimuovere. *utente* è un **sysname**, non prevede alcun valore predefinito. *utente* deve esistere nel database corrente. Quando si specifica un account di accesso di Windows, utilizzare il nome con il quale il database identifica l'account di accesso.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dropuser** viene eseguito **sp_revokedbaccess** per rimuovere l'utente dal database corrente.  
  
 Utilizzare **sp_helpuser** per visualizzare un elenco dei nomi utente che può essere rimosso dal database corrente.  
  
 Quando si rimuove un utente di database, vengono rimossi anche tutti gli alias di tale utente. Se l'utente è proprietario di uno schema vuoto che ha lo stesso suo nome, lo schema verrà rimosso. Se l'utente è proprietario di altre entità a protezione diretta nel database, l'utente non verrà rimosso. La proprietà degli oggetti deve prima essere trasferita ad un'altra entità. Per altre informazioni, vedere [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md). Se si rimuove un utente di database, vengono rimosse automaticamente anche le autorizzazioni corrispondenti e l'utente viene rimosso dai ruoli di database di cui è membro.  
  
 **sp_dropuser** non può essere utilizzato per rimuovere il proprietario del database (**dbo**) **INFORMATION_SCHEMA** gli utenti, o il **guest** utente dal **master**  oppure **tempdb** database. Nei database non di sistema, `EXEC sp_dropuser 'guest'` revocare l'autorizzazione CONNECT all'utente **guest**. ma l'utente stesso non verrà rimosso.  
  
 **sp_dropuser** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER ANY USER per il database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'utente `Albert` viene rimosso dal database corrente.  
  
```  
EXEC sp_dropuser 'Albert';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [DROP USER & #40; Transact-SQL & #41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
