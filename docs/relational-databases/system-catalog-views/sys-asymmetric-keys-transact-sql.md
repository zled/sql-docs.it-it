---
title: asymmetric_keys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- asymmetric_keys
- sys.asymmetric_keys_TSQL
- asymmetric_keys_TSQL
- sys.asymmetric_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.asymmetric_keys catalog view
ms.assetid: bbca796a-9bb5-4a62-9ca8-1d255984553d
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0cc6153993ffd5febbc9fdaa7a06b477ea3aad1f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683259"
---
# <a name="sysasymmetrickeys-transact-sql"></a>sys.asymmetric_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni chiave asimmetrica.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome della chiave. Valore univoco all'interno del database.|  
|**principal_id**|**int**|ID dell'entità di database proprietaria della chiave.|  
|**asymmetric_key_id**|**int**|ID della chiave. Valore univoco all'interno del database.|  
|**pvt_key_encryption_type**|**char(2)**|Tipo di crittografia utilizzata per la chiave.<br /><br /> NA = Chiave non crittografata<br /><br /> MK = La chiave è crittografata tramite la chiave master<br /><br /> PW = La chiave è crittografata tramite una password definita dall'utente<br /><br /> SK = La chiave è crittografata tramite la chiave master del servizio|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|Descrizione della modalità di crittografia utilizzata per la chiave privata.<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**Identificazione personale**|**varbinary(32)**|Hash SHA-1 della chiave. L'hash è univoco a livello globale.|  
|**algoritmo**|**char(2)**|Algoritmo utilizzato con la chiave.<br /><br /> 1R = RSA a 512 bit<br /><br /> 2R = RSA a 1024 bit<br /><br /> 3R = RSA a 2048 bit|  
|**algorithm_desc**|**nvarchar(60)**|Descrizione dell'algoritmo utilizzato con la chiave.<br /><br /> RSA_512<br /><br /> RSA_1024<br /><br /> RSA_2048|  
|**lunghezza_chiave**|**int**|Lunghezza in bit della chiave.|  
|**sid**|**varbinary(85)**|SID dell'account di accesso della chiave. Per le chiavi EKM questo valore è NULL.|  
|**string_sid**|**nvarchar(128)**|Rappresentazione stringa del SID dell'account di accesso della chiave. Per le chiavi EKM questo valore è NULL.|  
|**public_key**|**varbinary(max)**|Chiave pubblica.|  
|**attested_by**|**nvarchar(260)**|Riservato per l'utilizzo nel sistema.|  
|**provider_type**|**nvarchar(120)**|Tipo di provider del servizio di crittografia:<br /><br /> CRYPTOGRAPHIC PROVIDER = chiavi EKM<br /><br /> NULL = chiavi non EKM|  
|**cryptographic_provider_guid**|**uniqueidentifier**|GUID del provider del servizio di crittografia. Per le chiavi non EKM questo valore è NULL.|  
|**cryptographic_provider_algid**|**sql_variant**|ID dell'algoritmo del provider del servizio di crittografia. Per le chiavi non EKM questo valore è NULL.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
  
  
