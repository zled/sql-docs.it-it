---
title: Sys. security_policies (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- SYS.SECURITY_POLICIES_TSQL
- SECURITY_POLICIES_TSQL
- SYS.SECURITY_POLICIES
- SECURITY_POLICIES
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_policies catalog view
- security_policies catalog view
ms.assetid: 35362f5b-e601-4049-9e1d-c5307e823831
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e30a903e31ce8ba7951f9756a8fd258375fb8e2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="syssecuritypolicies-transact-sql"></a>Sys. security_policies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni criterio di sicurezza nel database.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nome del criterio di sicurezza, univoco all'interno del database.|  
|object_id|**int**|ID del criterio di sicurezza.|  
|principal_id|**int**|ID del proprietario del criterio di sicurezza registrato nel database. NULL se il proprietario viene determinato tramite lo schema.|  
|schema_id|**int**|ID dello schema in cui si trova l'oggetto.|  
|parent_object_id|**int**|ID dell'oggetto a cui appartiene il criterio. Deve essere 0.|  
|tipo|**vachar(2)**|Deve essere **SP**.|  
|type_desc|**nvarchar(60)**|**SECURITY_POLICY**.|  
|create_date|**datetime**|Data UTC di creazione del criterio di sicurezza.|  
|modify_date|**datetime**|Data UTC dell'ultima modifica del criterio di sicurezza.|  
|is_ms_shipped|**bit**|Sempre false.|  
|is_enabled|**bit**|Stato della specifica del criterio di sicurezza:<br /><br /> 0 = disabilitato<br /><br /> 1 = abilitato|  
|is_not_for_replication|**bit**|Il criterio è stato creato con l'opzione NOT FOR REPLICATION.|  
|uses_database_collation|**bit**|Usa le stesse regole di confronto del database.|  
|is_schemabinding_enabled|**bit**|SCHEMABINDING stato per i criteri di sicurezza:<br /><br /> 0 o NULL = abilitata<br /><br /> 1 = disabilitata|  
  
## <a name="permissions"></a>Permissions  
 Entità che dispongono di **ALTER ANY SECURITY POLICY** autorizzazione hanno accesso a tutti gli oggetti in questa vista del catalogo, nonché tutti gli utenti con **VIEW DEFINITION** sull'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza a livello di riga](../../relational-databases/security/row-level-security.md)   
 [sys.security_predicates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
