---
title: sys.dm_database_encryption_keys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3a6624182bdaafac45a01c90c4aba39dd6d64a5a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669570"
---
# <a name="sysdmdatabaseencryptionkeys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sullo stato di crittografia di un database e sulle chiavi di crittografia a esso associate. Per altre informazioni sulla crittografia del database, vedere [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database.|  
|encryption_state|**int**|Indica se il database è crittografato o meno.<br /><br /> 0 = Nessuna chiave di crittografia del database presente, nessuna crittografia<br /><br /> 1 = Non crittografato<br /><br /> 2 = Crittografia in corso<br /><br /> 3 = Crittografato<br /><br /> 4 = Modifica chiave in corso<br /><br /> 5 = Decrittografia in corso<br /><br /> 6 = Modifica della protezione in corso. È in corso la modifica della chiave asimmetrica o del certificato usato per crittografare la chiave di crittografia del database.|  
|create_date|**datetime**|Visualizza la data di creazione della chiave di crittografia.|  
|regenerate_date|**datetime**|Visualizza la data di rigenerazione della chiave di crittografia.|  
|modify_date|**datetime**|Visualizza la data di modifica della chiave di crittografia.|  
|set_date|**datetime**|Visualizza la data di applicazione al database della chiave di crittografia.|  
|opened_date|**datetime**|Mostra l'ultima apertura della chiave del database.|  
|key_algorithm|**nvarchar(32)**|Visualizza l'algoritmo usato per la chiave.|  
|key_length|**int**|Visualizza la lunghezza della chiave.|  
|encryptor_thumbprint|**varbinary(20)**|Mostra l'identificazione digitale della crittografia.|  
|encryptor_type|**nvarchar(32)**|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [versione corrente](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> Descrive il componente di crittografia.|  
|percent_complete|**real**|Percentuale di completamento del cambiamento di stato della crittografia del database. In assenza di un cambiamento di stato il valore sarà 0.|  
  
## <a name="permissions"></a>Permissions

Sul [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario `VIEW SERVER STATE` autorizzazione.   
Sul [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], è necessario il `VIEW DATABASE STATE` autorizzazione nel database.   

## <a name="see-also"></a>Vedere anche  

 [Funzioni e viste a gestione dinamica relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Crittografia di SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Chiavi di crittografia del database e di SQL Server &#40;Motore di database&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
