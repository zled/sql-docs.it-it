---
title: Sys.openkeys (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- openkeys_TSQL
- sys.openkeys_TSQL
- openkeys
- sys.openkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.openkeys catalog view
ms.assetid: 719a1259-2398-4fcb-ba05-aeabba7aec21
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ae65fbb1eaf69788917982aedb63ffedbc9d7a71
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33179917"
---
# <a name="sysopenkeys-transact-sql"></a>sys.openkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Questa vista del catalogo restituisce informazioni sulle chiavi di crittografia aperte nella sessione corrente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID del database contenente la chiave.|  
|**database_name**|**sysname**|Nome del database contenente la chiave.|  
|**key_id**|**int**|ID della chiave. L'ID è univoco all'interno del database.|  
|**key_name**|**sysname**|Nome della chiave. Univoco all'interno del database.|  
|**key_guid**|**varbinary**|GUID della chiave. Univoco all'interno del database.|  
|**opened_date**|**datetime**|Data e ora in cui la chiave è stata aperta.|  
|**status**|**int**|1 se la chiave è valida nei metadati. 0 se la chiave non è inclusa nei metadati.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)  
  
  
