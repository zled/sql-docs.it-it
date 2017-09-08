---
title: La funzione DROP (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_FUNCTION_TSQL
- DROP FUNCTION
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined functions [SQL Server], removing
- removing user-defined functions
- DROP FUNCTION statement
- dropping user-defined functions
- deleting user-defined functions
ms.assetid: ee5ad283-9e44-4109-902f-0ce12669ee11
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b85cb68749cdcf88d62d9d8fbf136a37e845519
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-function-transact-sql"></a>DROP FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Rimuove dal database corrente una o più funzioni definite dall'utente. Funzioni definite dall'utente vengono create utilizzando [CREATE FUNCTION](../../t-sql/statements/create-function-transact-sql.md) e modificati tramite [ALTER FUNCTION](../../t-sql/statements/alter-function-transact-sql.md).  
  
 La funzione DROP supporta funzioni compilate in modo nativo e scalari definite dall'utente. Per ulteriori informazioni, vedere [funzioni scalari definite dall'utente per OLTP In memoria](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
 -- SQL Server, Azure SQL Database 

DROP FUNCTION [ IF EXISTS ] { [ schema_name. ] function_name } [ ,...n ]   
[;]
```

```  
 -- Azure SQL Data Warehouse, Parallel Data Warehouse 

DROP FUNCTION [ schema_name. ] function_name
[;] 
```  
   
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*    
 Elimina in modo condizionale la funzione solo se esiste già. Disponibile a partire da [!INCLUDE[ssnoversion_md](../../includes/ssnoversion_md.md)] 2016 e in [!INCLUDE[sssds_md](../../includes/sssds_md.md)].
  
 *schema_name*  
 Nome dello schema a cui appartiene la funzione definita dall'utente.  
  
 *nome_funzione*  
 Nome della funzione o delle funzioni definite dall'utente che si desidera rimuovere. Il nome dello schema è facoltativo. Non è possibile specificare il nome del server e il nome del database.  
  
## <a name="remarks"></a>Osservazioni  
 DROP FUNCTION ha esito negativo se nel database esistono funzioni o viste [!INCLUDE[tsql](../../includes/tsql-md.md)] che fanno riferimento a questa funzione e sono state create con l'opzione SCHEMABINDING oppure se esistono colonne calcolate, vincoli CHECK o vincoli DEFAULT che fanno riferimento a questa funzione.  
  
 DROP FUNCTION ha esito negativo se esistono colonne calcolate che fanno riferimento a questa funzione e sono state indicizzate.  
  
## <a name="permissions"></a>Permissions  
 Per eseguire l'istruzione DROP FUNCTION, è necessario disporre almeno dell'autorizzazione ALTER per lo schema a cui la funzione appartiene oppure dell'autorizzazione CONTROL per la funzione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-function"></a>A. Eliminazione di una funzione  
 Nell'esempio seguente viene eliminato il `fn_SalesByStore` funzione definita dall'utente dal `Sales` schema il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database di esempio. Per creare questa funzione, vedere l'esempio B in [CREATE FUNCTION &#40; Transact-SQL &#41; ](../../t-sql/statements/create-function-transact-sql.md).  
  
```  
DROP FUNCTION Sales.fn_SalesByStore;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-function-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Sys. Parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  

