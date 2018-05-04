---
title: column_encryption_key_values (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- column_encryption_key_values
- column_encryption_key_values_TSQL
- sys.column_encryption_key_values
- sys.column_encryption_key_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_encryption_key_values catalog view
ms.assetid: 440875ab-b0e9-4966-8c16-01503558fedd
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 776e6e8ecf9e6ce79d2f1f72a01acfd5af268448
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syscolumnencryptionkeyvalues-transact-sql"></a>column_encryption_key_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sui valori crittografati della colonna delle chiavi di crittografia (eseguono) create con la [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) o il [ALTER COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)istruzione. Ogni riga rappresenta un valore di una CEK, crittografata con una chiave master della colonna (CMK).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_id**|**int**|ID della CEK nel database.|  
|**column_master_key_id**|**int**|ID della chiave master della colonna utilizzata per crittografare il valore CEK.|  
|**encrypted_value**|**varbinary(8000)**|Valore CEK crittografato con la chiave CMK in column_master_key_id specificata.|  
|**encryption_algorithm_name**|**sysname**|Nome dell'algoritmo utilizzato per crittografare il valore CEK.<br /><br /> Nome dell'algoritmo di crittografia usato per crittografare il valore. L'algoritmo per i provider di sistema deve essere **RSA_OAEP**.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **VIEW ANY COLUMN ENCRYPTION KEY** autorizzazione.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys.column_encryption_keys  &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys.column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
  
  
