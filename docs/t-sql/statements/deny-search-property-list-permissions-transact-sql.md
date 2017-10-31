---
title: NEGARE autorizzazioni Search Property List (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
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
- full-text search [SQL Server], permissions
- DENY statement, search property list permissions
- denying permissions [SQL Server], search property lists
- search property lists [SQL Server], permissions
ms.assetid: 96513cb4-a9c0-4834-97a4-ddc0777b8415
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6c7db64ebf313a13227797fba7ec222dcbdeafad
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="deny-search-property-list-permissions-transact-sql"></a>Autorizzazioni per l'elenco delle proprietà di ricerca DENY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Nega le autorizzazioni per un elenco di proprietà di ricerca.  
 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DENY permission [ ,...n ] ON  
        SEARCH PROPERTY LIST :: search_property_list_name  
    TO database_principal [ ,...n ] [ CASCADE ]  
    [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Nome di un'autorizzazione. I mapping validi tra le autorizzazioni e le entità a protezione diretta sono descritti nella sezione "Osservazioni" più avanti in questo argomento.  
  
ELENCO delle proprietà di ricerca **::***search_property_list_name*  
 Specifica l'elenco delle proprietà di ricerca per cui viene negata l'autorizzazione. Il qualificatore di ambito :: è obbligatorio.  
  
*database_principal*  
 Specifica l'entità a cui viene negata l'autorizzazione. Le possibili entità sono le seguenti:  
  
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
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di negare l'autorizzazione. Le possibili entità sono le seguenti:  
  
-   utente del database  
-   ruolo del database  
-   ruolo dell'applicazione  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
-   utente del database sul quale viene eseguito il mapping a un certificato  
-   utente del database mappato a una chiave asimmetrica  
-   utente del database non mappato ad alcuna entità server.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="search-property-list-permissions"></a>Autorizzazioni SEARCH PROPERTY LIST  
 Un elenco di proprietà di ricerca è un'entità a protezione diretta a livello di database contenuta nel database padre nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile negare per un elenco di proprietà di ricerca, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazioni per l'elenco delle proprietà di ricerca|Autorizzazioni dell'elenco delle proprietà di ricerca in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per il catalogo full-text. Se si utilizza l'opzione AS, l'entità specificata deve essere proprietaria del catalogo full-text.  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE APPLICATION ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE SEARCH PROPERTY LIST &#40; Transact-SQL &#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [Autorizzazioni GRANT Search Property List &#40; Transact-SQL &#41;](../../t-sql/statements/grant-search-property-list-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [REVOCARE autorizzazioni Search Property List &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-search-property-list-permissions-transact-sql.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [registered_search_property_lists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  

