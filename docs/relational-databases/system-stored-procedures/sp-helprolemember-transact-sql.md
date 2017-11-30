---
title: sp_helprolemember (Transact-SQL) | Documenti Microsoft
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
- sp_helprolemember_TSQL
- sp_helprolemember
dev_langs: TSQL
helpviewer_keywords: sp_helprolemember
ms.assetid: 42797510-aa5d-4564-85ac-27418419af9c
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0d9b3b1a361b0e079d6c8d8fa844e86ed984fc66
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sphelprolemember-transact-sql"></a>sp_helprolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui membri diretti di un ruolo del database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helprolemember [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@rolename =** ] **'** *ruolo* **'**  
 Nome di un ruolo del database corrente. *ruolo* è **sysname**, con un valore predefinito è NULL. *ruolo* deve esistere nel database corrente. Se *ruolo* non viene specificato, vengono restituiti tutti i ruoli che contengono almeno un membro dal database corrente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**DbRole**|**sysname**|Nome del ruolo nel database corrente.|  
|**Nome di membro**|**sysname**|Nome di un membro di **DbRole.**|  
|**MemberSID**|**varbinary (85)**|ID di sicurezza di **MemberName.**|  
  
## <a name="remarks"></a>Osservazioni  
 Se il database contiene i ruoli nidificati, **MemberName** potrebbe essere il nome di un ruolo. **sp_helprolemember** non mostra l'appartenenza ottenuta attraverso i ruoli nidificati. Se, ad esempio, User1 è un membro di Role1 e Role1 è un membro di Role2, `EXEC sp_helprolemember 'Role2'`, verrà restituito Role1, ma non i membri di Role1 (User1 in questo esempio). Per restituire le appartenenze annidate, è necessario eseguire **sp_helprolemember** più volte per ogni ruolo annidato.  
  
 Utilizzare **sp_helpsrvrolemember** per visualizzare i membri di un ruolo predefinito del server.  
  
 Utilizzare [IS_ROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-rolemember-transact-sql.md) per controllare l'appartenenza al ruolo per un utente specificato.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono visualizzati i membri del ruolo `Sales`.  
  
```  
EXEC sp_helprolemember 'Sales';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helpsrvrolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
