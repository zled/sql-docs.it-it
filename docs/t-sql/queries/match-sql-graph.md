---
title: CORRISPONDENZA (SQL grafico) | Documenti Microsoft
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MATCH
- MATCH_TSQL
dev_langs: TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
ms.assetid: 
caps.latest.revision: "1"
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8944c6b5ca481e61a1ca18e7c453d2c2035e1acb
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="match-transact-sql"></a>CORRISPONDENZA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

  Specifica una condizione di ricerca per un grafico. CORRISPONDENZA possa essere utilizzata solo con graph nodo e bordo tabelle, nell'istruzione SELECT come parte della clausola WHERE. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
MATCH (<graph_search_pattern>)

<graph_search_pattern>::=
    {<node_alias> { 
                     { <-( <edge_alias> )- } 
                   | { -( <edge_alias> )-> }
                 <node_alias> 
                 } 
     }
     [ { AND } { ( <graph_search_pattern> ) } ]
     [ ,...n ]
  
<node_alias> ::=
    node_table_name | node_alias 

<edge_alias> ::=
    edge_table_name | edge_alias
```

## <a name="arguments"></a>Argomenti  
*graph_search_pattern*  
Specifica il criterio di ricerca o un percorso di attraversare il grafico. Questo modello Usa sintassi ClipArt ASCII per attraversare un percorso nel grafico. Il modello passa da un nodo a un altro tramite un bordo, nella direzione della freccia fornita. Bordo nomi o gli alias vengono forniti all'interno di parantheses. I nomi dei nodi o gli alias vengono visualizzati alle due estremità della freccia. La freccia può andare in entrambe le direzioni nel modello.

*node_alias*  
Nome o alias di una tabella di nodo specificata nella clausola FROM.

*edge_alias*  
Nome o alias di una tabella edge fornita nella clausola FROM.


## <a name="remarks"></a>Osservazioni  
I nomi dei nodi all'interno di corrispondenza può essere ripetuti.  In altre parole, un nodo può essere attraversato un numero arbitrario di volte nella stessa query.  
Il nome di un bordo non può essere ripetuto all'interno di corrispondenza.  
Un bordo può puntare in entrambe le direzioni, ma deve essere una direzione esplicita.  
O e non gli operatori non sono supportati nel criterio di corrispondenza. CORRISPONDENZA può essere combinata con altre espressioni utilizzando e nella clausola WHERE. Tuttavia, integrarlo con altre espressioni tramite OR o non è supportato. 

## <a name="examples"></a>Esempi  
### <a name="a--find-a-friend"></a>A.  Trovare un elemento friend 
 Nell'esempio seguente crea una tabella di nodo di persona e una tabella Edge amici, inserisce alcuni dati e quindi Usa corrispondenza per trovare gli elementi Friend di Alice, una persona nel grafico.

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Insert into node table
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 INSERT INTO dbo.Person VALUES (3, 'Jacob');

-- Insert into edge table
INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');

INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'Jacob'), '10/15/2011');

INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'John'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'Jacob'), '10/15/2012');

-- use MATCH in SELECT to find friends of Alice
SELECT Person2.name AS FriendName
FROM Person Person1, friend, Person Person2
WHERE MATCH(Person1-(friend)->Person2)
AND Person1.name = 'Alice';

 ```

 ### <a name="b--find-friend-of-a-friend"></a>B.  Trovare l'elemento friend di un elemento friend
 Nell'esempio seguente tenta di trovare l'elemento friend di un elemento friend di Alice. 

 ```
SELECT Person3.name AS FriendName 
FROM Person Person1, friend, Person Person2, friend friend2, Person Person3
WHERE MATCH(Person1-(friend)->Person2-(friend2)->Person3)
AND Person1.name = 'Alice';

 ```

### <a name="c--more-match-patterns"></a>C.  Ulteriori `MATCH` modelli
 Di seguito sono alcuni altri modi in cui è possibile specificare un criterio all'interno di corrispondenza.

 ```
 -- Find a friend
    SELECT Person2.name AS FriendName
    FROM Person Person1, friend, Person Person2
    WHERE MATCH(Person1-(friend)->Person2);
    
-- The pattern can also be expressed as below

    SELECT Person2.name AS FriendName
    FROM Person Person1, friend, Person Person2 
    WHERE MATCH(Person2<-(friend)-Person1);


-- Find 2 people who are both friends with same person
    SELECT Person1.name AS Friend1, Person2.name AS Friend2
    FROM Person Person1, friend friend1, Person Person2, 
         friend friend2, Person Person0
    WHERE MATCH(Person1-(friend1)->Person0<-(friend2)-Person2);
    
-- this pattern can also be expressed as below

    SELECT Person1.name AS Friend1, Person2.name AS Friend2
    FROM Person Person1, friend friend1, Person Person2, 
         friend friend2, Person Person0
    WHERE MATCH(Person1-(friend1)->Person0 AND Person2-(friend2)->Person0);
 ```
 

## <a name="see-also"></a>Vedere anche  
 [CREARE una tabella &#40; Grafico SQL &#41;](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (SQL grafico)](../../t-sql/statements/insert-sql-graph.md)]  
 [L'elaborazione con SQL Server 2017 grafico](../../relational-databases/graphs/sql-graph-overview.md)  
