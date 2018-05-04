---
title: sp_helpuser (Transact-SQL) | Documenti Microsoft
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
- sp_helpuser
- sp_helpuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpuser
ms.assetid: 9c70b41d-ef4c-43df-92da-bd534c287ca1
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1bf9bca0586d1e8e5f7f0bf6db40d2cd244aec8e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpuser-transact-sql"></a>sp_helpuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle entità a livello di database nel database corrente.  
  
> [!IMPORTANT]  
>  **sp_helpuser** non restituisce informazioni sulle entità a protezione diretta introdotte in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Utilizzare [Sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpuser [ [ @name_in_db = ] 'security_account' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name_in_db =** ] **'***security_account***'**  
 Nome dell'utente o del ruolo del database nel database corrente. *security_account* deve esistere nel database corrente. *security_account* viene **sysname**, con un valore predefinito è NULL. Se *security_account* non viene specificato, **sp_helpuser** restituisce informazioni su tutte le entità di database.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nella tabella seguente viene illustrato il set di risultati quando non un account utente né una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o utente di Windows specificato per *security_account*.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**UserName**|**sysname**|Utenti nel database corrente.|  
|**RoleName**|**sysname**|Ruoli a cui **UserName** appartiene.|  
|**LoginName**|**sysname**|Account di accesso di **UserName**.|  
|**DefDBName**|**sysname**|Database predefinito del **UserName**.|  
|**DefSchemaName**|**sysname**|Schema predefinito dell'utente del database.|  
|**UserID**|**smallint**|ID del **UserName** nel database corrente.|  
|**SID**|**smallint**|ID di sicurezza dell'utente (SID)|  
  
 Nella tabella seguente viene illustrato il set di risultati quando non si specifica alcun account utente ed esistono alias nel database corrente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Account di accesso associati come alias agli utenti del database corrente.|  
|**UserNameAliasedTo**|**sysname**|Nome utente nel database corrente associato come alias all'account utente.|  
  
 Nella tabella seguente viene illustrato il set di risultati quando viene specificato un ruolo per *security_account*.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**role_name**|**sysname**|Nome del ruolo nel database corrente.|  
|**Role_id**|**smallint**|ID del ruolo nel database corrente.|  
|**Users_in_role**|**sysname**|Membro del ruolo nel database corrente.|  
|**ID utente**|**smallint**|ID utente del membro del ruolo.|  
  
## <a name="remarks"></a>Osservazioni  
 Per visualizzare informazioni sull'appartenenza ai ruoli di database, utilizzare [database_role_members](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md). Per visualizzare informazioni sui membri del ruolo server, utilizzare [server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)e per visualizzare le informazioni sulle entità a livello di server, utilizzare [Sys. server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
 Le informazioni restituite sono soggette a limitazioni di accesso ai metadati. Non vengono visualizzate le entità per le quali l'entità di database non dispone dell'autorizzazione. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-all-users"></a>A. Visualizzazione di un elenco di tutti gli utenti  
 Nell'esempio seguente vengono elencati tutti gli utenti nel database corrente.  
  
```  
EXEC sp_helpuser;  
```  
  
### <a name="b-listing-information-for-a-single-user"></a>B. Visualizzazione di informazioni relative a un singolo utente  
 Nell'esempio seguente vengono restituite informazioni sul proprietario del database utente (`dbo`).  
  
```  
EXEC sp_helpuser 'dbo';  
```  
  
### <a name="c-listing-information-for-a-database-role"></a>C. Visualizzazione di informazioni relative a un ruolo del database  
 Nell'esempio seguente vengono restituite informazioni sul ruolo predefinito del database `db_securityadmin`.  
  
```  
EXEC sp_helpuser 'db_securityadmin';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
  
