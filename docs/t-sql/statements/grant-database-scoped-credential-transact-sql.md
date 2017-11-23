---
title: Credenziali (Transact-SQL) con ambito Database GRANT | Documenti Microsoft
ms.custom: 
ms.date: 06/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GRANT DATABASE SCOPED CREDENTIAL
- GRANT_DATABASE_SCOPED_CREDENTIAL_TSQL
dev_langs: TSQL
helpviewer_keywords:
- granting permissions [SQL Server], database scoped credential
- permissions [SQL Server], database scoped credential
- database scoped credential [SQL Server], permissions
- GRANT statement, database scoped credentials
ms.assetid: 501f2c8a-6aeb-41af-bf0b-974d17af33c0
caps.latest.revision: "3"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6dbd261334e580904e9c6ad3b12ff761d8c909ab
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="grant-database-scoped-credential-permissions-transact-sql"></a>Con ambito di Database di concedere le autorizzazioni delle credenziali (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Concede le autorizzazioni per un database di credenziali con ambito. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
GRANT permission  [ ,...n ]    
    ON DATABASE SCOPED CREDENTIAL :: credential_name   
    TO principal [ ,...n ] [ WITH GRANT OPTION ]   
    [ AS granting_principal ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Specifica un'autorizzazione che può essere concessa su un database di credenziali con ambito. Vedere l'elenco riportato di seguito.  
  
 NEL DATABASE SCOPED CREDENTIAL **::***credential_name*  
 Specifica le credenziali con ambito database per cui viene concessa l'autorizzazione. Il qualificatore di ambito "::" è obbligatorio.  
  
 *database_principal*  
 Specifica l'entità a cui viene concessa l'autorizzazione. I tipi validi sono:  
  
-   utente del database  
-   ruolo del database  
-   ruolo dell'applicazione  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
-   utente del database sul quale viene eseguito il mapping a un certificato  
-   utente del database mappato a una chiave asimmetrica  
-   utente del database non mappato ad alcuna entità server.  
  
GRANT OPTION  
 Indica che l'entità potrà inoltre concedere l'autorizzazione specificata ad altre entità.  
  
AS *granting_principal*  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di concedere l'autorizzazione. I tipi validi sono:  
  
-   utente del database  
-   ruolo del database  
-   ruolo dell'applicazione  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
-   utente del database sul quale viene eseguito il mapping a un certificato  
-   utente del database mappato a una chiave asimmetrica  
-   utente del database non mappato ad alcuna entità server.  
  
## <a name="remarks"></a>Osservazioni  
 Una credenziale con ambito database è un database a livello di entità a protezione diretta contenuta nel database padre nella gerarchia delle autorizzazioni. Le autorizzazioni più specifiche e limitate che possono essere concesse a una credenziale con ambito database sono elencate di seguito, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione delle credenziali con ambito database|Autorizzazione delle credenziali con ambito database cui è inclusa|Autorizzazione del database in cui è inclusa|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 L'utente che concede le autorizzazioni (o l'entità specificata con l'opzione AS) deve disporre della relativa autorizzazione con GRANT OPTION oppure di un'autorizzazione di livello superiore che include l'autorizzazione che viene concessa.  
  
 Se si usano l'opzione AS, sono previsti questi requisiti aggiuntivi.  
  
|AS *granting_principal*|Autorizzazione aggiuntiva necessaria|  
|------------------------------|------------------------------------|  
|Utente del database|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un gruppo di Windows|L'appartenenza al gruppo di Windows, appartenenza al gruppo il **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un certificato|L'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza di **db_owner** o l'appartenenza al ruolo il **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica|L'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza di **db_owner** o l'appartenenza al ruolo il **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui non è stato eseguito il mapping ad alcuna entità server|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Ruolo del database|L'autorizzazione ALTER per il ruolo, appartenenza al gruppo di **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
|Ruolo applicazione|L'autorizzazione ALTER per il ruolo, appartenenza al gruppo di **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
  
 I proprietari degli oggetti possono concedere autorizzazioni per gli oggetti di cui sono proprietari. Le entità con l'autorizzazione CONTROL per un'entità a sicurezza diretta possono concedere l'autorizzazione per quella entità.  
  
 Gli utenti che dispongono dell'autorizzazione CONTROL SERVER, ad esempio i membri del **sysadmin** ruolo predefinito del server, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel server. Gli utenti che dispongono dell'autorizzazione CONTROL per un database, ad esempio i membri del **db_owner** ruolo predefinito del database, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel database. Gli utenti che dispongono dell'autorizzazione CONTROL in uno schema, possono concedere qualsiasi autorizzazione per qualsiasi oggetto all'interno dello schema.  
  
## <a name="see-also"></a>Vedere anche  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Credenziali (Transact-SQL) con ambito Database REVOKE](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)   
 [DENY (Transact-SQL) credenziali con ambito Database](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
