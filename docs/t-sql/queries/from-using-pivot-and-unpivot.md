---
title: Utilizzo di PIVOT e UNPIVOT | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PIVOT_TSQL
helpviewer_keywords:
- FROM clause, UNPIVOT operator
- unpivoting tables
- table pivoting [SQL Server]
- UNPIVOT operator
- crosstab query
- PIVOT operator
- rotating table-valued expressions
- pivoting tables
- FROM clause, PIVOT operator
- rotating columns
ms.assetid: 24ba54fc-98f7-4d35-8881-b5158aac1d66
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 413e4e89679358f0c53c82340dcae5640387ddcb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="from---using-pivot-and-unpivot"></a>DA - tramite PIVOT e UNPIVOT
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  È possibile utilizzare il `PIVOT` e `UNPIVOT` operatori relazionali per modificare un'espressione con valori di tabella in un'altra tabella. `PIVOT`Ruota un'espressione con valori di tabella convertendo i valori univoci da una colonna nell'espressione in più colonne nell'output ed esegue aggregazioni dove sono necessarie sui valori di colonna restanti da includere nell'output finale. `UNPIVOT`esegue l'operazione contraria rispetto a PIVOT ruotando le colonne di un'espressione con valori di tabella in valori di colonna.  
  
 La sintassi per `PIVOT` fornisce è più semplice e più leggibile di quella che potrebbe essere altrimenti specificata in una serie complessa di `SELECT...CASE` istruzioni. Per una descrizione completa della sintassi per `PIVOT`, vedere [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
 La sintassi seguente viene riepilogato come utilizzare il `PIVOT` operatore.  
  
```  
SELECT <non-pivoted column>,  
    [first pivoted column] AS <column name>,  
    [second pivoted column] AS <column name>,  
    ...  
    [last pivoted column] AS <column name>  
FROM  
    (<SELECT query that produces the data>)   
    AS <alias for the source query>  
PIVOT  
(  
    <aggregation function>(<column being aggregated>)  
FOR   
[<column that contains the values that will become column headers>]   
    IN ( [first pivoted column], [second pivoted column],  
    ... [last pivoted column])  
) AS <alias for the pivot table>  
<optional ORDER BY clause>;  
```  

## <a name="remarks"></a>Osservazioni  
Gli identificatori di colonna nel `UNPIVOT` clausola seguire le regole di confronto del catalogo. Per [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], le regole di confronto è sempre `SQL_Latin1_General_CP1_CI_AS`. Per [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] database parzialmente indipendenti, le regole di confronto è sempre `Latin1_General_100_CI_AS_KS_WS_SC`. Se la colonna viene combinata con altre colonne, quindi una clausola collate (`COLLATE DATABASE_DEFAULT`) è necessario per evitare conflitti.  

  
## <a name="basic-pivot-example"></a>Esempio di PIVOT di base  
 Nell'esempio di codice seguente viene generata una tabella a due colonne che include quattro righe.  
  
```  
USE AdventureWorks2014 ;  
GO  
SELECT DaysToManufacture, AVG(StandardCost) AS AverageCost   
FROM Production.Product  
GROUP BY DaysToManufacture;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 DaysToManufacture AverageCost
 ----------------- -----------
 0                 5.0885
 1                 223.88
 2                 359.1082
 4                 949.4105
 ```
  
 Nessun prodotto viene definito con tre `DaysToManufacture`.  
  
 Il codice seguente consente di visualizzare lo stesso risultato, trasformato tramite Pivot in modo che i valori di `DaysToManufacture` diventino le intestazioni di colonna. Una colonna è disponibile per tre `[3]` giorni, anche se i risultati sono `NULL`.  
  
```  
-- Pivot table with one row and five columns  
SELECT 'AverageCost' AS Cost_Sorted_By_Production_Days,   
[0], [1], [2], [3], [4]  
FROM  
(SELECT DaysToManufacture, StandardCost   
    FROM Production.Product) AS SourceTable  
PIVOT  
(  
AVG(StandardCost)  
FOR DaysToManufacture IN ([0], [1], [2], [3], [4])  
) AS PivotTable;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
Cost_Sorted_By_Production_Days 0           1           2           3           4         
------------------------------ ----------- ----------- ----------- ----------- -----------
AverageCost                    5.0885      223.88      359.1082    NULL        949.4105
```
  
## <a name="complex-pivot-example"></a>Esempio di PIVOT complesso  
 Uno scenario comune in cui `PIVOT` può essere utile è il caso in cui si desidera generare report a tabulazione incrociata per creare un riepilogo dei dati. Si supponga, ad esempio, di voler eseguire una query sulla tabella `PurchaseOrderHeader` nel database di esempio `AdventureWorks2014` per determinare il numero di ordini di acquisto effettuati da dipendenti specifici. La query seguente fornisce questo report, ordinato per fornitore.  
  
```  
USE AdventureWorks2014;  
GO  
SELECT VendorID, [250] AS Emp1, [251] AS Emp2, [256] AS Emp3, [257] AS Emp4, [260] AS Emp5  
FROM   
(SELECT PurchaseOrderID, EmployeeID, VendorID  
FROM Purchasing.PurchaseOrderHeader) p  
PIVOT  
(  
COUNT (PurchaseOrderID)  
FOR EmployeeID IN  
( [250], [251], [256], [257], [260] )  
) AS pvt  
ORDER BY pvt.VendorID;  
```  
  
 Set di risultati parziale:  
  
```
VendorID    Emp1        Emp2        Emp3        Emp4        Emp5  
----------- ----------- ----------- ----------- ----------- -----------
1492        2           5           4           4           4
1494        2           5           4           5           4
1496        2           4           4           5           5
1498        2           5           4           4           4
1500        3           4           4           5           4
```
  
 I risultati restituiti dall'istruzione di selezione secondaria vengono trasformati tramite Pivot nella colonna `EmployeeID`.  
  
```  
SELECT PurchaseOrderID, EmployeeID, VendorID  
FROM PurchaseOrderHeader;  
```  
  
 In questo modo, i valori univoci restituiti dalla colonna `EmployeeID` diventano campi nel set di risultati finale. Pertanto è presente una colonna per ogni numero `EmployeeID` specificato nella clausola Pivot. In questo caso i dipendenti `164`, `198`, `223`, `231` e `233`. La colonna `PurchaseOrderID` funge da colonna dei valori, rispetto alla quale vengono raggruppate le colonne restituite nell'output finale, dette colonne di raggruppamento. In questo caso, le colonne di raggruppamento vengono aggregate dalla funzione `COUNT`. Si noti che viene visualizzato un messaggio di avviso che indica che eventuali valori Null visualizzati nella colonna `PurchaseOrderID` non sono considerati nel calcolo del `COUNT` per ogni dipendente.  
  
> [!IMPORTANT]  
>  Quando le funzioni di aggregazione vengono utilizzate con `PIVOT`, la presenza di eventuali valori null nella colonna del valore non sono considerati durante l'elaborazione di un'aggregazione.  
  
 `UNPIVOT`esegue quasi l'operazione inversa di `PIVOT`, ruotando le colonne in righe. Si supponga che la tabella generata nell'esempio precedente venga archiviata nel database come `pvt` e che si desideri ruotare gli identificatori di colonna `Emp1`, `Emp2`, `Emp3`, `Emp4` e `Emp5` in valori di riga corrispondenti a un particolare fornitore. Ciò significa che è necessario identificare altre due colonne. La colonna che includerà i valori di colonna da ruotare (`Emp1`, `Emp2`,...) sarà denominata `Employee` e la colonna che includerà i valori che attualmente si trovano nelle colonne da ruotare sarà denominata `Orders`. Tali colonne corrispondono per la *pivot_column* e *value_column*, rispettivamente, nel [!INCLUDE[tsql](../../includes/tsql-md.md)] definizione. La query è la seguente.  
  
```  
-- Create the table and insert values as portrayed in the previous example.  
CREATE TABLE pvt (VendorID int, Emp1 int, Emp2 int,  
    Emp3 int, Emp4 int, Emp5 int);  
GO  
INSERT INTO pvt VALUES (1,4,3,5,4,4);  
INSERT INTO pvt VALUES (2,4,1,5,5,5);  
INSERT INTO pvt VALUES (3,4,3,5,4,4);  
INSERT INTO pvt VALUES (4,4,2,5,5,4);  
INSERT INTO pvt VALUES (5,5,1,5,5,5);  
GO  
-- Unpivot the table.  
SELECT VendorID, Employee, Orders  
FROM   
   (SELECT VendorID, Emp1, Emp2, Emp3, Emp4, Emp5  
   FROM pvt) p  
UNPIVOT  
   (Orders FOR Employee IN   
      (Emp1, Emp2, Emp3, Emp4, Emp5)  
)AS unpvt;  
GO  
```  
  
 Set di risultati parziale:  
  
```
VendorID    Employee    Orders
----------- ----------- ------
1            Emp1       4
1            Emp2       3 
1            Emp3       5
1            Emp4       4
1            Emp5       4
2            Emp1       4
2            Emp2       1
2            Emp3       5
2            Emp4       5
2            Emp5       5
...
```
  
 Si noti che `UNPIVOT` non è l'esatto opposto di `PIVOT`. `PIVOT`esegue un'aggregazione e, pertanto, unisce più righe possibili in una sola riga nell'output. `UNPIVOT`non si verifica il risultato dell'espressione con valori di tabella originale perché le righe sono state unite. Inoltre, i valori nell'input di null `UNPIVOT` scompaiono nell'output, mentre si è verificato i valori null originali nell'input prima di `PIVOT` operazione.  
  
 Il `Sales.vSalesPersonSalesByFiscalYears` visualizzare il [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] Usa database di esempio `PIVOT` per restituire le vendite totali per ogni venditore, per ogni anno fiscale. Per creare script di visualizzazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in **Esplora oggetti**, individuare la vista sotto il **viste** cartella per il [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database. Il nome della visualizzazione e quindi scegliere **visualizzazione Script come**.  
  
## <a name="see-also"></a>Vedere anche  
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)   
 [CASE (Transact-SQL)](../../t-sql/language-elements/case-transact-sql.md)  
  
  

