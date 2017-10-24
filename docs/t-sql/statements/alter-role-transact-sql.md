---
title: RUOLO ALTER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_ROLE_TSQL
- ALTER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database roles
- ALTER ROLE statement
- renaming database roles
- database roles [SQL Server], modifying
- names [SQL Server], database roles
ms.assetid: e1e83caa-17cc-4871-b2db-2711339fb64f
caps.latest.revision: 64
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3eaee2d346eda964545caa60cd7168b531f47ad9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-role-transact-sql"></a>ALTER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Aggiunge o rimuove i membri a o da un ruolo del database o modifica il nome di un ruolo del database definito dall'utente.  
  
> [!NOTE]  
>  Per modificare i ruoli in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare [sp_addrolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) e [sp_droprolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server (starting with 2012) and Azure SQL Database  
  
ALTER ROLE  role_name  
{  
       ADD MEMBER database_principal  
    |  DROP MEMBER database_principal  
    |  WITH NAME = new_name  
}  
[;]  
```  
  
 
```  
-- Syntax for SQL Server 2008 only  
  
-- Change the name of a user-defined database role  
ALTER ROLE role_name   
    WITH NAME = new_name  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *role_name*  
 **Si applica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da 2008),  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Specifica il ruolo di database da modificare.  
  
 Aggiungi membro *database_principal*l  
 **Si applica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da 2012),  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Specifica per aggiungere l'entità di database per l'appartenenza di un ruolo del database.  
  
-   *database_principal* è un utente del database o un ruolo del database definito dall'utente.  
  
-   *database_principal* non può essere un ruolo predefinito del database o un'entità del server.  
  
DROP MEMBER *database_principal*  
 **Si applica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da 2012),  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Specifica di rimuovere un'entità di database dall'appartenenza di un ruolo del database.  
  
-   *database_principal* è un utente del database o un ruolo del database definito dall'utente.  
  
-   *database_principal* non può essere un ruolo predefinito del database o un'entità del server.  
  
CON NAME = *nuovo_nome*  
 **Si applica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da 2008),  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Specifica per modificare il nome di un ruolo del database definito dall'utente. Il nuovo nome non deve esistere già nel database.  
  
 La modifica del nome di un ruolo del database non comporta la modifica del numero di ID, del proprietario o delle autorizzazioni del ruolo.  
  
## <a name="permissions"></a>Permissions  
 Per eseguire questo comando è necessario uno o più di queste autorizzazioni o appartenenze:  
  
-   **ALTER** autorizzazione per il ruolo  
-   **Autorizzazione ALTER ANY ROLE** autorizzazione per il database  
-   L'appartenenza di **db_securityadmin** ruolo predefinito del database  
  
Inoltre, per modificare l'appartenenza a un ruolo predefinito del database è necessario:  
  
-   L'appartenenza di **db_owner** ruolo predefinito del database  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 È possibile modificare il nome di un ruolo predefinito del database.  
  
## <a name="metadata"></a>Metadati  
 Queste viste di sistema contengono informazioni sui ruoli di database e le entità di database.  
  
-   [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)  
  
-   [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-change-the-name-of-a-database-role"></a>A. Modificare il nome di un ruolo del database  
 **Si applica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da 2008),  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 Nell'esempio seguente viene modificato il nome del ruolo `buyers` in `purchasing`. [!INCLUDE[AdWorks-example](../../includes/adworks-example-md.md)]  
  
```tsql  
ALTER ROLE buyers WITH NAME = purchasing;  
```  
  
### <a name="b-add-or-remove-role-members"></a>B. Aggiungere o rimuovere i membri del ruolo  
 **Si applica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da 2012),  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 Questo esempio viene creato un ruolo del database denominato `Sales`. Aggiunge un utente del database denominato Barry all'appartenenza e viene illustrato come rimuovere il membro Barry. [!INCLUDE[AdWorks-example](../../includes/adworks-example-md.md)]  
  
```tsql  
CREATE ROLE Sales;  
ALTER ROLE Sales ADD MEMBER Barry;  
ALTER ROLE Sales DROP MEMBER Barry;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREAZIONE di ruolo &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [DROP ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  

