---
title: Sys. Credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.credentials
- sys.credentials_TSQL
- credentials_TSQL
- credentials
dev_langs:
- TSQL
helpviewer_keywords:
- sys.credentials catalog view
ms.assetid: ea48cf80-904a-4273-a950-6d35b1b0a1b6
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: d94a60edd7dac48b8510a112fe7cbfe1e5ad40ec
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560601"
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Restituisce una riga per ogni credenziale a livello di server.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID della credenziale. Il nome è univoco nel server.|  
|NAME|**sysname**|Nome delle credenziali. Il nome è univoco nel server.|  
|credential_identity|**nvarchar(4000)**|Nome dell'identità da utilizzare, in genere corrispondente a un utente di Windows. Non è necessario che sia univoco.|  
|create_date|**datetime**|Ora di creazione della credenziale.|  
|modify_date|**datetime**|Ora dell'ultima modifica apportata alla credenziale.|  
|target_type|**Nvarchar(100)**|Tipo di credenziale. Restituisce NULL per credenziali tradizionali e CRYPTOGRAPHIC PROVIDER per credenziali di cui è stato eseguito il mapping a un provider di servizi di crittografia. Per altre informazioni sui provider di gestione delle chiavi esterne, vedere [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  
|target_id|**int**|ID dell'oggetto a cui è stato eseguito il mapping della credenziale. Restituisce 0 per credenziali tradizionali e un valore diverso da 0 per credenziali di cui è stato eseguito il mapping a un provider di servizi di crittografia. Per altre informazioni sui provider di gestione delle chiavi esterne, vedere [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  

## <a name="remarks"></a>Note  
Le credenziali a livello di database, vedere [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).
  
## <a name="permissions"></a>Permissions  
 Richiede `VIEW ANY DEFINITION` autorizzazione o `ALTER ANY CREDENTIAL` autorizzazione. Inoltre, l'entità non deve essere negata `VIEW ANY DEFINITION` l'autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [Credenziali &#40;motore di database&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
