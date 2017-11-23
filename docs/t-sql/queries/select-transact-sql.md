---
title: SELECT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT_TSQL
- SELECT
dev_langs: TSQL
helpviewer_keywords:
- retrieving rows
- SELECT statement [SQL Server]
- SELECT statement [SQL Server], about SELECT statement
- row retrieval [SQL Server], SELECT statement
- DML [SQL Server], SELECT statement
- data manipulation language [SQL Server], SELECT statement
- row retrieval [SQL Server]
- queries [SQL Server], results
ms.assetid: dc85caea-54d1-49af-b166-f3aa2f3a93d0
caps.latest.revision: "51"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 012853c97e01250bf5aee62d95ae7971549f5094
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="select-transact-sql"></a>SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Recupera righe dal database e consente la selezione di uno o più righe o colonne da uno o più tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La sintassi completa dell'istruzione SELECT è complessa, ma le clausole principali sono le seguenti:  
  
[Con {[WITH XMLNAMESPACES,] [ \<common_table_expression >]}]
  
 Selezionare *select_list* [INTO *new_table* ]  
  
 [Da *table_source* ] [dove *search_condition* ]  
  
 [GROUP BY *group_by_expression* ]  
  
 [Con *search_condition* ]  
  
 [ORDER BY *order_expression* [ASC | DESC]]  
  
 L'operatore UNION, EXCEPT e INTERSECT operatori possono essere utilizzati tra le query per combinare o confrontare i risultati in un set di risultati.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
<SELECT statement> ::=    
    [ WITH { [ XMLNAMESPACES ,] [ <common_table_expression> [,...n] ] } ]  
    <query_expression>   
    [ ORDER BY { order_by_expression | column_position [ ASC | DESC ] }   
  [ ,...n ] ]   
    [ <FOR Clause>]   
    [ OPTION ( <query_hint> [ ,...n ] ) ]   
<query_expression> ::=   
    { <query_specification> | ( <query_expression> ) }   
    [  { UNION [ ALL ] | EXCEPT | INTERSECT }  
        <query_specification> | ( <query_expression> ) [...n ] ]   
<query_specification> ::=   
SELECT [ ALL | DISTINCT ]   
    [TOP ( expression ) [PERCENT] [ WITH TIES ] ]   
    < select_list >   
    [ INTO new_table ]   
    [ FROM { <table_source> } [ ,...n ] ]   
    [ WHERE <search_condition> ]   
    [ <GROUP BY> ]   
    [ HAVING < search_condition > ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
[ WITH <common_table_expression> [ ,...n ] ]  
SELECT <select_criteria>  
[;]  
  
<select_criteria> ::=  
    [ TOP ( top_expression ) ]   
    [ ALL | DISTINCT ]   
    { * | column_name | expression } [ ,...n ]   
    [ FROM { table_source } [ ,...n ] ]  
    [ WHERE <search_condition> ]   
    [ GROUP BY <group_by_clause> ]   
    [ HAVING <search_condition> ]   
    [ ORDER BY <order_by_expression> ]  
    [ OPTION ( <query_option> [ ,...n ] ) ]  
  
```  
  
## <a name="remarks"></a>Osservazioni  
 A causa della complessità dell'istruzione SELECT, gli elementi della sintassi e gli argomenti dettagliati sono stati raggruppati e descritti in base alla clausola:  
  
|||  
|-|-|  
|[WITH XMLNAMESPACES](../../t-sql/xml/with-xmlnamespaces.md)<br /><br /> [WITH common_table_expression](../../t-sql/queries/with-common-table-expression-transact-sql.md)|[CON](../../t-sql/queries/select-having-transact-sql.md)|  
|[Clausola SELECT](../../t-sql/queries/select-clause-transact-sql.md)|[UNIONE](../../t-sql/language-elements/set-operators-union-transact-sql.md)|  
|[Clausola INTO](../../t-sql/queries/select-into-clause-transact-sql.md)|[EXCEPT e INTERSECT](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)|  
|[FROM](../../t-sql/queries/from-transact-sql.md)|[ORDER BY](../../t-sql/queries/select-order-by-clause-transact-sql.md)|  
|[WHERE](../../t-sql/queries/where-transact-sql.md)|[Clausola FOR](../../t-sql/queries/select-for-clause-transact-sql.md)|  
|[RAGGRUPPA PER](../../t-sql/queries/select-group-by-transact-sql.md)|[Clausola OPTION](../../t-sql/queries/option-clause-transact-sql.md)|  
  
 L'ordine delle clausole nell'istruzione SELECT è significativo. È possibile omettere qualsiasi clausola facoltativa, ma se tali clausole vengono utilizzate, è necessario specificarle nell'ordine corretto.  
  
 Le istruzioni SELECT sono consentite in funzioni definite dall'utente solo se gli elenchi di selezione di tali istruzioni includono espressioni per l'assegnazione di valori a variabili che sono locali rispetto alle funzioni.  
  
 Un nome composto da quattro parti costruito con la funzione OPENDATASOURCE come parte del nome di server può essere utilizzato come origine di tabella in qualsiasi punto di istruzioni SELECT in cui sono consentiti i nomi di tabella. Non è possibile specificare un nome composto da quattro parti per [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Per le istruzioni SELECT in cui sono coinvolte tabelle remote sono previste alcune limitazioni della sintassi.  
  
## <a name="logical-processing-order-of-the-select-statement"></a>Ordine di elaborazione logica dell'istruzione SELECT  
 Nei passaggi seguenti viene mostrato l'ordine di elaborazione logica, o ordine di associazione, per un'istruzione SELECT. Questo ordine consente di determinare il momento in cui gli oggetti definiti in un passaggio vengono resi disponibili per le clausole nei passaggi successivi. Ad esempio, se Query Processor può essere associato alle tabelle o alle viste definite nella clausola FROM, ovvero gli viene consentito l'accesso, questi oggetti e le relative colonne vengono resi disponibili in tutti i passaggi successivi. Invece, poiché la clausola SELECT si trova al passaggio 8, tramite le clausole precedenti non è possibile fare riferimento a qualsiasi alias di colonna o colonna derivata definito in tale clausola. Tuttavia, è possibile farvi riferimento tramite clausole successive, ad esempio ORDER BY. L'esecuzione fisica effettiva dell'istruzione è determinata da query processor e l'ordine può variare da questo elenco.  
  
1.  FROM  
2.  ON  
3.  JOIN  
4.  WHERE  
5.  GROUP BY  
6.  WITH CUBE o WITH ROLLUP  
7.  HAVING  
8.  SELECT  
9. DISTINCT  
10. ORDER BY  
11. Torna all'inizio  

> [!WARNING]
> La precedente sequenza si verifica in genere. Tuttavia, esistono casi non comuni in cui la sequenza può essere diverso.
>
> Si supponga, ad esempio, si dispone di un indice cluster in una vista, e la vista esclude alcune righe di tabella, elenco selezionare la colonna della vista utilizza una conversione che modifica un tipo di dati da *varchar* a *intero*. In questo caso, la funzione CONVERT può essere eseguita prima della clausola WHERE viene eseguita. Insolito effettivamente. Spesso è possibile modificare la vista per evitare la sequenza di diversi, se è importante nel caso specifico. 

## <a name="permissions"></a>Permissions  
 La selezione di dati richiede l'autorizzazione **SELECT** per la tabella o la vista che potrebbe essere ereditata da un ambito più elevato, ad esempio l'autorizzazione **SELECT** per lo schema o l'autorizzazione **CONTROL** per la tabella. O richiede l'appartenenza di **db_datareader** o **db_owner** ruoli predefiniti del database, o **sysadmin** ruolo predefinito del server. Creazione di una nuova tabella tramite **SELECTINTO** richiede inoltre il **CREATETABLE** autorizzazione e **ALTERSCHEMA** autorizzazione per lo schema a cui appartiene la nuova tabella.  
  
## <a name="examples"></a>Esempi:   
Nell'esempio seguente viene utilizzato il database [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
### <a name="a-using-select-to-retrieve-rows-and-columns"></a>A. Utilizzo dell'istruzione SELECT per il recupero di righe e colonne  
 Questa sezione illustra i tre esempi di codice. Questo primo esempio di codice restituisce tutte le righe (una clausola WHERE non omessa) e tutte le colonne (utilizzando la `*`) dal `DimEmployee` tabella.  
  
```sql  
SELECT *  
FROM DimEmployee  
ORDER BY LastName;  
```  
  
 Questo esempio l'utilizzo di alias di tabella per ottenere lo stesso risultato.  
  
```sql  
SELECT e.*  
FROM DimEmployee AS e  
ORDER BY LastName;  
```  
  
 Questo esempio vengono restituite tutte le righe (una clausola WHERE non omessa) e un subset delle colonne (`FirstName`, `LastName`, `StartDate`) dal `DimEmployee` tabella il `AdventureWorksPDW2012` database. Intestazione della terza colonna è stata rinominata `FirstDay`.  
  
```sql  
SELECT FirstName, LastName, StartDate AS FirstDay  
FROM DimEmployee   
ORDER BY LastName;  
```  
  
 Questo esempio vengono restituite solo le righe per `DimEmployee` che dispongono di un `EndDate` che non è NULL e un `MaritalStatus` di m' ' (sposato).  
  
```sql  
SELECT FirstName, LastName, StartDate AS FirstDay  
FROM DimEmployee   
WHERE EndDate IS NOT NULL   
AND MaritalStatus = 'M'  
ORDER BY LastName;  
```  
  
### <a name="b-using-select-with-column-headings-and-calculations"></a>B. Utilizzo dell'istruzione SELECT con intestazioni e calcoli di colonna  
 L'esempio seguente restituisce tutte le righe dal `DimEmployee` tabella e calcola la retribuzione lorda per ogni dipendente in base alle loro `BaseRate` e lavoro 40 ore alla settimana.  
  
```sql  
SELECT FirstName, LastName, BaseRate, BaseRate * 40 AS GrossPay  
FROM DimEmployee  
ORDER BY LastName;  
```  
  
### <a name="c-using-distinct-with-select"></a>C. Utilizzo della clausola DISTINCT con l'istruzione SELECT  
 L'esempio seguente usa `DISTINCT` per generare un elenco di tutti i titoli univoci nel `DimEmployee` tabella.  
  
```sql  
SELECT DISTINCT Title  
FROM DimEmployee  
ORDER BY Title;  
```  
  
### <a name="d-using-group-by"></a>D. Utilizzo della clausola GROUP BY  
 Nell'esempio seguente consente di trovare la quantità totale per tutte le vendite in ogni giorno.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
 Perché il `GROUP BY` clausola, per ciascun giorno in cui viene restituita solo una riga contenente la somma di tutte le vendite.  
  
### <a name="e-using-group-by-with-multiple-groups"></a>E. Utilizzo della clausola GROUP BY con più gruppi  
 Nell'esempio seguente consente di individuare il prezzo medio e la somma delle vendite Internet per ogni giorno, raggruppati per data dell'ordine e la chiave di innalzamento di livello.  
  
```sql  

SELECT OrderDateKey, PromotionKey, AVG(SalesAmount) AS AvgSales, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey, PromotionKey  
ORDER BY OrderDateKey;   
```  
  
### <a name="f-using-group-by-and-where"></a>F. Utilizzo delle clausole GROUP BY e WHERE  
 Nell'esempio seguente inserisce i risultati in gruppi dopo il recupero solo le righe con date successive a 1 agosto 2002.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
WHERE OrderDateKey > '20020801'  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
### <a name="g-using-group-by-with-an-expression"></a>G. Utilizzo della clausola GROUP BY con un'espressione  
 Nell'esempio seguente vengono creati gruppi in base a un'espressione. È possibile creare gruppi in base a un'espressione se tale espressione non include funzioni di aggregazione.  
  
```sql  
SELECT SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY (OrderDateKey * 10);  
```  
  
### <a name="h-using-group-by-with-order-by"></a>H. Utilizzo della clausola GROUP BY con la clausola ORDER BY  
 Nell'esempio seguente consente di trovare la somma delle vendite per ogni giorno e orders entro il giorno.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
### <a name="i-using-the-having-clause"></a>I. Utilizzo della clausola HAVING  
 Questa query utilizza la `HAVING` clausola per limitare i risultati.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
HAVING OrderDateKey > 20010000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Selezionare esempi &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)  
 [Hint per la &#40; Transact-SQL &#41;](../../t-sql/queries/hints-transact-sql.md)
  

