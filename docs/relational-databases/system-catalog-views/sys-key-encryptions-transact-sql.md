---
title: Sys. key_encryptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8a8fb9b2103316219bcdac74c1b861ac0a2668cb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853689"
---
# <a name="syskeyencryptions-transact-sql"></a>sys.key_encryptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni crittografia di chiave simmetrica specificata tramite la clausola ENCRYPTION BY dell'istruzione CREATE SYMMETRIC KEY.  

  
|Nomi colonna|Tipi di dati|Description|  
|------------------|----------------|-----------------|  
|**key_id**|**int**|ID della chiave crittografata.|  
|**Identificazione personale**|**varbinary(32)**|Hash SHA-1 del certificato con il quale è crittografata la chiave, o GUID della chiave simmetrica con il quale è crittografata la chiave.|  
|**crypt_type**|**Char(4)**|Tipo di crittografia:<br /><br /> ESKS = Crittografato tramite chiave simmetrica<br /><br /> ESP3, ESP2 o ESKP = crittografato tramite password<br /><br /> EPUC = Crittografato tramite certificato<br /><br /> EPUA = Crittografato tramite chiave asimmetrica<br /><br /> ESKM = Crittografato tramite chiave master|  
|**crypt_type_desc**|**nvarchar(60)**|Descrizione del tipo di crittografia:<br /><br /> ENCRYPTION BY SYMMETRIC KEY<br /><br /> ENCRYPTION BY PASSWORD <br />(A partire da [!INCLUDE[sssqlv14_md](../../includes/sssqlv14-md.md)], include un numero di versione per l'uso da CSS.)<br /><br /> ENCRYPTION BY CERTIFICATE<br /><br /> ENCRYPTION BY ASYMMETRIC KEY<br /><br /> ENCRYPTION BY MASTER KEY<br /><br /> Nota: Windows DPAPI viene usato per proteggere la chiave master del servizio.|  
|**crypt_property**|**varbinary(max)**|Bit firmati o crittografati.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
