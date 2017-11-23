---
title: RAGGRUPPAMENTO (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- GROUP
- CUBE
- ROLLUP
- GROUPING_SETS_TSQL
- GROUP BY
- GROUPING SETS
- GROUP_BY_TSQL
- GROUP_TSQL
- CUBE_TSQL
- ROLLUP_TSQL
dev_langs: TSQL
helpviewer_keywords:
- GROUP BY clause, about GROUP BY clause
- dividing tables into groups
- GROUPING SETS
- GROUP BY clause
- table groups [SQL Server]
- groups [SQL Server], tables divided into groups
- summary values [SQL Server]
ms.assetid: 40075914-6385-4692-b4a5-62fe44ae6cb6
caps.latest.revision: "80"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 49b572a8ce91287faa4c162efa8de8e7f0113235
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="select---group-by--transact-sql"></a>Selezionare - GROUP - BY Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Una clausola dell'istruzione SELECT che divide il risultato della query in gruppi di righe, in genere per eseguire una o più aggregazioni su ogni gruppo. L'istruzione SELECT restituisce una riga per ogni gruppo.  
  
## <a name="syntax"></a>Sintassi  

 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
```  
-- Syntax for SQL Server and Azure SQL Database   
-- ISO-Compliant Syntax  
  
GROUP BY {
      column-expression  
    | ROLLUP ( <group_by_expression> [ ,...n ] )  
    | CUBE ( <group_by_expression> [ ,...n ] )  
    | GROUPING SETS ( <grouping_set> [ ,...n ]  )  
    | () --calculates the grand total 
} [ ,...n ] 
 
<group_by_expression> ::=  
      column-expression  
    | ( column-expression [ ,...n ] )    
   
<grouping_set> ::=  
      () --calculates the grand total  
    | <grouping_set_item>  
    | ( <grouping_set_item> [ ,...n ] )  
  
<grouping_set_item> ::=  
      <group_by_expression>  
    | ROLLUP ( <group_by_expression> [ ,...n ] )  
    | CUBE ( <group_by_expression> [ ,...n ] )  
  

-- For backward compatibility only.
-- Non-ISO-Compliant Syntax for SQL Server and Azure SQL Database 
  
GROUP BY 
      [ ALL ] column-expression [ ,...n ] 
    | column-expression [ ,...n ] [ WITH { CUBE | ROLLUP } ]   

```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
GROUP BY {
      column-name [ WITH (DISTRIBUTED_AGG) ]  
    | column-expression
} [ ,...n ]

```  
  
## <a name="arguments"></a>Argomenti 
 
### <a name="column-expression"></a>*espressione di colonna*  
Specifica una colonna o un calcolo non di aggregazione su una colonna. Questa colonna può appartenere a una tabella, una tabella derivata o una vista. La colonna deve essere presente nella clausola FROM dell'istruzione SELECT, ma non è necessaria visualizzare nell'elenco di selezione. 

Per le espressioni valide, vedere [espressione](~/t-sql/language-elements/expressions-transact-sql.md).    

La colonna deve essere presente nella clausola FROM dell'istruzione SELECT, ma non è necessaria visualizzare nell'elenco di selezione. Tuttavia, ogni tabella o vista di colonna in qualsiasi espressione non di aggregazione di \<selezionare > elenco deve essere incluso nell'elenco GROUP BY:  
  
Le istruzioni seguenti sono consentite:  
  
    ```  
    SELECT ColumnA, ColumnB FROM T GROUP BY ColumnA, ColumnB;  
    SELECT ColumnA + ColumnB FROM T GROUP BY ColumnA, ColumnB;  
    SELECT ColumnA + ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    SELECT ColumnA + ColumnB + constant FROM T GROUP BY ColumnA, ColumnB;  
    ```  
  
Le istruzioni seguenti non sono consentite:  
  
    ```  
    SELECT ColumnA, ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    SELECT ColumnA + constant + ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    ```  
L'espressione della colonna non può contenere:

- Un alias di colonna definito nell'elenco di selezione. È possibile utilizzare un alias di colonna per una tabella derivata definita nella clausola FROM.
- Una colonna di tipo **testo**, **ntext**, o **immagine**. Tuttavia, è possibile utilizzare una colonna di text, ntext o image come argomento a una funzione che restituisce un valore di un tipo di dati validi. Ad esempio, l'espressione è possibile utilizzare substring () e cast (). Questo vale anche per le espressioni nella clausola HAVING.
- metodi con tipo di dati XML. Può includere una funzione definita dall'utente che utilizza i metodi con tipo di dati xml. Può includere una colonna calcolata che utilizza i metodi con tipo di dati xml. 
- Sottoquery. Viene restituito l'errore 144. 
- Una colonna da una vista indicizzata. 
 
### <a name="group-by-column-expression--n-"></a>GROUP BY *espressione di colonna* [,... n] 

Raggruppa i risultati dell'istruzione SELECT in base ai valori in un elenco di uno o più espressioni di colonna. 

Questa query, ad esempio, crea una tabella Sales con le colonne per paese, regione e Sales. Inserisce quattro righe e due delle righe con valori corrispondenti per paese e area.  

```
CREATE TABLE Sales ( Country varchar(50), Region varchar(50), Sales int );

INSERT INTO sales VALUES (N'Canada', N'Alberta', 100);
INSERT INTO sales VALUES (N'Canada', N'British Columbia', 200);
INSERT INTO sales VALUES (N'Canada', N'British Columbia', 300);
INSERT INTO sales VALUES (N'United States', N'Montana', 100);
```
La tabella Sales contiene queste righe:

| Country | Region | Sales |
|---------|--------|-------|
| Canada | Alberta | 100 |
| Canada | British Columbia | 200 |
| Canada | British Columbia | 300 |
| United States | Montana | 100 |

Questa query successiva Raggruppa paese e area geografica e restituisce la somma di aggregazione per ogni combinazione di valori.  
 
``` 
SELECT Country, Region, SUM(sales) AS TotalSales
FROM Sales
GROUP BY Country, Region;
```
Poiché sono presenti 3 combinazioni di valori per paese e area, il risultato della query è 3 righe. I totali di vendite per il Canada e British Columbia è la somma di due righe. 

| Country | Region | TotalSales |
|---------|--------|-------|
| Canada | Alberta | 100 |
| Canada | British Columbia | 500 |
| United States | Montana | 100 |

### <a name="group-by-rollup"></a>GROUP BY ROLLUP

Crea un gruppo per ogni combinazione di espressioni di colonna. Inoltre, "esegue il rollup" i risultati in subtotali e totali complessivi. A tale scopo, vengono spostati da destra a sinistra, riducendo il numero di espressioni di colonna su cui viene creato il aggregation(s) e gruppi. 

L'ordine delle colonne influisce sull'output di ROLLUP e può influire sul numero di righe nel set di risultati.  

Ad esempio, `GROUP BY ROLLUP (col1, col2, col3, col4)` crea gruppi per ogni combinazione di espressioni di colonna negli elenchi seguenti.  

- Col1, col2, col3, col4 
- Col1, col2, col3, NULL
- Col1, col2, NULL, NULL
- Col1, NULL, NULL, NULL
- NULL, NULL, NULL, NULL, questo è il totale complessivo

Utilizzando la tabella dell'esempio precedente, questo codice viene eseguita un'operazione GROUP BY ROLLUP anziché una clausola GROUP BY semplice.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY ROLLUP (Country, Region);
```

Il risultato della query ha le stesse aggregazioni come la clausola GROUP BY semplice senza il ROLLUP. Inoltre, crea i subtotali per ogni valore del paese. Infine, offre un totale complessivo per tutte le righe. Il risultato è simile al seguente:

| Country | Region | TotalSales |
| :------ | :----- | ---------: |
| Canada | Alberta | 100 |
| Canada | British Columbia | 500 |
| Canada | NULL | 600 |
| United States | Montana | 100 |
| United States | NULL | 100 |
| NULL | NULL | 700 |

### <a name="group-by-cube--"></a>GROUP BY () DEL CUBO  

GROUP BY CUBE consente di creare gruppi per tutte le possibili combinazioni di colonne. Dispone di gruppi per i valori univoci per GROUP BY CUBE (a, b) i risultati di (a, b), (NULL, b), (a, NULL) e (NULL, NULL).

Utilizzando la tabella degli esempi precedenti, questo codice esegue un'operazione GROUP BY CUBE sul paese e area. 

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY CUBE (Country, Region);
```

Il risultato della query ha gruppi per i valori univoci di (Country, Region), (NULL, area), (paese, NULL) e (NULL, NULL). I risultati è simile al seguente:

| Country | Region | TotalSales |
|---------|--------|-------|
| Canada | Alberta | 100 |
| NULL | Alberta | 100 |
| Canada | British Columbia | 500 |
| NULL | British Columbia | 500 |
| United States | Montana | 100 |
| NULL | Montana | 100 |
| NULL | NULL | 700
| Canada | NULL | 600 |
| United States | NULL | 100 |
   
 ### <a name="group-by-grouping-sets--"></a>GROUP BY () SET DI RAGGRUPPAMENTO  
 
L'opzione di GROUPING SETS offre la possibilità di combinare più clausole GROUP BY in una clausola GROUP BY. I risultati rappresentano l'equivalente di quelli della clausola UNION ALL dei gruppi specificati. 

Ad esempio, `GROUP BY ROLLUP (Country, Region)` e `GROUP BY GROUPING SETS ( ROLLUP (Country, Region) )` restituiscono gli stessi risultati. 

Quando GROUPING SETS dispone di due o più elementi, i risultati sono un'unione degli elementi. In questo esempio restituisce l'unione dei risultati di ROLLUP e CUBE per paese e area.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY GROUPING SETS ( ROLLUP (Country, Region), CUBE (Country, Region) );
```

I risultati sono gli stessi come la query che restituisce l'unione delle due istruzioni GROUP BY.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY ROLLUP (Country, Region)
UNION ALL
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY CUBE (Country, Region)
;
```

SQL non consolidare gruppi duplicati generati per un elenco GROUPING SETS. Ad esempio, in `GROUP BY ( (), CUBE (Country, Region) )`, entrambi gli elementi restituiscano una riga per il totale complessivo ed entrambe le righe verranno elencate nei risultati. 

 ### <a name="group-by-"></a>GROUP BY ()  
Specifica il gruppo vuoto che genera il totale complessivo. Ciò è utile come uno degli elementi di un SET di raggruppamento. Ad esempio, questa istruzione offre le vendite totali per ogni singolo paese e fornisce i totali complessivi per tutti i paesi.

```
SELECT Country, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY GROUPING SETS ( Country, () );
```

### <a name="group-by--all--column-expression--n-"></a>GROUP BY [ALL]-espressione di colonna [,... n] 

Si applica a: SQL Server e Database SQL di Azure

Nota: Questa sintassi è fornita solo per la compatibilità. Verrà rimosso in una versione futura. Evitare di usare questa sintassi in nuovi progetti di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa sintassi.

Specifica di includere tutti i gruppi nei risultati indipendentemente dal fatto che siano soddisfatti i criteri di ricerca nella clausola WHERE. Gruppi che non soddisfano i criteri di ricerca hanno valore NULL per l'aggregazione. 

RAGGRUPPA TUTTE:
- Non è supportata nelle query che accedono a tabelle remote se esiste anche una clausola WHERE della query.
- Avrà esito negativo in colonne che includono l'attributo FILESTREAM.
  
### <a name="with-distributedagg"></a>CON (DISTRIBUTED_AGG)
Si applica a: Azure SQL Data Warehouse e Parallel Data Warehouse

Hint per la query DISTRIBUTED_AGG impone al sistema di elaborazione parallela massiva (. MPP) per la ridistribuzione di una tabella in una colonna specifica prima di eseguire un'aggregazione. Solo una colonna nella clausola GROUP BY può contenere hint DISTRIBUTED_AGG per la query. Al termine dell'esecuzione della query, viene eliminata la tabella ridistribuita. La tabella originale non viene modificata.  

Nota: L'hint DISTRIBUTED_AGG per la query viene fornito per la compatibilità con le versioni precedenti di Parallel Data Warehouse e non migliorerà le prestazioni per la maggior parte delle query. Per impostazione predefinita, MPP già dati vengono ridistribuiti in base alle esigenze per migliorare le prestazioni per le aggregazioni. 
  
## <a name="general-remarks"></a>Osservazioni generali

### <a name="how-group-by-interacts-with-the-select-statement"></a>GROUP BY interazione con l'istruzione SELECT
Elenco di selezione:
- Aggregazioni vettoriali. Se le funzioni di aggregazione sono inclusi nell'elenco di selezione, GROUP BY calcola un valore di riepilogo per ogni gruppo. Tali funzioni sono denominate aggregazioni vettoriali. 
- Aggregazioni DISTINCT. Le funzioni di aggregazione AVG (DISTINCT *column_name*), COUNT (DISTINCT *column_name*) e SUM (DISTINCT *column_name*) sono supportati con ROLLUP, CUBE e GROUPING SETS.
  
Clausola WHERE:
- SQL rimuove le righe che non soddisfano le condizioni nella clausola WHERE prima di eseguire qualsiasi operazione di raggruppamento.  
  
Clausola HAVING:
- SQL utilizza la presenza di una clausola per filtrare gruppi nel set di risultati. 
  
Clausola ORDER BY:
- Per eseguire questa operazione, utilizzare la clausola ORDER BY. La clausola GROUP BY non ordina il set di risultati. 
  
Valori NULL:
- Se una colonna di raggruppamento contiene valori NULL, tutti i valori NULL vengono considerati uguali e vengono raccolti in un unico gruppo.   
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni

Si applica a: SQL Server (a partire da 2008) e Azure SQL Data Warehouse

### <a name="maximum-capacity"></a>Capacità massima

Per una clausola GROUP BY che utilizza ROLLUP, CUBE o GROUPING SETS, il numero massimo di espressioni è 32. Il numero massimo di gruppi è 4096 (2<sup>12</sup>). Negli esempi seguenti esito negativo perché la clausola GROUP BY è 4096 più gruppi.  
 
-   Nell'esempio seguente viene generati 4.097 (2<sup>12</sup> + 1) set di raggruppamenti e avrà esito negativo.  
  
    ```  
    GROUP BY GROUPING SETS( CUBE(a1, ..., a12), b )  
    ```  
  
-   Nell'esempio seguente viene generati 4.097 (2<sup>12</sup> + 1) gruppi e avrà esito negativo. Sia `CUBE ()` sia il set di raggruppamenti `()` consentono di generare una riga del totale complessivo e i set di raggruppamenti duplicati non vengono eliminati.  
  
    ```  
    GROUP BY GROUPING SETS( CUBE(a1, ..., a12), ())  
    ```  

-   In questo esempio viene utilizzata la sintassi compatibile con le versioni precedenti. Genera 8192 (2<sup>13</sup>) set di raggruppamenti e avrà esito negativo.  
  
    ```  
    GROUP BY CUBE (a1, ..., a13)   
    GROUP BY a1, ..., a13 WITH CUBE   
    ```    
    Per compatibilità a ritroso clausole GROUP BY che non contengono CUBE o ROLLUP, il numero di group by items è limitato dalle RAGGRUPPA dimensioni delle colonne, le colonne aggregate, e i valori di aggregazione coinvolti nella query. Tale limite è correlato al limite di 8.060 byte della tabella di lavoro intermedia necessaria per mantenere i risultati intermedi delle query. Quando viene specificato l'operatore CUBE o ROLLUP, sono consentite al massimo 12 espressioni di raggruppamento.

### <a name="support-for-iso-and-ansi-sql-2006-group-by-features"></a>Supporto per le funzionalità GROUP BY di SQL-2006 ISO e ANSI

La clausola GROUP BY supporta tutte le funzionalità GROUP BY incluse nello standard SQL-2006 con le eccezioni di sintassi seguenti:  
  
-   Nella clausola GROUP BY non è consentito utilizzare set di raggruppamenti a meno che non appartengano a un elenco GROUPING SETS esplicito. Ad esempio, `GROUP BY Column1, (Column2, ...ColumnN`) è consentita nello standard, ma non in Transact-SQL.  Transact-SQL supporta `GROUP BY C1, GROUPING SETS ((Column2, ...ColumnN))` e `GROUP BY Column1, Column2, ... ColumnN`, che sono semanticamente equivalenti. Queste espressioni sono semanticamente equivalenti a quelle dell'esempio relativo a `GROUP BY` precedente. Per evitare la possibilità che `GROUP BY Column1, (Column2, ...ColumnN`) potrebbe essere erroneamente interpretata come `GROUP BY C1, GROUPING SETS ((Column2, ...ColumnN))`, che non sono semanticamente equivalenti.  
  
-   L'utilizzo di set di raggruppamenti non è consentito all'interno di GROUPING SETS. Ad esempio, `GROUP BY GROUPING SETS (A1, A2,…An, GROUPING SETS (C1, C2, ...Cn))` è consentita nello standard SQL-2006 ma non in Transact-SQL. Consente di Transact-SQL `GROUP BY GROUPING SETS( A1, A2,...An, C1, C2, ...Cn )` o `GROUP BY GROUPING SETS( (A1), (A2), ... (An), (C1), (C2), ... (Cn) )`, che sono semanticamente equivalenti al primo esempio GROUP BY e una sintassi più chiara.  
  
-   GROUP BY [ALL/DISTINCT] è consentito solo in una clausola GROUP BY semplice che contiene espressioni di colonna. Non è consentito con i costrutti di GROUPING SETS, ROLLUP, CUBE, WITH CUBE o WITH ROLLUP. ALL è il valore predefinito ed è implicito. È consentito anche solo la sintassi compatibile con le versioni precedenti.
  
### <a name="comparison-of-supported-group-by-features"></a>Confronto tra le funzionalità GROUP BY supportate  
 Nella tabella seguente descrive le funzionalità GROUP BY supportate in base alle versioni di SQL e a livello di compatibilità del database.  
  
|Funzionalità|SQL Server Integration Services|Livello di compatibilità di SQL Server 100 o superiore|Livello di compatibilità di SQL Server 2008 o versioni successive pari a 90.|  
|-------------|-------------------------------------|--------------------------------------------------|-----------------------------------------------------------|  
|Aggregazioni DISTINCT|Non supportate per WITH CUBE o WITH ROLLUP.|Supportate per WITH CUBE, WITH ROLLUP, GROUPING SETS, CUBE o ROLLUP.|Comportamento analogo al livello di compatibilità pari a 100.|  
|Funzione definita dall'utente denominata CUBE o ROLLUP nella clausola GROUP BY|Funzione definita dall'utente **dbo. CUBE (***arg1***,***... argN***)** o  **dbo. rollup (***arg1***,**... *argN***)** in GROUP BY clausola è consentita.<br /><br /> Ad esempio: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`|Funzione definita dall'utente **dbo. CUBE (***arg1***,**... argN**)** o **dbo. rollup (**arg1**,***... argN***)** in GROUP BY clausola non è consentita.<br /><br /> Ad esempio: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`<br /><br /> Viene restituito il seguente messaggio di errore: "sintassi non corretta in prossimità del cubo' parola chiave' &#124;' rollup'. "<br /><br /> Per evitare questo problema, sostituire `dbo.cube` con `[dbo].[cube]` oppure `dbo.rollup` con `[dbo].[rollup]`.<br /><br /> Nell'esempio seguente è consentito:`SELECT SUM (x) FROM T  GROUP BY [dbo].[cube](y);`|Funzione definita dall'utente **dbo. CUBE (***arg1***,***... argN*) o **dbo. rollup (** *arg1***,***... argN***)** in GROUP BY clausola è consentita<br /><br /> Ad esempio: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`|  
|GROUPING SETS|Non supportato|Supportato|Supportato|  
|CUBE|Non supportato|Supportato|Non supportato|  
|ROLLUP|Non supportato|Supportato|Non supportato|  
|Totale complessivo, ad esempio GROUP BY ()|Non supportato|Supportato|Supportato|  
|GROUPING_ID - funzione|Non supportato|Supportato|Supportato|  
|GROUPING - funzione|Supportato|Supportato|Supportato|  
|WITH CUBE|Supportato|Supportato|Supportato|  
|WITH ROLLUP|Supportato|Supportato|Supportato|  
|Rimozione di raggruppamenti duplicati relativa a WITH CUBE o WITH ROLLUP|Supportato|Supportato|Supportato| 
 
  
## <a name="examples"></a>Esempi  
  
### <a name="a-use-a-simple-group-by-clause"></a>A. Utilizzare una clausola GROUP BY semplice  
 Nell'esempio seguente viene recuperato il totale per ogni `SalesOrderID` dalla tabella `SalesOrderDetail`. Questo esempio viene usato AdventureWorks.  
  
```  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail AS sod  
GROUP BY SalesOrderID  
ORDER BY SalesOrderID;  
```  
  
### <a name="b-use-a-group-by-clause-with-multiple-tables"></a>B. Utilizzare una clausola GROUP BY con più tabelle  
 Nell'esempio seguente viene recuperato il numero di dipendenti per ogni `City` dalla tabella `Address` unita in join alla tabella `EmployeeAddress`. Questo esempio viene usato AdventureWorks. 
  
```  
SELECT a.City, COUNT(bea.AddressID) EmployeeCount  
FROM Person.BusinessEntityAddress AS bea   
    INNER JOIN Person.Address AS a  
        ON bea.AddressID = a.AddressID  
GROUP BY a.City  
ORDER BY a.City;  
```  
  
### <a name="c-use-a-group-by-clause-with-an-expression"></a>C. Utilizzare una clausola GROUP BY con un'espressione  
 Nell'esempio seguente vengono recuperate le vendite totali per ogni anno tramite la funzione `DATEPART`. La stessa espressione deve essere presente sia nell'elenco `SELECT` che nella clausola `GROUP BY`.  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,SUM(TotalDue) AS N'Total Order Amount'  
FROM Sales.SalesOrderHeader  
GROUP BY DATEPART(yyyy,OrderDate)  
ORDER BY DATEPART(yyyy,OrderDate);  
```  
  
### <a name="d-use-a-group-by-clause-with-a-having-clause"></a>D. Utilizzare una clausola GROUP BY con una clausola HAVING  
 Nell'esempio seguente viene utilizzata la clausola `HAVING` per specificare quale gruppo generato nella clausola `GROUP BY` deve essere incluso nel set di risultati.  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,SUM(TotalDue) AS N'Total Order Amount'  
FROM Sales.SalesOrderHeader  
GROUP BY DATEPART(yyyy,OrderDate)  
HAVING DATEPART(yyyy,OrderDate) >= N'2003'  
ORDER BY DATEPART(yyyy,OrderDate);  
```  
  
## <a name="examples-sql-data-warehouse-and-parallel-data-warehouse"></a>Esempi: SQL Data Warehouse e Parallel Data Warehouse  
  
### <a name="e-basic-use-of-the-group-by-clause"></a>E. Utilizzo di base della clausola GROUP BY  
 Nell'esempio seguente consente di trovare la quantità totale per tutte le vendite in ogni giorno. Una sola riga contenente la somma di tutte le vendite viene restituita per ogni giorno.  
  
```  
-- Uses AdventureWorksDW  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales FROM FactInternetSales  
GROUP BY OrderDateKey ORDER BY OrderDateKey;  
```  
  
### <a name="f-basic-use-of-the-distributedagg-hint"></a>F. Utilizzo di base dell'hint DISTRIBUTED_AGG  
 Questo esempio viene utilizzato l'hint DISTRIBUTED_AGG per la query per forzare il dispositivo da riprodurre in modo casuale la tabella di `CustomerKey` colonna prima di eseguire l'aggregazione.  
  
```  
-- Uses AdventureWorksDW  
  
SELECT CustomerKey, SUM(SalesAmount) AS sas  
FROM FactInternetSales  
GROUP BY CustomerKey WITH (DISTRIBUTED_AGG)  
ORDER BY CustomerKey DESC;  
```  
  
### <a name="g-syntax-variations-for-group-by"></a>G. Per RAGGRUPPARE le differenze di sintassi  
 Quando l'elenco di selezione non è nessuna aggregazione, ogni colonna nell'elenco di selezione deve essere incluso nell'elenco GROUP BY. Nell'elenco Seleziona le colonne calcolate possono essere elencate, ma non sono necessari, nell'elenco GROUP BY. Questi sono esempi di istruzioni SELECT sintatticamente valide:  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, FirstName FROM DimCustomer GROUP BY LastName, FirstName;  
SELECT NumberCarsOwned FROM DimCustomer GROUP BY YearlyIncome, NumberCarsOwned;  
SELECT (SalesAmount + TaxAmt + Freight) AS TotalCost FROM FactInternetSales GROUP BY SalesAmount, TaxAmt, Freight;  
SELECT SalesAmount, SalesAmount*1.10 SalesTax FROM FactInternetSales GROUP BY SalesAmount;  
SELECT SalesAmount FROM FactInternetSales GROUP BY SalesAmount, SalesAmount*1.10;  
```  
  
### <a name="h-using-a-group-by-with-multiple-group-by-expressions"></a>H. Utilizzare GROUP BY con più espressioni di raggruppamento  
 Nell'esempio seguente vengono raggruppati i risultati usando più `GROUP BY` criteri. Se, all'interno di ogni `OrderDateKey` gruppo esistono sottogruppi che possono essere differenziati da `DueDateKey`, verrà definito un nuovo raggruppamento per il set di risultati.  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, DueDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSalesGROUP BY OrderDateKey, DueDateKey   
ORDER BY OrderDateKey;  
```  
  
### <a name="i-using-a-group-by-clause-with-a-having-clause"></a>I. Utilizzo di una clausola GROUP BY con una clausola HAVING  
 L'esempio seguente usa il `HAVING` clausola per specificare i gruppi generati nel `GROUP BY` clausola che deve essere incluse nel set di risultati. Nei risultati verranno inclusi solo i gruppi con le date degli ordini nel 2004 o versione successiva.  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING OrderDateKey > 20040000   
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [GROUPING_ID &#40; Transact-SQL &#41;](~/t-sql/functions/grouping-id-transact-sql.md)   
 [RAGGRUPPAMENTO &#40; Transact-SQL &#41;](~/t-sql/functions/grouping-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](~/t-sql/queries/select-transact-sql.md)   
 [Clausola SELECT &#40; Transact-SQL &#41;](~/t-sql/queries/select-clause-transact-sql.md)  
  
  




