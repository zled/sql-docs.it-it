---
title: Sys. database_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_credentials
- sys.database_credentials_TSQL
- database_credentials
- database_credentials_TSQL
helpviewer_keywords:
- sys.database_credentials catalog view
ms.assetid: 796322df-e62a-45bf-b519-89e1d521abce
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: ed1a494823c661710d1a5c184ff72c9f5099565e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39533471"
---
# <a name="sysdatabasecredentials-transact-sql"></a>Sys. database_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Restituisce una riga per ogni database scoped credential nel database.  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Uso [database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) invece.    
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID della credenziale con ambito database. È univoco nel database.|  
|NAME|**sysname**|Nome del database-credenziali con ambito. È univoco nel database.|  
|credential_identity|**nvarchar(4000)**|Nome dell'identità da utilizzare, in genere corrispondente a un utente di Windows. Non è necessario che sia univoco.|  
|create_date|**datetime**|Ora in cui è stata creata la credenziale con ambito database.|  
|modify_date|**datetime**|Ora ultima modifica in corrispondenza del quale la credenziale con ambito database.|  
|target_type|**Nvarchar(100)**|Tipo di database-credenziali con ambito. Le credenziali con ambito restituisce NULL per il database.|  
|target_id|**int**|ID dell'oggetto mappato per la credenziale con ambito database. Le credenziali con ambito restituisce 0 per il database|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione `CONTROL` per il database.  
  
## <a name="see-also"></a>Vedere anche  
 [Credenziali &#40;motore di database&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
