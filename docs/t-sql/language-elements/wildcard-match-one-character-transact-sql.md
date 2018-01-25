---
title: _ (Carattere jolly per corrispondenze di singoli caratteri) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
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
dev_langs: TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- _ (wildcard - match one character)
ms.assetid: 11a2ed36-9e21-4bdf-ae20-a31db1434b97
caps.latest.revision: "33"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 01bc0c4c006ae55395d752a0377575fa680dffaa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="-wildcard---match-one-character-transact-sql"></a>_ (carattere jolly per corrispondenze di singoli caratteri) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Utilizzare il carattere di sottolineatura _ per la corrispondenza di qualsiasi carattere singolo in un'operazione di confronto di stringhe che comporta un criterio di corrispondenza, ad esempio `LIKE` e `PATINDEX`.  
  
## <a name="examples"></a>Esempi  

## <a name="a-simple-example"></a>R: semplice esempio   

L'esempio seguente restituisce tutti i nomi che iniziano con la lettera di database `m` e avere la lettera `d` come la terza lettera. Il carattere di sottolineatura specifica che il secondo carattere del nome può essere qualsiasi lettera. Il `model` e `msdb` database soddisfino questi criteri. Il `master` non di database.

```sql
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
  
```sql  
-- USE AdventureWorks2012
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE '_an'  
ORDER BY FirstName;  
```  
## <a name="c-escaping-the-underscore-character"></a>C: escape di il carattere di sottolineatura   
Nell'esempio seguente restituisce i nomi dei ruoli predefiniti del database come `db_owner` e `db_ddladmin`, ma restituisce inoltre il `dbo` utente. 

```sql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db_%';
```

Il carattere di sottolineatura nella terza posizione di carattere verrà considerata come un carattere jolly e non Filtra per solo le entità inizia con le lettere `db_`. Caratteri di escape per il carattere di sottolineatura racchiudere tra parentesi quadre `[_]`. 

```sql
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
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)   
  [% (Carattere jolly alla corrispondenza)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91; &#93; (Carattere jolly alla corrispondenza)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [&#91; ^ &#93; Mancata corrispondenza dei caratteri (jolly)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
  
