---
title: NEGARE autorizzazioni per raccolte XML Schema (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], XML schema collections
- XML schema collections [SQL Server], permissions
- DENY statement, XML schema collections
- schema collections [SQL Server], permissions
ms.assetid: 159969a7-8313-41bc-bb19-c55af76597e6
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a2851147a37d9a99ab2f1fee8c1e3083e7a5f4fd
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="deny-xml-schema-collection-permissions-transact-sql"></a>DENY - autorizzazioni per raccolte di XML Schema (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Nega le autorizzazioni per una raccolta di XML Schema.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DENY permission  [ ,...n ] ON   
    XML SCHEMA COLLECTION :: [ schema_name . ]  
    XML_schema_collection_name  
    TO <database_principal> [ ,...n ]  
        [ CASCADE ]  
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
 *permission*  
 Specifica un'autorizzazione che può essere negata per una raccolta di XML Schema. Per un elenco delle autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 RACCOLTA di XML SCHEMA ON:: [ *schema_name * * *.* *] *XML_schema_collection_name*  
 Specifica la raccolta di XML Schema per cui viene negata l'autorizzazione. Il qualificatore di ambito (::) è obbligatorio. Se *schema_name* viene omesso, viene utilizzato lo schema predefinito. Se *schema_name* è specificato, il qualificatore di ambito dello schema (.) è obbligatorio.  
  
 PER \<database_principal >  
 Specifica l'entità a cui viene negata l'autorizzazione.  
  
 CASCADE  
 Indica che l'autorizzazione negata viene negata anche ad altre entità alle quali è stata concessa da questa entità.  
  
 AS \<database_principal >  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di negare l'autorizzazione.  
  
 *Database_user*  
 Specifica un utente di database.  
  
 *Database_role*  
 Specifica un ruolo del database.  
  
 *Application_role*  
 Specifica un ruolo applicazione.  
  
 *Database_user_mapped_to_Windows_User*  
 Specifica un utente del database sul quale viene eseguito il mapping a un utente di Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Specifica un utente del database sul quale viene eseguito il mapping a un gruppo di Windows.  
  
 *Database_user_mapped_to_certificate*  
 Specifica un utente del database sul quale viene eseguito il mapping a un certificato.  
  
 *Database_user_mapped_to_asymmetric_key*  
 Specifica un utente del database sul quale viene eseguito il mapping a una chiave asimmetrica.  
  
 *Database_user_with_no_login*  
 Specifica un utente del database per cui non esiste un'entità corrispondente a livello del server.  
  
## <a name="remarks"></a>Osservazioni  
 Informazioni sulle raccolte di XML schema sono visibile nel [xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) vista del catalogo.  
  
 Una raccolta di XML Schema è un'entità a protezione diretta a livello di schema contenuta nello schema padre nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile negare per una raccolta di XML Schema, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione della raccolta di XML Schema|Autorizzazione della raccolta di XML Schema in cui è inclusa|Autorizzazione dello schema in cui è inclusa|  
|--------------------------------------|-------------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|EXECUTE|CONTROL|EXECUTE|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL per la raccolta di XML Schema. Se si utilizza l'opzione AS, l'entità specificata deve essere proprietaria della raccolta di XML Schema.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene negata l'autorizzazione `EXECUTE` per la raccolta di XML Schema `Invoices4` all'utente `Wanida`. La raccolta di XML Schema `Invoices4` è incluso nello schema `Sales` del database `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
DENY EXECUTE ON XML SCHEMA COLLECTION::Sales.Invoices4 TO Wanida;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [GRANT-autorizzazioni per raccolte XML Schema &#40; Transact-SQL &#41;](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)   
 [REVOCARE autorizzazioni per raccolte XML Schema &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-xml-schema-collection-permissions-transact-sql.md)   
 [sys.xml_schema_collections &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md)   
 [CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;Motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
