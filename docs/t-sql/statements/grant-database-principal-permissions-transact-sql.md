---
title: "GRANT-autorizzazioni per entità di Database (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 03/12/2017
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
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], permissions
- permissions [SQL Server], database roles
- granting permissions [SQL Server], database users
- granting permissions [SQL Server], application roles
- granting permissions [SQL Server], database roles
- database user permissions [SQL Server]
- permissions [SQL Server], application roles
- permissions [SQL Server], database users
- GRANT statement, users
- GRANT statement, roles
- application roles [SQL Server], permissions
ms.assetid: 012588a2-cbe1-48f0-a731-b4a2b83203d5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 58f66a871299d85c8ee9bce59b696cec2668ae9f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="grant-database-principal-permissions-transact-sql"></a>GRANT - autorizzazioni per entità di database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Concede le autorizzazioni per un utente di database, un ruolo del database o un ruolo applicazione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
GRANT permission [ ,...n ]    
    ON   
    {  [ USER :: database_user ]  
     | [ ROLE :: database_role ]  
     | [ APPLICATION ROLE :: application_role ]  
    }  
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
 Specifica un'autorizzazione che può essere concessa per un'entità di database. Per un elenco delle autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 UTENTE::*database_user*  
 Specifica la classe e il nome dell'utente per cui viene concessa l'autorizzazione. Il qualificatore di ambito (::) è obbligatorio.  
  
 RUOLO::*database_role*  
 Specifica la classe e il nome del ruolo per cui viene concessa l'autorizzazione. Il qualificatore di ambito (::) è obbligatorio.  
  
 RUOLO applicazione::*application_role*  
   
 Specifica la classe e il nome del ruolo applicazione per cui viene concessa l'autorizzazione. Il qualificatore di ambito (::) è obbligatorio.  
  
 WITH GRANT OPTION  
 Indica che l'entità potrà inoltre concedere l'autorizzazione specificata ad altre entità.  
  
 AS \<database_principal >  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di concedere l'autorizzazione.  
  
 *Database_user*  
 Specifica un utente di database.  
  
 *Database_role*  
 Specifica un ruolo del database.  
  
 *Application_role*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Specifica un ruolo applicazione.  
  
 *Database_user_mapped_to_Windows_User*  
 Specifica un utente del database mappato a un utente di Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
  
 Specifica un utente del database sul quale viene eseguito il mapping a un gruppo di Windows.  
  
 *Database_user_mapped_to_certificate*  
  
 Specifica un utente del database sul quale viene eseguito il mapping a un certificato.  
  
 *Database_user_mapped_to_asymmetric_key*  
  
 Specifica un utente del database sul quale viene eseguito il mapping a una chiave asimmetrica.  
  
 *Database_user_with_no_login*  
 Specifica un utente del database per cui non esiste un'entità corrispondente a livello del server.  
  
## <a name="remarks"></a>Osservazioni  
 Informazioni sulle entità di database sono visibili nella [Sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) vista del catalogo. Informazioni sulle autorizzazioni a livello di database sono visibili nella [Sys. database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) vista del catalogo.  
  
## <a name="database-user-permissions"></a>Autorizzazioni per utenti di database  
 Un utente di database è un'entità a protezione diretta a livello di database contenuta nel database padre nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile concedere per un utente di database, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione dell'utente di database|Autorizzazione dell'utente di database in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|IMPERSONATE|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY USER|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="database-role-permissions"></a>Autorizzazioni per ruoli del database  
 Un ruolo del database è un'entità a protezione diretta a livello di database contenuta nel database padre nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile concedere per un ruolo del database, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione del ruolo del database|Autorizzazione del ruolo del database in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="application-role-permissions"></a>Autorizzazioni per i ruoli applicazione  
 Un ruolo applicazione è un'entità a protezione diretta a livello di database contenuta nel database padre nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile concedere per un ruolo applicazione, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione del ruolo applicazione|Autorizzazione del ruolo applicazione in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|---------------------------------|--------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY APPLICATION ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 L'utente che concede le autorizzazioni (o l'entità specificata con l'opzione AS) deve disporre della relativa autorizzazione con GRANT OPTION oppure di un'autorizzazione di livello superiore che include l'autorizzazione che viene concessa.  
  
 Se si utilizza l'opzione AS, sono previsti i requisiti aggiuntivi seguenti.  
  
|AS *granting_principal*|Autorizzazione aggiuntiva necessaria|  
|------------------------------|------------------------------------|  
|Utente del database|Autorizzazione IMPERSONATE per l'utente, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui è stato eseguito il mapping a un utente di Windows|Autorizzazione IMPERSONATE per l'utente, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui è stato eseguito il mapping a un gruppo di Windows|Appartenenza al gruppo di Windows, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui è stato eseguito il mapping a un certificato|Appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica|L'appartenenza al ruolo del database db_securityadminfixed, l'appartenenza al ruolo db_owner predefinito ruolo del database o l'appartenenza nel ruolo predefinito del server sysadmin.|  
|Utente del database di cui non è stato eseguito il mapping ad alcuna entità server|Autorizzazione IMPERSONATE per l'utente, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Ruolo del database|Autorizzazione ALTER nel ruolo, appartenenza al ruolo del database db_securityadminfixed, l'appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Ruolo applicazione|Autorizzazione ALTER per il ruolo, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
  
 Le entità con l'autorizzazione CONTROL per un'entità a protezione diretta possono concedere l'autorizzazione per quella entità.  
  
 Gli utenti che dispongono dell'autorizzazione CONTROL in un database, ad esempio i membri del ruolo predefinito del database db_owner, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-granting-control-permission-on-a-user-to-another-user"></a>A. Concessione a un altro utente dell'autorizzazione CONTROL per un utente  
 Nell'esempio seguente viene concessa l'autorizzazione `CONTROL` per l'utente `AdventureWorks2012` del database `Wanida` all'utente `RolandX`.  
  
```  
GRANT CONTROL ON USER::Wanida TO RolandX;  
GO  
```  
  
### <a name="b-granting-view-definition-permission-on-a-role-to-a-user-with-grant-option"></a>B. Concessione a un utente dell'autorizzazione VIEW DEFINITION per un ruolo con GRANT OPTION  
 Nell'esempio seguente viene concessa l'autorizzazione `VIEW DEFINITION` per il ruolo `AdventureWorks2012` del database `SammamishParking` insieme all'opzione `GRANT OPTION` all'utente di database `JinghaoLiu`.  
  
```  
GRANT VIEW DEFINITION ON ROLE::SammamishParking   
    TO JinghaoLiu WITH GRANT OPTION;  
GO  
```  
  
### <a name="c-granting-impersonate-permission-on-a-user-to-an-application-role"></a>C. Concessione a un ruolo applicazione dell'autorizzazione IMPERSONATE per un utente  
 Nell'esempio seguente viene concessa l'autorizzazione `IMPERSONATE` per l'utente `HamithaL` al ruolo applicazione `AdventureWorks2012` del database `AccountsPayable17`.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
```  
GRANT IMPERSONATE ON USER::HamithaL TO AccountsPayable17;  
GO    
```  
  
## <a name="see-also"></a>Vedere anche  
 [NEGARE autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)   
 [REVOKE-autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Sys. database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREAZIONE di ruolo &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
