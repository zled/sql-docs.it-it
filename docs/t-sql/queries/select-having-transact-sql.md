---
title: CON (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HAVING
- HAVING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restricting conditions for result set
- search conditions [SQL Server], HAVING clause
- HAVING clause
- HAVING clause, about HAVING clause
ms.assetid: 55650709-001e-42f4-902f-ead09a3c34af
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9bff75a84689090f6e416db052a2561e57fa98a6
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="select---having-transact-sql"></a>SELECT - con (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Specifica una condizione di ricerca per un gruppo o una funzione di aggregazione. Può essere specificata solo nell'istruzione SELECT. In genere viene inclusa in una clausola GROUP BY. Se la clausola GROUP BY non è specificata, la funzionalità della clausola HAVING corrisponde a quella di una clausola WHERE.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ HAVING <search condition> ]  
```  
  
## <a name="arguments"></a>Argomenti  
\<search_condition > specifica la condizione di ricerca per il gruppo o l'aggregazione deve soddisfare.  
  
 Il **testo**, **immagine**, e **ntext** tipi di dati non possono essere utilizzati in una clausola HAVING.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata una clausola `HAVING` semplice per recuperare il totale di ogni voce `SalesOrderID` maggiore di `SalesOrderDetail` dalla tabella `$100000.00`.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail  
GROUP BY SalesOrderID  
HAVING SUM(LineTotal) > 100000.00  
ORDER BY SalesOrderID ;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente viene utilizzato un `HAVING` clausola per recuperare il totale per ogni `SalesAmount` dal `FactInternetSales` tabella quando la `OrderDateKey` rientra nell'anno 2004 o versione successiva.  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING SUM(SalesAmount) > 80000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Clausola GROUP BY &#40; Transact-SQL &#41;](../../t-sql/queries/select-group-by-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


