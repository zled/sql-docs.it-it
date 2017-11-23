---
title: '[] (Carattere jolly per corrispondenze) (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Match
- wildcard
- '[ ]'
- '[_]_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[ ] (wildcard - character(s) to match)'
ms.assetid: 57817576-0bf1-49ed-b05d-fac27e8fed7a
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ee043b18eebafdc86b0d2d6e6a34afc0fc865c2f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="--wildcard---characters-to-match-transact-sql"></a>\[\] (Caratteri jolly - corrispondenza) (Transact-SQL)
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
  [% &#40; Carattere jolly - carattere &#40; s &#41; in corrispondenza &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
 [&#91; ^ &#93; &#40; Carattere jolly - carattere &#40; s &#41; Non corrispondenza &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [\_&#40; Carattere jolly - corrispondenze di singoli caratteri &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  
