---
title: CREARE ruolo (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE ROLE
- DATABASE ROLE
- ROLE_TSQL
- DATABASE_ROLE_TSQL
- CREATE_ROLE_TSQL
- CREATE DATABASE ROLE
- ROLE
- CREATE_DATABASE_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], creating
- CREATE DATABASE ROLE statement
- roles [SQL Server], creating
- CREATE ROLE statement
ms.assetid: b0cd54ad-e81d-4d71-acec-8a6d7261ca08
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cccfc9f6f9810d8f674ea32858e08683160b2ef1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-role-transact-sql"></a>CREATE ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Crea un nuovo ruolo di database nel database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE ROLE role_name [ AUTHORIZATION owner_name ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *role_name*  
 Nome del ruolo che si desidera creare.  
  
 AUTORIZZAZIONE *owner_name*  
 Utente o ruolo del database che sarà proprietario del nuovo ruolo. Se non viene specificato alcun utente, il ruolo sarà di proprietà dell'utente che esegue l'istruzione CREATE ROLE.  
  
## <a name="remarks"></a>Osservazioni  
 I ruoli sono entità a protezione diretta a livello di database. Dopo aver creato un ruolo, configurare le autorizzazioni a livello di database per il ruolo tramite GRANT, DENY e REVOKE. Per aggiungere membri a un ruolo del database, utilizzare [ALTER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-role-transact-sql.md). Per ulteriori informazioni, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 I ruoli del database sono visibili nelle viste del catalogo sys.database_role_members e sys.database_principals.  
  
 Per informazioni sulla progettazione di un sistema di autorizzazioni, vedere [Introduzione alle autorizzazioni del motore di database](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Richiede **CREATE ROLE** l'autorizzazione per il database o l'appartenenza di **db_securityadmin** ruolo predefinito del database. Quando si utilizza il **autorizzazione** opzione, le autorizzazioni seguenti sono necessari anche:  
  
-   Per assegnare la proprietà di un ruolo a un altro utente, è richiesta l'autorizzazione IMPERSONATE per quell'utente.  
  
-   Per assegnare la proprietà di un ruolo a un altro ruolo, è richiesta l'appartenenza al ruolo destinatario oppure l'autorizzazione ALTER per tale ruolo.  
  
-   Per assegnare la proprietà di un ruolo a un ruolo applicazione, è richiesta l'autorizzazione ALTER per il ruolo applicazione.  
  
## <a name="examples"></a>Esempi  
Gli esempi seguenti vengono utilizzano il database AdventureWorks.   

### <a name="a-creating-a-database-role-that-is-owned-by-a-database-user"></a>A. Creazione di un ruolo del database di proprietà di un utente del database  
 Nell'esempio seguente viene creato il ruolo del database `buyers` di proprietà dell'utente `BenMiller`.  
  
```  
CREATE ROLE buyers AUTHORIZATION BenMiller;  
GO  
```  
  
### <a name="b-creating-a-database-role-that-is-owned-by-a-fixed-database-role"></a>B. Creazione di un ruolo del database di proprietà di un ruolo predefinito del database  
 Nell'esempio seguente viene creato il ruolo del database `auditors` di proprietà del ruolo predefinito del database `db_securityadmin`.  
  
```  
CREATE ROLE auditors AUTHORIZATION db_securityadmin;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [ALTER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [DROP ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Introduzione alle autorizzazioni del motore di database](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
  


