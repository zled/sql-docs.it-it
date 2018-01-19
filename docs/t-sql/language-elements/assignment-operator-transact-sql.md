---
title: = (Operatore di assegnazione) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- operators [Transact-SQL], assignment
- assignment operators [Transact-SQL]
- headings [SQL Server columns]
- relationships [SQL Server], assignment operators
- column headings [SQL Server]
ms.assetid: c3040db6-21d6-40ac-a783-82c98ec006cc
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1a4a3e1634579ecb985a6c99fc4973d7f8717c94
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="-assignment-operator-transact-sql"></a>= (Assignment Operator) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Il segno di uguale (=) è l'unico operatore di assegnazione supportato in [!INCLUDE[tsql](../../includes/tsql-md.md)]. Nell'esempio seguente viene creata la variabile `@MyCounter` e quindi viene utilizzato l'operatore di assegnazione per impostare `@MyCounter` su un valore restituito da un'espressione.  
  
```  
DECLARE @MyCounter INT;  
SET @MyCounter = 1;  
```  
  
 È inoltre possibile utilizzare l'operatore di assegnazione per stabilire una relazione tra l'intestazione di una colonna e l'espressione che definisce i valori di tale colonna. Nell'esempio seguente vengono visualizzate le intestazioni di colonna `FirstColumnHeading` e `SecondColumnHeading`. Nell'intestazione di colonna `xyz` viene visualizzata la stringa `FirstColumnHeading` per tutte le righe e nell'intestazione di colonna `Product` vengono elencati gli ID di tutti i prodotti della tabella `SecondColumnHeading`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstColumnHeading = 'xyz',  
       SecondColumnHeading = ProductID  
FROM Production.Product;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Composta operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
