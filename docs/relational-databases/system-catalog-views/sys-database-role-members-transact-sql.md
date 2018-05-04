---
title: database_role_members (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/31/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_role_members_TSQL
- sys.database_role_members
- database_role_members_TSQL
- database_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_role_members catalog view
ms.assetid: ed1b019d-ca48-4db3-85df-cf6d2db591cf
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fb7a04068c8c444fb7cb1b6d37466b44ce4f0b61
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdatabaserolemembers-transact-sql"></a>sys.database_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni membro di ogni ruolo del database.  Gli utenti del database, ruoli applicazione e altri ruoli del database possono essere membri di un ruolo del database. Per aggiungere membri a un ruolo, utilizzare il [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) istruzione con il `ADD MEMBER` opzione. Creare un join con [Sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) per restituire i nomi di `principal_id` valori.
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|ID dell'entità del ruolo del database.|  
|**member_principal_id**|**int**|ID dell'entità di database del membro.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Qualsiasi utente può visualizzare la propria appartenenza al ruolo. Per visualizzare gli altri ruoli appartenenza richiede l'appartenenza di `db_securityadmin` ruolo predefinito del database o `VIEW DEFINITION` nel database.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="example"></a>Esempio  
 La query seguente restituisce i membri dei ruoli del database.  
  
```  
SELECT DP1.name AS DatabaseRoleName,   
   isnull (DP2.name, 'No members') AS DatabaseUserName   
 FROM sys.database_role_members AS DRM  
 RIGHT OUTER JOIN sys.database_principals AS DP1  
   ON DRM.role_principal_id = DP1.principal_id  
 LEFT OUTER JOIN sys.database_principals AS DP2  
   ON DRM.member_principal_id = DP2.principal_id  
WHERE DP1.type = 'R'
ORDER BY DP1.name;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
[RUOLO ALTER (Transact-SQLL)](../../t-sql/statements/alter-role-transact-sql.md)      
[Sys. server_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
  


