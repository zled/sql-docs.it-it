---
title: (Carattere jolly alla corrispondenza) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Match
- wildcard
- '[ ]'
- '[_]_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[ ] (wildcard - character(s) to match)'
ms.assetid: 57817576-0bf1-49ed-b05d-fac27e8fed7a
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18688c96cd0369905844d79a1a109f4e5032bce3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="wildcard---characters-to-match-transact-sql"></a>(Carattere jolly alla corrispondenza) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Corrisponde a qualsiasi carattere singolo compreso nell'intervallo specificato o di un set specificato tra parentesi quadre `[ ]`. I caratteri jolly possono essere utilizzati nei confronti di stringa che coinvolgono i criteri di ricerca, ad esempio `LIKE` e `PATINDEX`.  
  
## <a name="examples"></a>Esempi  
### <a name="a-simple-example"></a>R: semplice esempio   
Nell'esempio seguente restituisce i nomi dei che iniziano con la lettera `m`. `[n-z]`Specifica che la seconda lettera deve essere un punto qualsiasi nell'intervallo da `n` a `z`. Il carattere jolly di percentuale `%` consente qualsiasi o nessuna caratteri a partire da 3 caratteri. Il `model` e `msdb` database soddisfino questi criteri. Il `master` non di database e viene escluso dal set di risultati.
 
```tsql
SELECT name FROM sys.databases
WHERE name LIKE 'm[n-z]%';
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]  

```
name
-----
model
msdb
```   
 È possibile database validi aggiuntivi installati.


### <a name="b-more-complex-example"></a>B: esempio più complesso   
 Nell'esempio seguente viene utilizzato l'operatore [] per trovare gli ID e i nomi di tutti i dipendenti inclusi in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] il cui indirizzo è associato a un C.A.P. a quattro cifre.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT e.BusinessEntityID, p.FirstName, p.LastName, a.PostalCode  
FROM HumanResources.Employee AS e  
INNER JOIN Person.Person AS p ON e.BusinessEntityID = p.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
INNER JOIN Person.Address AS a ON a.AddressID = ea.AddressID  
WHERE a.PostalCode LIKE '[0-9][0-9][0-9][0-9]';  
```  
  
 Set di risultati:  
  
```  
EmployeeID      FirstName      LastName      PostalCode  
----------      ---------      ---------     ----------  
290             Lynn           Tsoflias      3000  
```  



  
## <a name="see-also"></a>Vedere anche  
 [Ad esempio &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
  [% (Carattere jolly alla corrispondenza)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
 [&#91; ^ &#93; Mancata corrispondenza dei caratteri (jolly)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [_ (Carattere jolly per corrispondenze di singoli caratteri)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  

