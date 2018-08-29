---
title: master_key_passwords (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.master_key_passwords_TSQL
- master_key_passwords_TSQL
- sys.master_key_passwords
- master_key_passwords
dev_langs:
- TSQL
helpviewer_keywords:
- sys.master_key_passwords catalog view
ms.assetid: b8e18cff-a9e6-4386-98ce-1cd855506e03
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a0aa45dc4ee0e54e7880837e289b2331b5ff11e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017721"
---
# <a name="sysmasterkeypasswords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni password della chiave master del database aggiunta tramite il **sp_control_dbmasterkey_password** stored procedure. Le password utilizzate per proteggere le chiavi master vengono archiviate nell'archivio credenziali. Il nome della credenziale ha il formato seguente: ##DBMKEY_<database_family_guid>_<random_password_guid>##. La password viene archiviata come segreto della credenziale. Per ogni password aggiunta tramite **sp_control_dbmasterkey_password**, è presente una riga nella **Sys. Credentials**.  
  
 Ogni riga in questa vista mostra una **credential_id** e il **family_guid** di un database la cui chiave master è protetto con la password associata a tale credenziale. Un join con **Sys. Credentials** nel **credential_id** restituirà campi utili, ad esempio il **create_date** e nome della credenziale.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|ID della credenziale alla quale appartiene la password. Questo ID è univoco all'interno dell'istanza del server.|  
|**family_guid**|**uniqueidentifier**|ID univoco del database originale al momento della creazione. Questo GUID rimane invariato in seguito al ripristino o all'aggiunta del database, anche se il nome del database viene modificato.<br /><br /> Se la decrittografia automatica per la chiave master del servizio ha esito negativo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza le **family_guid** per identificare le credenziali che possono contenere la password utilizzata per proteggere la chiave master del database.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
