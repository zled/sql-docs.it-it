---
title: '&lt;= (Minore o uguale a) (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- <=
- Less
- Equal To
- <=_TSQL
- Less Than
- Equal
dev_langs:
- TSQL
helpviewer_keywords:
- <= (less than or equal to operator)
- less than or equal to operator (<=)
ms.assetid: 1f05474c-0377-48cb-b567-9d85d0c40479
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c3604745940bff9695f6a961661b3ee99fe6171a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lt-less-than-or-equal-to-transact-sql"></a>&lt;= (Minore o uguale a) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Confronta due espressioni (operatore di confronto). Quando si confrontano due espressioni diverse da Null, il risultato è TRUE se il valore dell'operando di sinistra è minore o uguale al valore di quello di destra. In caso contrario il risultato è FALSE.  
  
 A differenza dell'operatore = (uguaglianza), il risultato del confronto >= tra due valori NULL non dipende dall'impostazione di ANSI_NULLS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
expression <= expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md). È necessario che il tipo di dati di entrambe le espressioni possa essere convertito in modo implicito. La conversione dipende dalle regole di [precedenza dei tipi di dati](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using--in-a-simple-query"></a>A. Utilizzando < = in una query semplice  
 Nell'esempio seguente vengono restituite tutte le righe nella tabella `HumanResources.Department` che dispongono di un valore in `DepartmentID` minore o uguale a 3.  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID <= 3  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
1            Engineering  
2            Tool Design  
3            Sales  
  
(3 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
