---
title: database_scoped_credentials (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords:
- sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 34db44a8b28ef9441e9bd6214e89ba2ef0e9f41b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysdatabasescopedcredentials-transact-sql"></a>database_scoped_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Restituisce una riga per ogni database con l'ambito delle credenziali nel database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID delle credenziali con ambito database. È univoco nel database.|  
|name|**sysname**|Nome del database di credenziali con ambito. È univoco nel database.|  
|credential_identity|**nvarchar(4000)**|Nome dell'identità da utilizzare, in genere corrispondente a un utente di Windows. Non è necessario che sia univoco.|  
|create_date|**datetime**|Ora in cui è stata creata la credenziale con ambito database.|  
|modify_date|**datetime**|Ora ultima modifica in cui le credenziali con ambito database.|  
|target_type|**nvarchar (100)**|Tipo di database di credenziali con ambito. Restituisce `NULL` per database credenziali con ambito.|  
|target_id|**int**|ID dell'oggetto cui viene eseguito il mapping di credenziali con ambito database per. Restituisce 0 per il database di credenziali con ambito|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione `CONTROL` per il database.  
  
## <a name="see-also"></a>Vedere anche  
 [Credenziali &#40; motore di Database &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
