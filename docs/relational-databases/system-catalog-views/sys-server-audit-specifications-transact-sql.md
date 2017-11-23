---
title: server_audit_specifications (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_audit_specifications_TSQL
- sys.server_audit_specifications_TSQL
- server_audit_specifications
- sys.server_audit_specifications
dev_langs: TSQL
helpviewer_keywords: sys.server_audit_specifications catalog view
ms.assetid: fa496c6c-2a54-4fda-a238-db490c6b3afd
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab490931f358f7c890fc040e9394779703f67b31
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysserverauditspecifications-transact-sql"></a>sys.server_audit_specifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni sulle specifiche del controllo del server in un controllo di SQL Server in un'istanza del server. Per ulteriori informazioni su SQL Server Audit, vedere [SQL Server Audit &#40; motore di Database &#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**Sysname**|Nome della specifica del server.|  
|**server_specification_id**|**Int**|ID di **server_specification**.|  
|**create_date**|**DateTime**|Data di creazione della specifica del controllo del server.|  
|**modified_date**|**DateTime**|Data dell'ultima modifica della specifica del controllo del server.|  
|**is_state_enabled**|**tinyint**|Stato della specifica del controllo:<br /><br /> 0 - DISABILITATO<br /><br /> 1 - ABILITATO|  
|**audit_GUID**|**uniqueidentifier**|GUID del controllo che contiene questa specifica. Viene utilizzato durante l'enumerazione delle specifiche del controllo del server membro durante l'avvio del server.|  
  
## <a name="permissions"></a>Permissions  
 Entità che dispongono di **ALTER ANY SERVER AUDIT** o **VIEW ANY DEFINITION** autorizzazione hanno accesso a questa vista del catalogo. Inoltre, l'entità non deve essere negato **VIEW ANY DEFINITION** autorizzazione.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREARE DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [AUTORIZZAZIONE ALTER &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys. fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys. server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys. server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [Sys. server_audit_specification_details – &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [Sys. database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Sys.dm_audit_class_type_map &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Creazione di un controllo del server e di una specifica del controllo del server](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
