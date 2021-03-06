---
title: DROP FUNCTION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9aea2cb62ad12745a8ad03fd9998a47ee77173e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838608"
---
# <a name="drop-function-transact-sql"></a>DROP FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove dal database corrente una o più funzioni definite dall'utente. Le funzioni definite dall'utente vengono create usando l'istruzione [CREATE FUNCTION](../../t-sql/statements/create-function-transact-sql.md) e modificate usando l'istruzione [ALTER FUNCTION](../../t-sql/statements/alter-function-transact-sql.md).  
  
 La funzione DROP supporta le funzioni scalari definite dall'utente e compilate in modo nativo. Per altre informazioni, vedere [Funzioni scalari definite dall'utente per OLTP in memoria](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
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
 *IF EXISTS*    
 Rimuove in modo condizionale la funzione solo se esiste già. Disponibile a partire da [!INCLUDE[ssnoversion_md](../../includes/ssnoversion-md.md)] 2016 e [!INCLUDE[sssds_md](../../includes/sssds-md.md)].
  
 *schema_name*  
 Nome dello schema a cui appartiene la funzione definita dall'utente.  
  
 *function_name*  
 Nome della funzione o delle funzioni definite dall'utente che si desidera rimuovere. Il nome dello schema è facoltativo. Non è possibile specificare il nome del server e il nome del database.  
  
## <a name="remarks"></a>Remarks  
 DROP FUNCTION ha esito negativo se nel database esistono funzioni o viste [!INCLUDE[tsql](../../includes/tsql-md.md)] che fanno riferimento a questa funzione e sono state create con l'opzione SCHEMABINDING oppure se esistono colonne calcolate, vincoli CHECK o vincoli DEFAULT che fanno riferimento a questa funzione.  
  
 DROP FUNCTION ha esito negativo se esistono colonne calcolate che fanno riferimento a questa funzione e sono state indicizzate.  
  
## <a name="permissions"></a>Permissions  
 Per eseguire l'istruzione DROP FUNCTION, è necessario disporre almeno dell'autorizzazione ALTER per lo schema a cui la funzione appartiene oppure dell'autorizzazione CONTROL per la funzione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-function"></a>A. Eliminazione di una funzione  
 L'esempio seguente elimina la funzione definita dall'utente `fn_SalesByStore` dallo schema `Sales` nel database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Per creare questa funzione, vedere l'esempio B in [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md).  
  
```  
DROP FUNCTION Sales.fn_SalesByStore;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-function-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  
