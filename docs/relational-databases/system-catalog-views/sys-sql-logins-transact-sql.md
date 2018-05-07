---
title: Sys. sql_logins (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cdf6447b7673606224852078f80306c4b7fb4632
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="syssqllogins-transact-sql"></a>sys.sql_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Viene restituita una riga per ogni account di accesso con autenticazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<colonne ereditate >**|--|Eredita da **Sys. server_principals**.|  
|**is_policy_checked**|**bit**|I criteri password vengono controllati.|  
|**is_expiration_checked**|**bit**|La scadenza delle password viene controllata.|  
|**password_hash**|**varbinary(256)**|Hash della password dell'account di accesso di SQL. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le informazioni relative alle password archiviate vengono calcolate tramite SHA-512 della password salt.|  
  
 Per un elenco delle colonne ereditate da questa vista, vedere [Sys. server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 Per visualizzare entrambi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso di autenticazione e accesso con autenticazione di Windows, vedere [Sys. server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Quando i contenuti vengono abilitati gli utenti del database, le connessioni possono essere eseguite senza account di accesso. Per identificare questi account, vedere [Sys. database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Con qualsiasi account di accesso con autenticazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile visualizzare il relativo nome di account di accesso e l'account di accesso sa. Per visualizzare altri account di accesso, è richiesta l'autorizzazione ALTER ANY LOGIN o un'autorizzazione per l'account di accesso.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Criteri password](../../relational-databases/security/password-policy.md)   
 [Entità &#40;Motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
