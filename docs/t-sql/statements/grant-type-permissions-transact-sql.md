---
title: Autorizzazioni per tipi GRANT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], types
- granting permissions [SQL Server], types
- GRANT statement, types
- type permissions [SQL Server]
ms.assetid: 14bd2fb3-1446-49c0-be87-c6a670317ed0
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1e29ede5580418d1cbcb55d5a877196c3cabab92
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="grant-type-permissions-transact-sql"></a>GRANT - autorizzazioni per tipi (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Concede le autorizzazioni per un tipo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GRANT permission  [ ,...n ] ON TYPE :: [ schema_name . ] type_name  
    TO <database_principal> [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS <database_principal> ]  
  
<database_principal> ::=   
        Database_user   
    | Database_role   
        | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login  
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Specifica un'autorizzazione che può essere concessa per un tipo. Per un elenco delle autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 TIPO **::** [ *schema_name***.** ] *type_name*  
 Specifica il tipo per cui viene concessa l'autorizzazione. Il qualificatore di ambito (**::**) è obbligatorio. Se *schema_name* non viene specificato, verrà utilizzato lo schema predefinito. Se *schema_name* è specificato, il qualificatore di ambito dello schema (**.**) è obbligatorio.  
  
 PER \<database_principal > specifica l'entità a cui viene concessa l'autorizzazione.  
  
 WITH GRANT OPTION  
 Indica che l'entità potrà inoltre concedere l'autorizzazione specificata ad altre entità.  
  
 AS \<database_principal > specifica un'entità da cui l'entità che esegue la query Ottiene il diritto di concedere l'autorizzazione.  
  
 *Database_user*  
 Specifica un utente di database.  
  
 *Database_role*  
 Specifica un ruolo del database.  
  
 *Application_role*  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 Specifica un ruolo applicazione.  
  
 *Database_user_mapped_to_Windows_User*  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Specifica un utente del database sul quale viene eseguito il mapping a un utente di Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Specifica un utente del database sul quale viene eseguito il mapping a un gruppo di Windows.  
  
 *Database_user_mapped_to_certificate*  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Specifica un utente del database sul quale viene eseguito il mapping a un certificato.  
  
 *Database_user_mapped_to_asymmetric_key*  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Specifica un utente del database sul quale viene eseguito il mapping a una chiave asimmetrica.  
  
 *Database_user_with_no_login*  
 Specifica un utente del database per cui non esiste un'entità corrispondente a livello del server.  
  
## <a name="remarks"></a>Osservazioni  
 Un tipo è un'entità a sicurezza diretta a livello di schema contenuta nello schema padre nella gerarchia delle autorizzazioni.  
  
> [!IMPORTANT]  
>  **GRANT**, **DENY** e **revocare** autorizzazioni non si applicano ai tipi di sistema. Ai tipi definiti dall'utente è possibile concedere autorizzazioni. Per ulteriori informazioni sui tipi definiti dall'utente, vedere [utilizzo di tipi definiti dall'utente in SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md).  
  
 Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile concedere per un tipo, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione del tipo|Autorizzazione del tipo in cui è inclusa|Autorizzazione dello schema in cui è inclusa|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|Eseguire|CONTROL|Eseguire|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 L'utente che concede le autorizzazioni (o l'entità specificata con l'opzione AS) deve disporre della relativa autorizzazione con GRANT OPTION oppure di un'autorizzazione di livello superiore che include l'autorizzazione che viene concessa.  
  
 Se si utilizza l'opzione AS, sono previsti i requisiti aggiuntivi seguenti.  
  
|AS|Autorizzazione aggiuntiva necessaria|  
|--------|------------------------------------|  
|Utente del database|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un gruppo di Windows|L'appartenenza al gruppo di Windows, appartenenza al gruppo il **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un certificato|L'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza di **db_owner** o l'appartenenza al ruolo il **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica|L'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza di **db_owner** o l'appartenenza al ruolo il **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui non è stato eseguito il mapping ad alcuna entità server|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Ruolo del database|L'autorizzazione ALTER per il ruolo, appartenenza al gruppo di **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
|Ruolo applicazione|L'autorizzazione ALTER per il ruolo, appartenenza al gruppo di **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene concessa l'autorizzazione `VIEW DEFINITION` con `GRANT OPTION` per il tipo definito dall'utente `PhoneNumber` all'utente `KhalidR`. `PhoneNumber` è incluso nello schema `Telemarketing`.  
  
```  
GRANT VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    TO KhalidR WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Nega le autorizzazioni di tipo &#40; Transact-SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [Autorizzazioni per tipi REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-type-permissions-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


