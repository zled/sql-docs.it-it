---
title: L'autorizzazione ALTER SCHEMA (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER SCHEMA
- ALTER_SCHEMA_TSQL
dev_langs: TSQL
helpviewer_keywords:
- objects [SQL Server], transferring
- transferring objects between schemas
- ALTER SCHEMA statement
- schemas [SQL Server], modifying
- modifying schemas
ms.assetid: 0a760138-460e-410a-a3c1-d60af03bf2ed
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: bcbc6cf4ed18bef5d4736375dd7eddaaa1167a33
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-schema-transact-sql"></a>ALTER SCHEMA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Trasferisce un'entità a protezione diretta da uno schema a un altro.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER SCHEMA schema_name   
   TRANSFER [ <entity_type> :: ] securable_name   
[;]  
  
<entity_type> ::=  
    {  
    Object | Type | XML Schema Collection  
    }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER SCHEMA schema_name   
   TRANSFER [ OBJECT :: ] securable_name   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome di uno schema nel database corrente in cui verrà spostata l'entità a protezione diretta. Non può essere SYS o INFORMATION_SCHEMA.  
  
 \<entity_type >  
 Classe dell'entità per la quale viene modificato il proprietario. L'oggetto rappresenta l'impostazione predefinita.  
  
 *securable_name*  
 Nome composto da una o due parti di un'entità a protezione diretta inclusa nello schema da spostare nello schema.  
  
## <a name="remarks"></a>Osservazioni  
 Utenti e schemi sono completamente distinti.  
  
 È possibile utilizzare ALTER SCHEMA solo per spostare le entità a protezione diretta tra schemi presenti nello stesso database. Per modificare o eliminare un'entità a sicurezza diretta all'interno di uno schema, utilizzare l'istruzione ALTER o DROP specifica dell'entità a sicurezza diretta desiderata.  
  
 Se viene utilizzato un nome di una parte per *securable_name*, le regole di risoluzione dei nomi attualmente in vigore verranno utilizzate per individuare l'entità a protezione diretta.  
  
 Tutte le autorizzazioni associate all'entità a sicurezza diretta vengono eliminate quando l'entità viene spostata nel nuovo schema. Se è stato impostato in modo esplicito, il proprietario dell'entità a sicurezza diretta rimarrà invariato. Se impostato su SCHEMA OWNER, il proprietario dell'entità a protezione diretta rimarrà SCHEMA OWNER. Tuttavia, in seguito allo spostamento SCHEMA OWNER verrà risolto nel nome del proprietario del nuovo schema. Il valore di principal_id del nuovo proprietario sarà NULL.  
  
 Per modificare lo schema di una tabella o vista utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Esplora oggetti, fare doppio clic su tabella o della vista e quindi fare clic su **progettazione**. Premere **F4** per aprire la finestra Proprietà. Nel **Schema** , selezionare un nuovo schema.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Per trasferire un'entità a sicurezza diretta da un altro schema, l'utente deve disporre dell'autorizzazione CONTROL per l'entità (non per lo schema) e dell'autorizzazione ALTER per lo schema di destinazione.  
  
 Se l'entità a sicurezza diretta è associata a una specifica dell'istruzione EXECUTE AS OWNER e il proprietario è impostato su SCHEMA OWNER, l'utente deve inoltre disporre dell'autorizzazione IMPERSONATION per il proprietario dello schema di destinazione.  
  
 Tutte le autorizzazioni associate all'entità a protezione diretta in fase di trasferimento vengono eliminate al momento dello spostamento.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-transferring-ownership-of-a-table"></a>A. Trasferimento della proprietà di una tabella  
 Nell'esempio seguente viene modificato lo schema `HumanResources` mediante il trasferimento nello schema della tabella `Address` dello schema `Person`.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER SCHEMA HumanResources TRANSFER Person.Address;  
GO  
```  
  
### <a name="b-transferring-ownership-of-a-type"></a>B. Trasferimento della proprietà di un tipo  
 Nell'esempio seguente viene creato un tipo nello schema `Production`, quindi il tipo viene trasferito nello schema `Person`.  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TYPE Production.TestType FROM [varchar](10) NOT NULL ;  
GO  
  
-- Check the type owner.  
SELECT sys.types.name, sys.types.schema_id, sys.schemas.name  
    FROM sys.types JOIN sys.schemas   
        ON sys.types.schema_id = sys.schemas.schema_id   
    WHERE sys.types.name = 'TestType' ;  
GO  
  
-- Change the type to the Person schema.  
ALTER SCHEMA Person TRANSFER type::Production.TestType ;  
GO  
  
-- Check the type owner.  
SELECT sys.types.name, sys.types.schema_id, sys.schemas.name  
    FROM sys.types JOIN sys.schemas   
        ON sys.types.schema_id = sys.schemas.schema_id   
    WHERE sys.types.name = 'TestType' ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-transferring-ownership-of-a-table"></a>C. Trasferimento della proprietà di una tabella  
 Nell'esempio seguente viene creata una tabella `Region` nel `dbo` dello schema, crea un `Sales` dello schema e quindi sposta il `Region` tabella il `dbo` dello schema per il `Sales` dello schema.  
  
```  
CREATE TABLE dbo.Region   
    (Region_id int NOT NULL,  
    Region_Name char(5) NOT NULL)  
WITH (DISTRIBUTION = REPLICATE);  
GO  
  
CREATE SCHEMA Sales;  
GO  
  
ALTER SCHEMA Sales TRANSFER OBJECT::dbo.Region;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREAZIONE dello SCHEMA &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [DROP SCHEMA &#40; Transact-SQL &#41;](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

