---
title: sp_changedbowner (Transact-SQL) | Documenti Microsoft
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
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 11b80fef363bd33f725a34e5cebd7fd8710be3b4
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spchangedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica il proprietario del database corrente.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @loginame=] '*accesso*'  
 ID di accesso del nuovo proprietario del database corrente. *account di accesso* è **sysname**, non prevede alcun valore predefinito. *account di accesso* deve essere già esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso o utente di Windows. *account di accesso* non può diventare il proprietario del database corrente se dispone già dell'accesso al database tramite un account di sicurezza utente all'interno del database. Per evitare questa situazione, rimuovere l'utente dal database corrente.  
  
 [ @map=] *remap_alias_flag*  
 Il *remap_alias_flag* parametro è deprecato in quanto gli alias di accesso sono state rimosse da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilizzo di *remap_alias_flag* parametro non viene generato un errore ma non ha alcun effetto.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Dopo l'esecuzione di sp_changedbowner, nel database il nuovo proprietario è noto come utente dbo. L'utente dbo dispone di autorizzazioni implicite per l'esecuzione di qualsiasi operazione nel database.  
  
 Il proprietario dei database di sistema master, model e tempdb non può essere modificato.  
  
 Per visualizzare un elenco di validi *accesso* valori, eseguire la stored procedure sp_helplogins.  
  
 L'esecuzione di sp_changedbowner esclusivamente con le *accesso* modifiche parametro proprietario del database in *accesso*.  
  
 È possibile modificare il proprietario di qualsiasi entità a protezione diretta mediante l'istruzione ALTER AUTHORIZATION. Per ulteriori informazioni, vedere [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione TAKE OWNERSHIP per il database. Se il nuovo proprietario dispone di un utente corrispondente nel database, è richiesta l'autorizzazione IMPERSONATE per l'account di accesso. In caso contrario, è richiesta l'autorizzazione CONTROL SERVER per il server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente l'account di accesso `Albert` diventa il proprietario del database corrente.  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sp_dropalias &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
