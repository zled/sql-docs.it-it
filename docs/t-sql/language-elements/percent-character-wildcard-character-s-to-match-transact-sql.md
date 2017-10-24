---
title: Il carattere di percentuale (carattere jolly per corrispondenze) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Data Warehouse
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- '%'
- '%_TSQL'
- wildcard
dev_langs:
- TSQL
helpviewer_keywords:
- conditions [SQL Server], wildcards
- '% (wildcard - character(s) to match)'
- matching conditions [SQL Server]
- wildcard characters [SQL Server]
- characters [SQL Server], wildcard
ms.assetid: d4cbc1a9-37e1-4101-97fb-e6ac30c1223e
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 63891f4f25781d1a4e7f169d42c4db779d5a9c12
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="percent-character-wildcard---characters-to-match-transact-sql"></a>Carattere di percentuale (carattere jolly) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Corrisponde a qualsiasi stringa composta da zero o più caratteri. Questo carattere jolly può essere utilizzato come prefisso o suffisso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti i nomi delle persone elencate nella tabella `Person` del database `AdventureWorks2012` che iniziano con `Dan`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Dan%';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ad esempio &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
 [&#91; &#93; (Carattere jolly alla corrispondenza)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
  [&#91; ^ &#93; Mancata corrispondenza dei caratteri (jolly)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [_ (Carattere jolly per corrispondenze di singoli caratteri)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  

