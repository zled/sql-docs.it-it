---
title: "È NULL (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NULL_TSQL
- IS_[NOT]_NULL_TSQL
- IS_NULL_TSQL
- NULL
- '[NOT]_TSQL'
- IS
- IS_TSQL
- IS NULL
- IS [NOT] NULL
- '[NOT]'
dev_langs:
- TSQL
helpviewer_keywords:
- verifying nullability
- IS NOT NULL clause
- null values [SQL Server], verifying
- null values [SQL Server], IS [NOT] NULL
- IS [NOT] NULL clause
- testing nullability
- checking nullability
ms.assetid: cdc45cd8-e9b6-4648-8417-892fbeab15af
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 047e4fd57b91155485fddc2459e94247bb923c7e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="is-null-transact-sql"></a>È NULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Determina se un'espressione specificata è NULL.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 NOT  
 Determina la negazione del risultato booleano. Il predicato inverte i valori restituiti. Restituisce TRUE se il valore non è NULL e FALSE se il valore è NULL.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="return-code-values"></a>Valori restituiti  
 Se il valore di *espressione* è NULL, IS NULL restituisce TRUE; in caso contrario, restituisce FALSE.  
  
 Se il valore di *espressione* è NULL, IS NOT NULL restituisce FALSE; in caso contrario, restituisce TRUE.  
  
## <a name="remarks"></a>Osservazioni  
 Per determinare se un'espressione è NULL, utilizzare la funzione IS NULL o IS NOT NULL anziché gli operatori di confronto, ad esempio = o !=, i quali restituiscono UNKNOWN se uno o entrambi gli argomenti sono NULL.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti il nome e il peso di tutti i prodotti con un peso inferiore a `10` libbre oppure il cui colore non è noto o è `NULL`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name, Weight, Color  
FROM Production.Product  
WHERE Weight < 10.00 OR Color IS NULL  
ORDER BY Name;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'esempio seguente restituisce i nomi completi di tutti i dipendenti con secondi nomi.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, MiddleName  
FROM DIMEmployee  
WHERE MiddleName IS NOT NULL  
ORDER BY LastName DESC;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CASE &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [Ad esempio &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori logici &#40; Transact-SQL &#41;](../../t-sql/language-elements/logical-operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


