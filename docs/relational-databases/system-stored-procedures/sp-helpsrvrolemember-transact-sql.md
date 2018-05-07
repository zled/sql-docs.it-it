---
title: sp_helpsrvrolemember (Transact-SQL) | Documenti Microsoft
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
- sp_helpsrvrolemember
- sp_helpsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsrvrolemember
ms.assetid: d0714913-8d6b-4de3-b042-3ae9934f839d
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d4c800464cf0da918e748ba6b6c9d1ffc4c093a0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpsrvrolemember-transact-sql"></a>sp_helpsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui membri di un ruolo predefinito del server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpsrvrolemember [ [ @srvrolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@srvrolename =** ] **'***ruolo***'**  
 Nome del ruolo predefinito del server. *ruolo* viene **sysname**, con un valore predefinito è NULL. Se *ruolo*non viene specificato, il set di risultati include informazioni su tutti i ruoli predefiniti del server.  
  
 *ruolo* può essere uno dei valori seguenti.  
  
|Ruolo predefinito del server|Description|  
|-----------------------|-----------------|  
|sysadmin|Amministratori di sistema|  
|securityadmin|Amministratori di sicurezza|  
|serveradmin|Amministratori di server|  
|setupadmin|Amministratori di installazione|  
|processadmin|Amministratori di processi|  
|diskadmin|Amministratori di dischi|  
|dbcreator|Creatori di database|  
|bulkadmin|Può eseguire le istruzioni BULK INSERT|  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|ServerRole|**sysname**|Nome del ruolo del server|  
|MemberName|**sysname**|Nome di un membro del ruolo server|  
|MemberSID|**varbinary(85)**|ID di sicurezza del nome di membro|  
  
## <a name="remarks"></a>Osservazioni  
 Per visualizzare i membri di un ruolo del database, utilizzare sp_helprolemember.  
  
 Tutti gli account di accesso sono membri del ruolo public. sp_helpsrvrolemember non riconosce il ruolo public perché, internamente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non implementa pubblica come ruolo.  
  
 Per aggiungere o rimuovere membri dai ruoli del server, vedere [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 sp_helpsrvrolemember non ha un ruolo del server definito dall'utente come argomento. Per determinare i membri di un ruolo del server definito dall'utente, vedere gli esempi in [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono elencati i membri del ruolo predefinito del server `sysadmin`.  
  
```  
EXEC sp_helpsrvrolemember 'sysadmin';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_helprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
