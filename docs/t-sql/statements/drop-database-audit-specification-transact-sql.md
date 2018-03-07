---
title: DROP DATABASE AUDIT SPECIFICATION (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_DATABASE_AUDIT_SPECIFICATION_TSQL
- DROP DATABASE AUDIT SPECIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- database audit specification
- DROP DATABASE AUDIT SPECIFICATION statement
ms.assetid: 3c387c6e-9a67-4daa-b64a-c87f6b3c9c4f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50a7d069903fc9cf4485b115a7ab9a29a53dcbde
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="drop-database-audit-specification-transact-sql"></a>DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina un oggetto specifica controllo database utilizzando la funzionalità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. Per altre informazioni, vedere [SQL Server Audit &#40;Motore di database&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP DATABASE AUDIT SPECIFICATION audit_specification_name  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *audit_specification_name*  
 Nome di un oggetto della specifica del controllo esistente.  
  
## <a name="remarks"></a>Osservazioni  
 DROP DATABASE AUDIT SPECIFICATION rimuove i metadati per la specifica del controllo, ma non i dati di controllo raccolti prima dell'esecuzione del comando DROP. È necessario impostare lo stato di una specifica del controllo del database su OFF utilizzando `ALTER DATABASE AUDIT SPECIFICATION` prima che può essere eliminata.  
  
## <a name="permissions"></a>Permissions  
 Gli utenti con il **ALTER ANY DATABASE AUDIT** autorizzazione può eliminare le specifiche controllo database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-database-audit-specification"></a>A. Eliminazione di una specifica del controllo del database  
 Nell'esempio seguente viene eliminato un controllo denominato `HIPAA_Audit_DB_Specification`.  
  
```  
DROP DATABASE AUDIT SPECIFICATION HIPAA_Audit_DB_Specification;  
GO  
```  
  
 Per un esempio completo di creazione di un controllo, vedere [SQL Server Audit &#40; motore di Database &#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREARE DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [AUTORIZZAZIONE ALTER &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys. fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys. server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys. server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [Sys. server_audit_specification_details – &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [Sys. database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Sys.dm_audit_class_type_map &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Creazione di un controllo del server e di una specifica del controllo del server](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
