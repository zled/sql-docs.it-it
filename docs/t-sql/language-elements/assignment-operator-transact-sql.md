---
title: Operatore di assegnazione (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- operators [Transact-SQL], assignment
- assignment operators [Transact-SQL]
- headings [SQL Server columns]
- relationships [SQL Server], assignment operators
- column headings [SQL Server]
ms.assetid: c3040db6-21d6-40ac-a783-82c98ec006cc
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d10872712d1b7114655b5d95ab9b871709c55b14
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="assignment-operator-transact-sql"></a>Operatore di assegnazione (Transact-SQL)
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
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
