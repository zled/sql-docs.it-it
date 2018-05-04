---
title: sp_droprole (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_droprole
- sp_droprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprole
ms.assetid: 889ee074-00f8-40a9-bddb-d7d3ef0cbc19
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6de087885b04b68cddfa7990705a217fbece5caa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spdroprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un ruolo del database dal database corrente.  
  
> [!IMPORTANT]  
>  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_droprole** è stata sostituita dall'istruzione DROP ROLE. **sp_droprole** è disponibile solo per compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e potrebbe non essere supportato nelle versioni future.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@rolename =** ] **'***ruolo***'**  
 Nome del ruolo del database da rimuovere dal database corrente. *ruolo* è un **sysname**, non prevede alcun valore predefinito. *ruolo* deve esistere nel database corrente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Solo i ruoli di database possono essere rimossi tramite **sp_droprole**.  
  
 Non è possibile rimuovere un ruolo del database a cui sono associati membri esistenti. È necessario rimuovere tutti i membri di un ruolo del database prima di poter rimuovere il ruolo del database stesso. Per rimuovere utenti da un ruolo, utilizzare **sp_droprolemember**. Se tutti gli utenti sono ancora i membri del ruolo, **sp_droprole** consente di visualizzare tali membri.  
  
 Ruoli predefiniti e **pubblica** ruolo non può essere rimosso.  
  
 Non è possibile rimuovere un ruolo proprietario di un'entità a sicurezza diretta. Prima di rimuovere un ruolo applicazione proprietario di entità a protezione diretta, è necessario innanzitutto trasferire la proprietà delle entità a protezione diretta oppure rimuoverle. Utilizzare ALTER AUTHORIZATION per modificare il proprietario degli oggetti che non devono essere rimossi.  
  
 **sp_droprole** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL per il ruolo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimosso il ruolo applicazione `Sales`.  
  
```  
EXEC sp_droprole 'Sales';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_dropapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
