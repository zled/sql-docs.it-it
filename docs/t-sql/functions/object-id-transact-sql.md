---
title: Object_id (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECT_ID
- OBJECT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], IDs
- identification numbers [SQL Server], database objects
- checking object exists
- IDs [SQL Server], database objects
- OBJECT_ID function
- database objects [SQL Server], IDs
- displaying object IDs
- viewing object IDs
- verifying object exists
ms.assetid: f89286db-440f-4218-a828-30881ce3077a
caps.latest.revision: 63
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a612928c3a30b48d3dc8e1dedd4375ca564555d8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="objectid-transact-sql"></a>OBJECT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il numero di identificazione di oggetto di database di un oggetto con ambito schema.  
  
> [!IMPORTANT]  
>  Gli oggetti senza ambito schema, ad esempio i trigger DDL, non possono essere soggetti a query tramite OBJECT_ID. Per gli oggetti che non si trovano nel [Sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vista del catalogo, ottenere il numero di identificazione eseguendo una query sulla vista del catalogo appropriata. Ad esempio, per restituire il numero di identificazione di oggetto di un trigger DDL, utilizzare `SELECT OBJECT_ID FROM sys.triggers WHERE name = 'DatabaseTriggerLog``'`.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
OBJECT_ID ( '[ database_name . [ schema_name ] . | schema_name . ]   
  object_name' [ ,'object_type' ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *object_name* **'**  
 Oggetto da utilizzare. *object_name* è **varchar** o **nvarchar**. Se *object_name* è **varchar**, viene convertito implicitamente in **nvarchar**. L'indicazione dei nomi dello schema e del database è facoltativa.  
  
 **'** *object_type* **'**  
 Tipo di oggetto a livello di ambito dello schema. *object_type* è **varchar** o **nvarchar**. Se *object_type* è **varchar**, viene convertito implicitamente in **nvarchar**. Per un elenco di tipi di oggetto, vedere il **tipo** colonna [Sys. Objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="exceptions"></a>Eccezioni  
 Per un indice spaziale, OBJECT_ID restituisce NULL.  
  
 Restituisce Null in caso di errore.  
  
 Un utente può visualizzare esclusivamente i metadati delle entità a sicurezza diretta di cui è proprietario o per cui ha ricevuto un'autorizzazione. Di conseguenza, le funzioni predefinite di creazione dei metadati come OBJECT_ID possono restituire NULL se l'utente non dispone di alcuna autorizzazione per l'oggetto. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Osservazioni  
 Se il parametro per una funzione di sistema è facoltativo, vengono utilizzati il database, il computer host, l'utente del server o l'utente del database correnti. Le funzioni predefinite devono essere sempre seguite da parentesi.  
  
 Quando viene specificato un nome di tabella temporanea, il nome del database deve precedere il nome della tabella temporanea, a meno che il database corrente è **tempdb**. Esempio: `SELECT OBJECT_ID('tempdb..#mytemptable')`.  
  
 È possibile utilizzare funzioni di sistema nell'elenco di selezione, nella clausola WHERE e in tutti i casi in cui è consentita un'espressione. Per ulteriori informazioni, vedere [espressioni &#40; Transact-SQL &#41; ](../../t-sql/language-elements/expressions-transact-sql.md) e [in &#40; Transact-SQL &#41; ](../../t-sql/queries/where-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-object-id-for-a-specified-object"></a>A. Restituzione dell'ID oggetto per un oggetto specificato  
 Nell'esempio seguente viene restituito l'ID oggetto per la tabella `Production.WorkOrder` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE master;  
GO  
SELECT OBJECT_ID(N'AdventureWorks2012.Production.WorkOrder') AS 'Object ID';  
GO  
```  
  
### <a name="b-verifying-that-an-object-exists"></a>B. Verifica dell'esistenza di un oggetto  
 Nell'esempio seguente viene controllata l'esistenza di una tabella specificata mediante la verifica della presenza dell'ID oggetto. Se la tabella esiste, verrà eliminata. Se la tabella non esiste, l'istruzione `DROP TABLE` non verrà eseguita.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'dbo.AWBuildVersion', N'U') IS NOT NULL  
DROP TABLE dbo.AWBuildVersion;  
GO  
```  
  
### <a name="c-using-objectid-to-specify-the-value-of-a-system-function-parameter"></a>C. Utilizzo di OBJECT_ID per specificare il valore di un parametro di una funzione di sistema  
 L'esempio seguente restituisce informazioni per tutti gli indici e partizioni del `Person.Address` tabella il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database utilizzando il [Sys.dm db_index_operational_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md) (funzione).  
  
> [!IMPORTANT]  
>  Quando si utilizzano le funzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] DB_ID e OBJECT_ID per restituire un valore di parametro, verificare sempre che venga restituito un ID valido. Se risulta impossibile trovare il nome del database o dell'oggetto, ad esempio quando tali nomi non esistono o sono stati immessi con un'ortografia errata, entrambe le funzioni restituiranno NULL. Il **Sys.dm db_index_operational_stats** funzione interpreta NULL come valore di carattere jolly che specifica tutti i database o tutti gli oggetti. Poiché può trattarsi di un'operazione accidentale, gli esempi riportati in questa sezione dimostrano la procedura sicura per determinare gli ID di database e oggetti.  
  
```  
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-returning-the-object-id-for-a-specified-object"></a>Unità d: restituzione dell'ID di oggetto per un oggetto specificato  
 Nell'esempio seguente viene restituito l'ID oggetto per la tabella `FactFinance` nel database [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].  
  
```  
SELECT OBJECT_ID(AdventureWorksPDW2012.dbo.FactFinance') AS 'Object ID';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [Sys. Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Sys.dm db_index_operational_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [Object_name &#40; Transact-SQL &#41;](../../t-sql/functions/object-name-transact-sql.md)  
  
  


