---
title: DENY (Transact-SQL) credenziali con ambito Database | Documenti Microsoft
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DENY DATABASE SCOPED CREDENTIAL
- DENY_DATABASE_SCOPED_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DENY statement, database scoped credentials
- denying permissions [SQL Server], database scoped credential
ms.assetid: c508b1c9-169e-4e7a-9a49-7ddf2ca8f848
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dcb2ee7f32cea0c848850dc504a91067611b743e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="deny-database-scoped-credential-transact-sql"></a>DENY (Transact-SQL) credenziali con ambito Database
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

  Nega le autorizzazioni per una credenziale con ambito database.  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DENY permission  [ ,...n ]   
    ON DATABASE SCOPED CREDENTIAL :: credential_name   
    TO principal [ ,...n ]  
    [ CASCADE ]  
    [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Specifica un'autorizzazione che può essere negata per una credenziale con ambito database. Vedere l'elenco riportato di seguito.  
  
 NEL DATABASE SCOPED CREDENTIAL **::***credential_name*  
 Specifica le credenziali con ambito database per cui viene negata l'autorizzazione. Il qualificatore di ambito "::" è obbligatorio.  
  
 *database_principal*  
 Specifica l'entità a cui viene negata l'autorizzazione. I tipi validi sono:  
  
-   utente del database  
  
-   ruolo del database  
  
-   ruolo dell'applicazione  
  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
  
-   utente del database sul quale viene eseguito il mapping a un certificato  
  
-   utente del database mappato a una chiave asimmetrica  
  
-   utente del database non mappato ad alcuna entità server.  
  
 CASCADE  
 Indica che l'autorizzazione negata viene negata anche ad altre entità alle quali è stata concessa da questa entità.  
  
 *denying_principal*  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di negare l'autorizzazione. I tipi validi sono:  
  
-   utente del database  
  
-   ruolo del database  
  
-   ruolo dell'applicazione  
  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
  
-   utente del database sul quale viene eseguito il mapping a un certificato  
  
-   utente del database mappato a una chiave asimmetrica  
  
-   utente del database non mappato ad alcuna entità server.  
  
## <a name="remarks"></a>Osservazioni  
 Una credenziale con ambito database è un database a livello di entità a protezione diretta contenuta nel database padre nella gerarchia delle autorizzazioni. Le autorizzazioni più specifiche e limitate che è possibile negare per una credenziale con ambito database sono elencate di seguito, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione delle credenziali con ambito database|Autorizzazione delle credenziali con ambito database cui è inclusa|Autorizzazione del database in cui è inclusa|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione CONTROL per le credenziali con ambito database. Se viene utilizzata la clausola AS, l'entità specificata deve essere proprietaria di credenziali con ambito database.  
  
## <a name="see-also"></a>Vedere anche  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [Credenziali (Transact-SQL) con ambito database GRANT](../../t-sql/statements/grant-database-scoped-credential-transact-sql.md)   
 [REVOCA delle credenziali con ambito database (Transact-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

