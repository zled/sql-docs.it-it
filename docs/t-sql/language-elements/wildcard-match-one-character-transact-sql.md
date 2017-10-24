---
title: _ (Carattere jolly per corrispondenze di singoli caratteri) (Transact-SQL) | Documenti Microsoft
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
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- Match
- wildcard
- _TSQL
- Match One
- _
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- _ (wildcard - match one character)
ms.assetid: 11a2ed36-9e21-4bdf-ae20-a31db1434b97
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: a8992de1c0eadc11902bae537b97100a4b3cda55
ms.contentlocale: it-it
ms.lasthandoff: 10/24/2017

---
# <a name="-wildcard---match-one-character-transact-sql"></a>_ (carattere jolly per corrispondenze di singoli caratteri) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Utilizzare il carattere di sottolineatura _ per la corrispondenza di qualsiasi carattere singolo in un'operazione di confronto di stringhe che comporta un criterio di corrispondenza, ad esempio `LIKE` e `PATINDEX`.  
  
## <a name="examples"></a>Esempi  

## <a name="a-simple-example"></a>R: semplice esempio   

L'esempio seguente restituisce tutti i nomi che iniziano con la lettera di database `m` e avere la lettera `d` come la terza lettera. Il carattere di sottolineatura specifica che il secondo carattere del nome può essere qualsiasi lettera. Il `model` e `msdb` database soddisfino questi criteri. Il `master` non di database.

```tsql
SELECT name FROM sys.databases
WHERE name LIKE 'm_d%';
```   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-----
model
msdb
```   
È possibile database aggiuntivi che soddisfano questi criteri.

È possibile utilizzare più caratteri di sottolineatura per rappresentare più caratteri. Modifica il `LIKE` criteri per includere i due caratteri di sottolineatura `'m__%` include il database master nel risultato.

### <a name="b-more-complex-example"></a>B: esempio più complesso
 L'esempio seguente usa l'operatore _ per trovare tutti gli utenti di `Person` tabella, che hanno un nome che termina con tre lettere `an`.  
  
```tsql  
-- USE AdventureWorks2012
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE '_an'  
ORDER BY FirstName;  
```  
## <a name="c-escaping-the-underscore-character"></a>C: escape di il carattere di sottolineatura   
Nell'esempio seguente restituisce i nomi dei ruoli predefiniti del database come `db_owner` e `db_ddladmin`, ma restituisce inoltre il `dbo` utente. 

```tsql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db_%';
```

Il carattere di sottolineatura nella terza posizione di carattere verrà considerata come un carattere jolly e non Filtra per solo le entità inizia con le lettere `db_`. Caratteri di escape per il carattere di sottolineatura racchiudere tra parentesi quadre `[_]`. 

```tsql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db[_]%';
```   
A questo punto il `dbo` utente è escluso.   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-------------
db_owner
db_accessadmin
db_securityadmin
...
```

  
## <a name="see-also"></a>Vedere anche  
 [Ad esempio &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
  [% (Carattere jolly alla corrispondenza)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91; &#93; (Carattere jolly alla corrispondenza)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [&#91; ^ &#93; Mancata corrispondenza dei caratteri (jolly)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
  

