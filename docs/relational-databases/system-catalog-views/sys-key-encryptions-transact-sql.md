---
title: key_encryptions (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 07/18/2017
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
f1_keywords:
- sys.key_encryptions
- key_encryptions_TSQL
- sys.key_encryptions_TSQL
- key_encryptions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.key_encryptions catalog view
ms.assetid: c39cecf8-af63-40b9-98e5-f84a5bf3ae54
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a922f80485fafe721124719d3d65566cdad02deb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syskeyencryptions-transact-sql"></a>sys.key_encryptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni crittografia di chiave simmetrica specificata tramite la clausola ENCRYPTION BY dell'istruzione CREATE SYMMETRIC KEY.  

  
|Nomi colonna|Tipi di dati|Description|  
|------------------|----------------|-----------------|  
|**key_id**|**int**|ID della chiave crittografata.|  
|**Identificazione personale**|**varbinary(32)**|Hash SHA-1 del certificato con il quale è crittografata la chiave, o GUID della chiave simmetrica con il quale è crittografata la chiave.|  
|**crypt_type**|**Char(4)**|Tipo di crittografia:<br /><br /> ESKS = Crittografato tramite chiave simmetrica<br /><br /> ESP3, ESP2 o ESKP = crittografato tramite password<br /><br /> EPUC = Crittografato tramite certificato<br /><br /> EPUA = Crittografato tramite chiave asimmetrica<br /><br /> ESKM = Crittografato tramite chiave master|  
|**crypt_type_desc**|**nvarchar(60)**|Descrizione del tipo di crittografia:<br /><br /> ENCRYPTION BY SYMMETRIC KEY<br /><br /> ENCRYPTION BY PASSWORD <br />(A partire da [!INCLUDE[sssqlv14_md](../../includes/sssqlv14-md.md)], include un numero di versione per l'utilizzo da CSS.)<br /><br /> ENCRYPTION BY CERTIFICATE<br /><br /> ENCRYPTION BY ASYMMETRIC KEY<br /><br /> ENCRYPTION BY MASTER KEY<br /><br /> Nota: DPAPI di Windows viene utilizzato per proteggere la chiave master del servizio.|  
|**crypt_property**|**varbinary(max)**|Bit firmati o crittografati.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
