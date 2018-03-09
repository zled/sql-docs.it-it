---
title: column_master_keys (Transact-SQL) | Documenti Microsoft
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
- column_master_key_definitions_TSQL
- column_master_key_definitions
- sys.column_master_key_definitions_TSQL
- sys.column_master_key_definitions
- column_master_keys_TSQL
- column_master_keys
- sys.column_master_keys_TSQL
- sys.column_master_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_key_definitions catalog view
- sys.column_master_keys catalog view
ms.assetid: fbec2efa-5fe9-4121-9b34-60497b0b2aca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e22e052d88c339828e0a7e5d6f5803bc04b30925
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumnmasterkeys-transact-sql"></a>sys.column_master_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni chiave master del database aggiunto tramite il [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) istruzione. Ogni riga rappresenta una chiave master di colonna (CMK).  
    
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Il nome di CMK.|  
|**column_master_key_id**|**int**|ID della chiave master della colonna.|  
|**create_date**|**datetime**|Data di che creazione della chiave master di colonna.|  
|**modify_date**|**datetime**|Data che ultima modifica della chiave master della colonna.|  
|**key_store_provider_name**|**sysname**|Nome del provider per l'archivio di chiavi master di colonna che contiene la chiave CMK. I valori consentiti sono:<br /><br /> MSSQL_CERTIFICATE_STORE: se l'archivio chiavi master della colonna è un archivio certificati.<br /><br /> Un valore definito dall'utente, se l'archivio chiavi master della colonna è di un tipo personalizzato.|  
|**key_path**|**nvarchar(4000)**|Percorso specifiche dell'archivio di chiave master di colonna della chiave. Il formato del percorso dipende dal tipo di archivio chiave master di colonna. Esempio:<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Per un archivio chiavi master della colonna personalizzata, lo sviluppatore è responsabile della definizione è il percorso di una chiave per l'archivio chiavi master della colonna personalizzato.|  
  
## <a name="permissions"></a>Permissions  
 Richiede il **VIEW ANY COLUMN MASTER KEY** autorizzazione.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
