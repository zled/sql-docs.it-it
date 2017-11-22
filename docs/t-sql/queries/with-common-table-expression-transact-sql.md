---
title: CON common_table_expression (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
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
- WITH common_table_expression
- WITH_TSQL
- WITH
- common table expression
dev_langs: TSQL
helpviewer_keywords:
- WITH common_table_expression clause
- CTEs
- hierarchical queries [SQL Server], WITH common_table_expression
- recursive CTEs [SQL Server]
- recursive queries [SQL Server]
- common table expressions
- MAXRECURSION hint
- clauses [SQL Server], WITH common_table_expression
ms.assetid: 27cfb819-3e8d-4274-8bbe-cbbe4d9c2e23
caps.latest.revision: "60"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: a45cb91754fdff2aaafb90d33b7d89a70702dfb2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="with-commontableexpression-transact-sql"></a>WITH common_table_expression (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Indica un set di risultati denominato temporaneo, noto come espressione di tabella comune (CTE). L'espressione di tabella comune è derivata da una query semplice e definita all'interno dell'ambito di esecuzione di un'istruzione SELECT, INSERT, UPDATE o DELETE. Questa clausola può anche essere utilizzata in un'istruzione CREATE VIEW come parte dell'istruzione di definizione SELECT. Un'espressione di tabella comune può includere riferimenti a se stessa. In questo caso viene indicata con il nome di espressione di tabella comune ricorsiva.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ WITH <common_table_expression> [ ,...n ] ]  
  
<common_table_expression>::=  
    expression_name [ ( column_name [ ,...n ] ) ]  
    AS  
    ( CTE_query_definition )  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression_name*  
È un identificatore valido per l'espressione di tabella comune. *expression_name* deve essere diverso dal nome di qualsiasi altra espressione di tabella comune definito in WITH stesso \<common_table_expression > clausola, ma *expression_name* può essere lo stesso nome di un vista o tabella di base. Qualsiasi riferimento *expression_name* nella query viene utilizzata l'espressione di tabella comune e non l'oggetto di base.
  
 *column_name*  
 Specifica un nome di colonna nell'espressione di tabella comune. Non sono consentiti nomi duplicati all'interno di una singola definizione CTE. Il numero di nomi di colonna specificato deve corrispondere al numero di colonne nel set di risultati del *elementi CTE_query_definition*. L'elenco dei nomi di colonna è facoltativo solo se i nomi distinti di tutte le colonne risultanti sono specificati nella definizione della query.  
  
 *Elementi CTE_query_definition*  
 Specifica un'istruzione SELECT il cui set di risultati popola l'espressione di tabella comune. L'istruzione SELECT per *elementi CTE_query_definition* deve soddisfare i requisiti necessari per creare una vista, ad eccezione del fatto una CTE non è possibile definire un'altra CTE stessi. Per ulteriori informazioni, vedere la sezione Osservazioni e [CREATE VIEW &#40; Transact-SQL &#41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 Se più oggetti *elementi CTE_query_definition* è definito, le definizioni di query devono essere aggiunti da uno di questi operatori sui set: UNION ALL, UNION, EXCEPT o INTERSECT.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="guidelines-for-creating-and-using-common-table-expressions"></a>Linee guida per la creazione e l'utilizzo delle espressioni di tabella comuni  
 Le linee guida seguenti sono valide per le espressioni di tabella comuni non ricorsive. Per le linee guida relative alle espressioni di tabella comuni ricorsive, vedere "Linee guida per la definizione e l'utilizzo delle espressioni di tabella comuni ricorsive" più avanti.  
  
-   Una CTE deve essere seguita da un'istruzione SELECT, INSERT, UPDATE o DELETE che faccia riferimento ad alcune o a tutte le colonne CTE. Un'espressione CTE può anche essere specificata in un'istruzione CREATE VIEW come parte dell'istruzione di definizione SELECT della vista.  
  
-   In una CTE non ricorsiva è possibile definire più query CTE. Le definizioni devono essere combinate da uno di questi operatori sui set: UNION ALL, UNION, INTERSECT o EXCEPT.  
  
-   Una CTE può far riferimento a se stessa e alle CTE definite in precedenza nella stessa clausola WITH. Il riferimento in avanti non è consentito.  
  
-   Non è consentito specificare più di una clausola WITH in una CTE. Ad esempio, se un *elementi CTE_query_definition* contiene una sottoquery, tale sottoquery non può contenere un annidati con clausola che definisce un'altra CTE.  
  
-   Le clausole seguenti non possono essere utilizzate nel *elementi CTE_query_definition*:  
  
    -   ORDER BY (tranne quando si specifica una clausola TOP)  
  
    -   INTO  
  
    -   Clausola OPTION con hint per la query  
  
    -   FOR BROWSE  
  
-   Quando un'espressione CTE viene utilizzata in un'istruzione che fa parte di un batch, l'istruzione precedente deve essere seguita da un punto e virgola.  
  
-   Una query che fa riferimento a un'espressione CTE può essere utilizzata per definire un cursore.  
  
-   L'espressione CTE può fare riferimento alle tabelle nei server remoti.  
  
-   Durante l'esecuzione di una CTE, tutti gli hint che fanno riferimento a una CTE possono entrare in conflitto con altri hint individuati quando la CTE accede alle tabelle sottostanti, allo stesso modo degli hint che fanno riferimento alle viste nelle query. In questo caso, la query restituisce un errore.  
  
## <a name="guidelines-for-defining-and-using-recursive-common-table-expressions"></a>Linee guida per la definizione e l'utilizzo delle espressioni di tabella comuni ricorsive  
 Le linee guida seguenti sono valide per la definizione delle espressioni di tabella comuni ricorsive.  
  
-   La definizione CTE ricorsiva deve contenere almeno due definizioni di query CTE, un membro non ricorsivo e un membro ricorsivo. È possibile definire più membri ricorsivi e non ricorsivi, ma tutte le definizioni delle query dei membri non ricorsivi devono precedere la definizione del primo membro ricorsivo. Tutte le definizioni delle query CTE sono membri non ricorsivi tranne nei casi un cui fanno riferimento all'espressione CTE stessa.  
  
-   I membri non ricorsivi devono essere combinati da uno degli operatori sui set seguenti: UNION ALL, UNION, INTERSECT o EXCEPT. UNION ALL è l'unico operatore sui set consentito tra l'ultimo membro non ricorsivo e il primo membro ricorsivo, nonché durante la combinazione di più membri ricorsivi.  
  
-   Il numero delle colonne nei membri ricorsivi e non ricorsivi deve essere lo stesso.  
  
-   Il tipo di dati di una colonna nel membro ricorsivo deve essere lo stesso del tipo di dati della colonna corrispondente nel membro non ricorsivo.  
  
-   La clausola FROM di un membro ricorsivo deve fare riferimento solo una volta alla CTE *expression_name*.  
  
-   Gli elementi seguenti non sono consentiti nel *elementi CTE_query_definition* di un membro ricorsivo:  
  
    -   SELECT DISTINCT  
  
    -   GROUP BY  
  
    -   PIVOT (quando il livello di compatibilità del database è impostato su 110 o oltre. Vedere [modifiche di rilievo apportate alle funzionalità del motore di Database in SQL Server 2016](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).)  
  
    -   HAVING  
  
    -   Aggregazione scalare  
  
    -   Torna all'inizio  
  
    -   LEFT, RIGHT, OUTER JOIN (INNER JOIN è consentito)  
  
    -   Sottoquery:  
  
    -   Hint applicato a un riferimento ricorsivo a un'espressione CTE all'interno di un *elementi CTE_query_definition*.  
  
 Le linee guida seguenti sono valide per l'utilizzo delle espressioni di tabella comuni ricorsive.  
  
-   Tutte le colonne restituite dalla CTE ricorsiva ammettono valori Null a prescindere dal supporto dei valori Null delle colonne restituite dalle istruzioni SELECT coinvolte.  
  
-   Una CTE ricorsiva formulata in modo non corretto può provocare un ciclo infinito. Ad esempio, se la definizione della query del membro ricorsivo restituisce gli stessi valori per entrambe le colonne padre e figlio, si crea un ciclo infinito. Per evitare un ciclo infinito, è possibile limitare il numero di livelli di ricorsione consentito per una particolare espressione utilizzando l'hint MAXRECURSION e un valore compreso tra 0 e 32.767 nella clausola OPTION dell'istruzione INSERT, UPDATE, DELETE o SELECT. Ciò consente di controllare l'esecuzione dell'istruzione fino a quando non viene risolto il problema relativo al codice che sta creando il ciclo. Il valore predefinito per l'intero server è 100. Se è specificato 0, non viene applicato alcun limite. È possibile specificare solo un valore MAXRECURSION per istruzione. Per altre informazioni, vedere [Hint per la query &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
-   Non è possibile utilizzare una vista che contiene un'espressione di tabella comune ricorsiva per aggiornare i dati.  
  
-   I cursori possono essere definiti sulle query tramite CTE. Questa è la *select_statement* argomento che definisce il set di risultati del cursore. Sono consentiti solo i cursori fast forward only e statici (snapshot) per le CTE ricorsive. Se viene specificato un altro tipo di cursore in una CTE ricorsiva, il tipo di cursore viene convertito in statico.  
  
-   Nelle CTE è possibile far riferimento alle tabelle nei server remoti. Se nel membro ricorsivo della CTE si fa riferimento al server remoto, viene creato uno spool per ogni tabella remota in maniera che si possa accedere alle tabelle in modo locale ripetutamente. Se la query è di tipo CTE, Index Spool o Lazy Spool viene visualizzato nel piano di query con il predicato aggiuntivo WITH STACK associato. Questo è uno dei modi utilizzati per confermare una ricorsione appropriata.  
  
-   Le funzioni analitiche e di aggregazione nella parte ricorsiva dell'espressione CTE vengono applicate al set per il livello di ricorsione corrente, non al set per l'espressione CTE. Le funzioni come ROW_NUMBER funzionano solo nel subset di dati passato dal livello di ricorsione corrente e non nell'intero set di dati passato alla parte ricorsiva dell'espressione CTE. Per ulteriori informazioni, vedere l'esempio K. utilizzo di funzioni analitiche in un'espressione CTE ricorsiva seguente.  
  
## <a name="features-and-limitations-of-common-table-expressions-in-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Funzionalità e limitazioni di una comune tabella espressioni in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'implementazione corrente di una CTE in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] sono le seguenti limitazioni:  
  
-   Una CTE può essere specificata in un **selezionare** istruzione.  
  
-   Una CTE può essere specificata in un **CREATE VIEW** istruzione.  
  
-   Una CTE può essere specificata in un **CREATE TABLE AS SELECT** istruzione (un'istruzione CTAS).  
  
-   Una CTE può essere specificata in un **CREATE REMOTE TABLE AS SELECT** istruzione (CRTAS).  
  
-   Una CTE può essere specificata in un **CREATE EXTERNAL TABLE AS SELECT** istruzione (CETAS).  
  
-   Una tabella remota può fare riferimento da un'espressione CTE.  
  
-   Una tabella esterna può fare riferimento da un'espressione CTE.  
  
-   È possibile definire più definizioni di query CTE in una CTE.  
  
-   Una CTE deve essere seguita da un singolo **selezionare** istruzione. **Inserisci**, **aggiornamento**, **eliminare**, e **MERGE** istruzioni non sono supportate.  
  
-   Un'espressione di tabella comune che include riferimenti a se stessa (ricorsiva espressione di tabella comune) non è supportata.  
  
-   Specificare più di una **WITH** clausola in una CTE non è consentita. Ad esempio, se un elementi CTE_query_definition contiene una sottoquery, tale sottoquery non può contenere un tipo annidato **WITH** clausola che definisce un'altra CTE.  
  
-   Un **ORDER BY** Impossibile utilizzare la clausola in elementi di CTE_query_definition, tranne quando una **TOP** è specificata alcuna clausola.  
  
-   Quando un'espressione CTE viene utilizzata in un'istruzione che fa parte di un batch, l'istruzione precedente deve essere seguita da un punto e virgola.  
  
-   Se utilizzata in istruzioni preparate da **sp_prepare**, CTE verranno si comportano allo stesso modo di altri **selezionare** istruzioni in PDW. Tuttavia, se le CTE vengono utilizzate come parte di CETAS preparato da **sp_prepare**, il comportamento può differire da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e altre istruzioni PDW a causa di associazione viene implementato per **sp_prepare**. Se **selezionare** riferimenti CTE è utilizzata una colonna di tipo non corretta che non esiste nella CTE, la **sp_prepare** passerà senza rilevare l'errore, ma l'errore verrà generata durante **sp_execute**  invece.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-simple-common-table-expression"></a>A. Creazione di un'espressione di tabella comune semplice  
 Nell'esempio seguente viene illustrato il numero totale di ordini di vendita all'anno per tutti i venditori di [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].  
  
```  
  
-- Define the CTE expression name and column list.  
WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
AS  
-- Define the CTE query.  
(  
    SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
)  
-- Define the outer query referencing the CTE name.  
SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
FROM Sales_CTE  
GROUP BY SalesYear, SalesPersonID  
ORDER BY SalesPersonID, SalesYear;  
GO  
  
```  
  
### <a name="b-using-a-common-table-expression-to-limit-counts-and-report-averages"></a>B. Utilizzo di un'espressione di tabella comune per limitare il numero medio di ordini  
 Nell'esempio seguente viene illustrato il numero medio di ordini di vendita all'anno per i venditori.  
  
```  
WITH Sales_CTE (SalesPersonID, NumberOfOrders)  
AS  
(  
    SELECT SalesPersonID, COUNT(*)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
    GROUP BY SalesPersonID  
)  
SELECT AVG(NumberOfOrders) AS "Average Sales Per Person"  
FROM Sales_CTE;  
GO  
```  
  
### <a name="c-using-multiple-cte-definitions-in-a-single-query"></a>C. Utilizzo di più definizioni CTE in una singola query  
 Nell'esempio seguente viene illustrato come definire più di una CTE in una singola query. Si noti che per separare le definizioni di query CTE è utilizzata una virgola. La funzione FORMAT, utilizzata per visualizzare gli importi monetari in un formato di valuta, è disponibile in SQL Server 2012 e versioni successive.  
  
```  
  
WITH Sales_CTE (SalesPersonID, TotalSales, SalesYear)  
AS  
-- Define the first CTE query.  
(  
    SELECT SalesPersonID, SUM(TotalDue) AS TotalSales, YEAR(OrderDate) AS SalesYear  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
       GROUP BY SalesPersonID, YEAR(OrderDate)  
  
)  
,   -- Use a comma to separate multiple CTE definitions.  
  
-- Define the second CTE query, which returns sales quota data by year for each sales person.  
Sales_Quota_CTE (BusinessEntityID, SalesQuota, SalesQuotaYear)  
AS  
(  
       SELECT BusinessEntityID, SUM(SalesQuota)AS SalesQuota, YEAR(QuotaDate) AS SalesQuotaYear  
       FROM Sales.SalesPersonQuotaHistory  
       GROUP BY BusinessEntityID, YEAR(QuotaDate)  
)  
  
-- Define the outer query by referencing columns from both CTEs.  
SELECT SalesPersonID  
  , SalesYear  
  , FORMAT(TotalSales,'C','en-us') AS TotalSales  
  , SalesQuotaYear  
  , FORMAT (SalesQuota,'C','en-us') AS SalesQuota  
  , FORMAT (TotalSales -SalesQuota, 'C','en-us') AS Amt_Above_or_Below_Quota  
FROM Sales_CTE  
JOIN Sales_Quota_CTE ON Sales_Quota_CTE.BusinessEntityID = Sales_CTE.SalesPersonID  
                    AND Sales_CTE.SalesYear = Sales_Quota_CTE.SalesQuotaYear  
ORDER BY SalesPersonID, SalesYear;  
GO  
  
```  
  
 Set di risultati parziale:  
  
```  
  
SalesPersonID SalesYear   TotalSales    SalesQuotaYear SalesQuota  Amt_Above_or_Below_Quota  
------------- ---------   -----------   -------------- ---------- ----------------------------------   
  
274           2005        $32,567.92    2005           $35,000.00  ($2,432.08)  
274           2006        $406,620.07   2006           $455,000.00 ($48,379.93)  
274           2007        $515,622.91   2007           $544,000.00 ($28,377.09)  
274           2008        $281,123.55   2008           $271,000.00  $10,123.55  
  
```  
  
### <a name="d-using-a-recursive-common-table-expression-to-display-multiple-levels-of-recursion"></a>D. Utilizzo di un'espressione di tabella comune ricorsiva per visualizzare più livelli di ricorsione  
 Nell'esempio seguente viene illustrato l'elenco gerarchico dei responsabili e dei dipendenti a loro subordinati. L'esempio inizia con la creazione e il popolamento della tabella `dbo.MyEmployees`.  
  
```  
-- Create an Employee table.  
CREATE TABLE dbo.MyEmployees  
(  
EmployeeID smallint NOT NULL,  
FirstName nvarchar(30)  NOT NULL,  
LastName  nvarchar(40) NOT NULL,  
Title nvarchar(50) NOT NULL,  
DeptID smallint NOT NULL,  
ManagerID int NULL,  
 CONSTRAINT PK_EmployeeID PRIMARY KEY CLUSTERED (EmployeeID ASC)   
);  
-- Populate the table with values.  
INSERT INTO dbo.MyEmployees VALUES   
 (1, N'Ken', N'Sánchez', N'Chief Executive Officer',16,NULL)  
,(273, N'Brian', N'Welcker', N'Vice President of Sales',3,1)  
,(274, N'Stephen', N'Jiang', N'North American Sales Manager',3,273)  
,(275, N'Michael', N'Blythe', N'Sales Representative',3,274)  
,(276, N'Linda', N'Mitchell', N'Sales Representative',3,274)  
,(285, N'Syed', N'Abbas', N'Pacific Sales Manager',3,273)  
,(286, N'Lynn', N'Tsoflias', N'Sales Representative',3,285)  
,(16,  N'David',N'Bradley', N'Marketing Manager', 4, 273)  
,(23,  N'Mary', N'Gibson', N'Marketing Specialist', 4, 16);  
```  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(ManagerID, EmployeeID, Title, EmployeeLevel) AS   
(  
    SELECT ManagerID, EmployeeID, Title, 0 AS EmployeeLevel  
    FROM dbo.MyEmployees   
    WHERE ManagerID IS NULL  
    UNION ALL  
    SELECT e.ManagerID, e.EmployeeID, e.Title, EmployeeLevel + 1  
    FROM dbo.MyEmployees AS e  
        INNER JOIN DirectReports AS d  
        ON e.ManagerID = d.EmployeeID   
)  
SELECT ManagerID, EmployeeID, Title, EmployeeLevel   
FROM DirectReports  
ORDER BY ManagerID;  
GO  
```  
  
### <a name="e-using-a-recursive-common-table-expression-to-display-two-levels-of-recursion"></a>E. Utilizzo di un'espressione di tabella comune ricorsiva per visualizzare due livelli di ricorsione  
 Nell'esempio seguente vengono illustrati i responsabili e i dipendenti che sono loro subordinati. Il numero di livelli restituiti è limitato a due.  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(ManagerID, EmployeeID, Title, EmployeeLevel) AS   
(  
    SELECT ManagerID, EmployeeID, Title, 0 AS EmployeeLevel  
    FROM dbo.MyEmployees   
    WHERE ManagerID IS NULL  
    UNION ALL  
    SELECT e.ManagerID, e.EmployeeID, e.Title, EmployeeLevel + 1  
    FROM dbo.MyEmployees AS e  
        INNER JOIN DirectReports AS d  
        ON e.ManagerID = d.EmployeeID   
)  
SELECT ManagerID, EmployeeID, Title, EmployeeLevel   
FROM DirectReports  
WHERE EmployeeLevel <= 2 ;  
GO  
  
```  
  
### <a name="f-using-a-recursive-common-table-expression-to-display-a-hierarchical-list"></a>F. Utilizzo di un'espressione di tabella comune ricorsiva per visualizzare un elenco gerarchico  
 Nell'esempio seguente viene utilizzato come base l'esempio D aggiungendo i nomi del responsabile e dei dipendenti e i loro rispettivi titoli. La gerarchia dei responsabili e dei dipendenti viene inoltre evidenziata rientrando ogni livello.  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(Name, Title, EmployeeID, EmployeeLevel, Sort)  
AS (SELECT CONVERT(varchar(255), e.FirstName + ' ' + e.LastName),  
        e.Title,  
        e.EmployeeID,  
        1,  
        CONVERT(varchar(255), e.FirstName + ' ' + e.LastName)  
    FROM dbo.MyEmployees AS e  
    WHERE e.ManagerID IS NULL  
    UNION ALL  
    SELECT CONVERT(varchar(255), REPLICATE ('|    ' , EmployeeLevel) +  
        e.FirstName + ' ' + e.LastName),  
        e.Title,  
        e.EmployeeID,  
        EmployeeLevel + 1,  
        CONVERT (varchar(255), RTRIM(Sort) + '|    ' + FirstName + ' ' +   
                 LastName)  
    FROM dbo.MyEmployees AS e  
    JOIN DirectReports AS d ON e.ManagerID = d.EmployeeID  
    )  
SELECT EmployeeID, Name, Title, EmployeeLevel  
FROM DirectReports   
ORDER BY Sort;  
GO  
```  
  
### <a name="g-using-maxrecursion-to-cancel-a-statement"></a>G. Utilizzo di MAXRECURSION per annullare un'istruzione  
 È possibile utilizzare `MAXRECURSION` per impedire che una CTE ricorsiva non corretta provochi un ciclo infinito. Nell'esempio seguente viene creato intenzionalmente un ciclo infinito e viene utilizzato l'hint `MAXRECURSION` per limitare a due il numero di livelli di ricorsione.  
  
```  
USE AdventureWorks2012;  
GO  
--Creates an infinite loop  
WITH cte (EmployeeID, ManagerID, Title) as  
(  
    SELECT EmployeeID, ManagerID, Title  
    FROM dbo.MyEmployees  
    WHERE ManagerID IS NOT NULL  
  UNION ALL  
    SELECT cte.EmployeeID, cte.ManagerID, cte.Title  
    FROM cte   
    JOIN  dbo.MyEmployees AS e   
        ON cte.ManagerID = e.EmployeeID  
)  
--Uses MAXRECURSION to limit the recursive levels to 2  
SELECT EmployeeID, ManagerID, Title  
FROM cte  
OPTION (MAXRECURSION 2);  
GO  
```  
  
 Dopo la correzione dell'errore del codice, MAXRECURSION non è più necessario. Nell'esempio seguente viene illustrato il codice corretto.  
  
```  
USE AdventureWorks2012;  
GO  
WITH cte (EmployeeID, ManagerID, Title)  
AS  
(  
    SELECT EmployeeID, ManagerID, Title  
    FROM dbo.MyEmployees  
    WHERE ManagerID IS NOT NULL  
  UNION ALL  
    SELECT  e.EmployeeID, e.ManagerID, e.Title  
    FROM dbo.MyEmployees AS e  
    JOIN cte ON e.ManagerID = cte.EmployeeID  
)  
SELECT EmployeeID, ManagerID, Title  
FROM cte;  
GO  
```  
  
### <a name="h-using-a-common-table-expression-to-selectively-step-through-a-recursive-relationship-in-a-select-statement"></a>H. Utilizzo di un'espressione di tabella comune per analizzare in maniera selettiva una relazione ricorsiva in un'istruzione SELECT  
 Nell'esempio seguente viene illustrata la gerarchia di assembly e componenti del prodotto che sono necessari per costruire la bicicletta per `ProductAssemblyID = 800`.  
  
```  
USE AdventureWorks2012;  
GO  
WITH Parts(AssemblyID, ComponentID, PerAssemblyQty, EndDate, ComponentLevel) AS  
(  
    SELECT b.ProductAssemblyID, b.ComponentID, b.PerAssemblyQty,  
        b.EndDate, 0 AS ComponentLevel  
    FROM Production.BillOfMaterials AS b  
    WHERE b.ProductAssemblyID = 800  
          AND b.EndDate IS NULL  
    UNION ALL  
    SELECT bom.ProductAssemblyID, bom.ComponentID, p.PerAssemblyQty,  
        bom.EndDate, ComponentLevel + 1  
    FROM Production.BillOfMaterials AS bom   
        INNER JOIN Parts AS p  
        ON bom.ProductAssemblyID = p.ComponentID  
        AND bom.EndDate IS NULL  
)  
SELECT AssemblyID, ComponentID, Name, PerAssemblyQty, EndDate,  
        ComponentLevel   
FROM Parts AS p  
    INNER JOIN Production.Product AS pr  
    ON p.ComponentID = pr.ProductID  
ORDER BY ComponentLevel, AssemblyID, ComponentID;  
GO  
```  
  
### <a name="i-using-a-recursive-cte-in-an-update-statement"></a>I. Utilizzo di una CTE ricorsiva in un'istruzione UPDATE  
 Nell'esempio seguente viene aggiornato il `PerAssemblyQty` valore per tutte le parti che vengono utilizzati per generare il prodotto 'Road-550-W Yellow, 44' `(ProductAssemblyID``800`). L'espressione di tabella comune restituisce un elenco gerarchico di parti utilizzate per compilare `ProductAssemblyID 800`, i componenti utilizzati per creare tali parti e così via. Vengono modificate solo le righe restituite dall'espressione di tabella comune.  
  
```  
USE AdventureWorks2012;  
GO  
WITH Parts(AssemblyID, ComponentID, PerAssemblyQty, EndDate, ComponentLevel) AS  
(  
    SELECT b.ProductAssemblyID, b.ComponentID, b.PerAssemblyQty,  
        b.EndDate, 0 AS ComponentLevel  
    FROM Production.BillOfMaterials AS b  
    WHERE b.ProductAssemblyID = 800  
          AND b.EndDate IS NULL  
    UNION ALL  
    SELECT bom.ProductAssemblyID, bom.ComponentID, p.PerAssemblyQty,  
        bom.EndDate, ComponentLevel + 1  
    FROM Production.BillOfMaterials AS bom   
        INNER JOIN Parts AS p  
        ON bom.ProductAssemblyID = p.ComponentID  
        AND bom.EndDate IS NULL  
)  
UPDATE Production.BillOfMaterials  
SET PerAssemblyQty = c.PerAssemblyQty * 2  
FROM Production.BillOfMaterials AS c  
JOIN Parts AS d ON c.ProductAssemblyID = d.AssemblyID  
WHERE d.ComponentLevel = 0;  
```  
  
### <a name="j-using-multiple-anchor-and-recursive-members"></a>J. Utilizzo di più membri ricorsivi e non ricorsivi  
 Nell'esempio seguente vengono utilizzati più membri ricorsivi e non ricorsivi per restituire tutti gli antenati di una specifica persona. Viene creata una tabella e vengono inseriti i valori per stabilire l'albero genealogico restituito dalla CTE ricorsiva.  
  
```  
-- Genealogy table  
IF OBJECT_ID('dbo.Person','U') IS NOT NULL DROP TABLE dbo.Person;  
GO  
CREATE TABLE dbo.Person(ID int, Name varchar(30), Mother int, Father int);  
GO  
INSERT dbo.Person   
VALUES(1, 'Sue', NULL, NULL)  
      ,(2, 'Ed', NULL, NULL)  
      ,(3, 'Emma', 1, 2)  
      ,(4, 'Jack', 1, 2)  
      ,(5, 'Jane', NULL, NULL)  
      ,(6, 'Bonnie', 5, 4)  
      ,(7, 'Bill', 5, 4);  
GO  
-- Create the recursive CTE to find all of Bonnie's ancestors.  
WITH Generation (ID) AS  
(  
-- First anchor member returns Bonnie's mother.  
    SELECT Mother   
    FROM dbo.Person  
    WHERE Name = 'Bonnie'  
UNION  
-- Second anchor member returns Bonnie's father.  
    SELECT Father   
    FROM dbo.Person  
    WHERE Name = 'Bonnie'  
UNION ALL  
-- First recursive member returns male ancestors of the previous generation.  
    SELECT Person.Father  
    FROM Generation, Person  
    WHERE Generation.ID=Person.ID  
UNION ALL  
-- Second recursive member returns female ancestors of the previous generation.  
    SELECT Person.Mother  
    FROM Generation, dbo.Person  
    WHERE Generation.ID=Person.ID  
)  
SELECT Person.ID, Person.Name, Person.Mother, Person.Father  
FROM Generation, dbo.Person  
WHERE Generation.ID = Person.ID;  
GO  
```  
  
###  <a name="bkmkUsingAnalyticalFunctionsInARecursiveCTE"></a>K. Utilizzo di funzioni analitiche in un'espressione CTE ricorsiva  
 Nell'esempio seguente viene illustrata una trappola in cui si può cadere quando si utilizza una funzione analitica o di aggregazione nella parte ricorsiva di un'espressione CTE.  
  
```  
DECLARE @t1 TABLE (itmID int, itmIDComp int);  
INSERT @t1 VALUES (1,10), (2,10);   
  
DECLARE @t2 TABLE (itmID int, itmIDComp int);   
INSERT @t2 VALUES (3,10), (4,10);   
  
WITH vw AS  
 (  
    SELECT itmIDComp, itmID  
    FROM @t1  
  
    UNION ALL  
  
    SELECT itmIDComp, itmID  
    FROM @t2  
)   
,r AS  
 (  
    SELECT t.itmID AS itmIDComp  
           , NULL AS itmID  
           ,CAST(0 AS bigint) AS N  
           ,1 AS Lvl  
    FROM (SELECT 1 UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4) AS t (itmID)   
  
UNION ALL  
  
SELECT t.itmIDComp  
    , t.itmID  
    , ROW_NUMBER() OVER(PARTITION BY t.itmIDComp ORDER BY t.itmIDComp, t.itmID) AS N  
    , Lvl + 1  
FROM r   
    JOIN vw AS t ON t.itmID = r.itmIDComp  
)   
  
SELECT Lvl, N FROM r;  
```  
  
 Di seguito vengono riportati i risultati previsti per la query.  
  
```  
Lvl  N  
1    0  
1    0  
1    0  
1    0  
2    4  
2    3  
2    2  
2    1  
```  
  
 Di seguito vengono riportati i risultati effettivi per la query.  
  
```  
Lvl  N  
1    0  
1    0  
1    0  
1    0  
2    1  
2    1  
2    1  
2    1  
```  
  
 `N` restituisce 1 per ogni sessione della parte ricorsiva dell'espressione CTE perché solo il subset di dati per tale livello di ricorsione viene passato a `ROWNUMBER`. Per ognuna delle iterazioni della parte ricorsiva della query, viene passata solo una riga a `ROWNUMBER`.  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="l-using-a-common-table-expression-within-a-ctas-statement"></a>L. Utilizzo di un'espressione di tabella comuni all'interno di un'istruzione di un'istruzione CTAS  
 L'esempio seguente crea una nuova tabella contenente il numero totale di ordini di vendita all'anno per ogni rappresentante di vendita in [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].  
  
```  
-- Uses AdventureWorks  
  
CREATE TABLE SalesOrdersPerYear  
WITH  
(  
    DISTRIBUTION = HASH(SalesPersonID)  
)  
AS  
    -- Define the CTE expression name and column list.  
    WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
    AS  
    -- Define the CTE query.  
    (  
        SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
        FROM Sales.SalesOrderHeader  
        WHERE SalesPersonID IS NOT NULL  
    )  
    -- Define the outer query referencing the CTE name.  
    SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
    FROM Sales_CTE  
    GROUP BY SalesYear, SalesPersonID  
    ORDER BY SalesPersonID, SalesYear;  
GO  
```  
  
### <a name="m-using-a-common-table-expression-within-a-cetas-statement"></a>M. Utilizzo di un'espressione di tabella comuni all'interno di un'istruzione CETAS  
 L'esempio seguente crea una nuova tabella esterna che contiene il numero totale di ordini di vendita all'anno per ogni rappresentante di vendita in [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].  
  
```  
-- Uses AdventureWorks  
  
CREATE EXTERNAL TABLE SalesOrdersPerYear  
WITH  
(  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:5000/files/Customer',  
    FORMAT_OPTIONS ( FIELD_TERMINATOR = '|' )   
)  
AS  
    -- Define the CTE expression name and column list.  
    WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
    AS  
    -- Define the CTE query.  
    (  
        SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
        FROM Sales.SalesOrderHeader  
        WHERE SalesPersonID IS NOT NULL  
    )  
    -- Define the outer query referencing the CTE name.  
    SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
    FROM Sales_CTE  
    GROUP BY SalesYear, SalesPersonID  
    ORDER BY SalesPersonID, SalesYear;  
GO  
```  
  
### <a name="n-using-multiple-comma-separated-ctes-in-a-statement"></a>N. Utilizzo di più valori delimitati da virgole separati CTE in un'istruzione  
 Nell'esempio seguente viene illustrato come inclusi due CTE in una singola istruzione. La CTE non possono essere annidato (nessuna ricorsione).  
  
```  
WITH   
 CountDate (TotalCount, TableName) AS  
    (  
     SELECT COUNT(datekey), 'DimDate' FROM DimDate  
    ) ,  
 CountCustomer (TotalAvg, TableName) AS  
    (  
     SELECT COUNT(CustomerKey), 'DimCustomer' FROM DimCustomer  
    )  
SELECT TableName, TotalCount FROM CountDate  
UNION ALL  
SELECT TableName, TotalAvg FROM CountCustomer;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Ad eccezione di e INTERSECT &#40; Transact-SQL &#41;](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  
