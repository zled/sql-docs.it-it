---
title: INSERT (SQL grafico) | Documenti Microsoft
description: INSERIRE la sintassi per le tabelle di nodo o bordo grafico SQL.
ms.date: 05/12/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], SQL graph
- SQL graph, INSERT statement
ms.assetid: 
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e694d89efef130d2abcd5cd6424e2be576ef09de
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---

# <a name="insert-sql-graph"></a>INSERT (grafico SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]  

  Aggiunge uno o più righe a un `node` o `edge` tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 

> [!NOTE]   
>  Per istruzioni Transact-SQL standard, vedere [Inserisci tabella (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="insert-into-node-table-syntax"></a>INSERIRE la sintassi di tabella di nodo 
La sintassi per l'inserimento in una tabella di nodo è uguale a quella di una normale tabella. 

```  
[ WITH <common_table_expression> [ ,...n ] ]  
INSERT   
{  
        [ TOP ( expression ) [ PERCENT ] ]   
        [ INTO ]   
        { <object> | rowset_function_limited   
          [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
        }  
    {  
        [ (column_list) ] | [(<edge_table_column_list>)]  
        [ <OUTPUT Clause> ]  
        { VALUES ( { DEFAULT | NULL | expression } [ ,...n ] ) [ ,...n     ]   
        | derived_table   
        | execute_statement  
        | <dml_table_source>  
        | DEFAULT VALUES   
        }  
    }  
}  
[;]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
      | database_name .[ schema_name ] .   
      | schema_name .   
    ]  
    node_table_name  | edge_table_name
}  
  
<dml_table_source> ::=  
    SELECT <select_list>  
    FROM ( <dml_statement_with_output_clause> )   
      [AS] table_alias [ ( column_alias [ ,...n ] ) ]  
    [ WHERE <on_or_where_search_condition> ]  
        [ OPTION ( <query_hint> [ ,...n ] ) ]  

<on_or_where_search_condition> ::=
    {  <search_condition_with_match> | <search_condition> }

<search_condition_with_match> ::=
    { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) }
    [ AND { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<search_condition> ::=
    { [ NOT ] <predicate> | ( <search_condition> ) }
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<graph_predicate> ::=
    MATCH( <graph_search_pattern> [ AND <graph_search_pattern> ] [ , ...n] )

<graph_search_pattern>::=
    <node_alias> { { <-( <edge_alias> )- | -( <edge_alias> )-> } <node_alias> }

<edge_table_column_list> ::=
    ($from_id, $to_id, [column_list])

```  
  
 
## <a name="arguments"></a>Argomenti  
 Questo documento descrive gli argomenti relativi al grafico SQL. Per un elenco completo e una descrizione di argomenti supportati nell'istruzione INSERT, vedere [Inserisci tabella (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)

 INTO  
 Parola chiave facoltativa che può essere usato tra `INSERT` e la tabella di destinazione.  
  
 *search_condition_with_match*   
 `MATCH`clausola è utilizzabile in una sottoquery durante l'inserimento in una tabella edge o di nodo. Per `MATCH` sintassi dell'istruzione, vedere [grafico corrispondenza (Transact-SQL)](../../t-sql/queries/match-sql-graph.md)

 *graph_search_pattern*   
 Criterio di ricerca fornita per `MATCH` clausola come parte del predicato di grafico.

 *edge_table_column_list*   
 Gli utenti devono fornire valori per `$from_id` e `$to_id` durante l'inserimento di un bordo. Se non viene fornito un valore o i valori null vengono inseriti in tali colonne, verrà restituito un errore. 
  

## <a name="remarks"></a>Osservazioni  
Inserimento in un nodo corrisponde all'inserimento in qualsiasi tabella relazionale. I valori per la colonna node_id $ vengono generati automaticamente.

Durante l'inserimento in una tabella edge, gli utenti devono fornire valori per `$from_id` e `$to_id` colonne.   

BULK insert per la tabella di nodo è rimangono identici a quelli di una tabella relazionale.

Prima di massa di inserimento in una tabella edge, le tabelle di nodo devono essere importate. I valori del parametro `$from_id` e `$to_id` possono essere estratte dal `$node_id` colonna della tabella dei nodi e inserire come bordi. 

  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione INSERT per la tabella di destinazione.  
  
 INSERIMENTO di autorizzazioni per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server, il **db_owner** e **db_datawriter** fissa ruoli del database e il proprietario della tabella. I membri del **sysadmin**, **db_owner**e **db_securityadmin** ruoli e il proprietario della tabella possono trasferire autorizzazioni ad altri utenti.  
  
 Per eseguire INSERT con l'opzione BULK della funzione OPENROWSET, è necessario essere un membro del **sysadmin** ruolo predefinito del server o il **bulkadmin** ruolo predefinito del server.  
  

## <a name="examples"></a>Esempi  
  
#### <a name="a--insert-into-node-table"></a>A.  Inserire nella tabella del nodo  
 Nell'esempio seguente viene creata una tabella di nodo di persona e inserisce 2 righe nella tabella.

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 
 -- Insert records for Alice and John
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 ```
  
#### <a name="b--insert-into-edge-table"></a>B.  Inserire nella tabella edge  
 Nell'esempio seguente viene creata una tabella edge friend e inserisce un bordo della tabella.

 ```
 -- Create friend edge table
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Create a friend edge, that connect Alice and John
 INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');
 ```

  
## <a name="see-also"></a>Vedere anche  
 [Inserisci tabella &#40; Transact-SQL &#41;](../../t-sql/statements/insert-transact-sql.md)   
 [L'elaborazione con SQL Server 2017 grafico](../../relational-databases/graphs/sql-graph-overview.md)  



