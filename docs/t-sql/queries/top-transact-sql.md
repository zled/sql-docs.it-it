---
title: TOP (Transact-SQL) | Documenti Microsoft
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
- TOP_TSQL
- TOP
dev_langs:
- TSQL
helpviewer_keywords:
- TOP clause
- first set of query result rows [SQL Server]
- TOP clause, about TOP clause
- queries [SQL Server], results
ms.assetid: da983c0a-06c5-4cf8-a6a4-7f9d66f34f2c
caps.latest.revision: 60
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9e360ecdae24cbe93b0ed75215819ad4bb9e6bff
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="top-transact-sql"></a>TOP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Limita le righe restituite nel set di risultati di una query a un numero specificato o a una percentuale di righe in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Se TOP viene utilizzato in combinazione con la clausola ORDER BY, il set di risultati è limitato al primo *N* numero di righe ordinate; in caso contrario, viene restituito il primo *N* numero di righe in un ordine non definito. Usare questa clausola per specificare il numero di righe restituite da un'istruzione SELECT o interessate da un'istruzione INSERT, UPDATE, MERGE o DELETE.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[   
    TOP (expression) [PERCENT]  
    [ WITH TIES ]  
]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
[   
    TOP ( expression )   
    [ WITH TIES ]  
]  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Espressione numerica che consente di specificare il numero di righe da restituire. *espressione* viene implicitamente convertito in un **float** valore se è specificato PERCENT; in caso contrario, viene convertito in **bigint**.  
  
 PERCENT  
 Indica che la query restituisce solo i primi *espressione* percento delle righe dal set di risultati. I valori frazionari vengono arrotondati al valore intero più vicino.  
  
 WITH TIES  
 Utilizzato quando si desidera restituire due o più righe che hanno un valore equivalente per l'ultima posizione nel set di risultati limitato. Deve essere utilizzato con il **ORDER BY** clausola. **WITH TIES** potrebbe essere più righe da restituire rispetto al valore specificato *espressione*. Ad esempio, se *espressione* è impostato su 5, ma 2 righe aggiuntive corrispondono ai valori del **ORDER BY** colonne nella riga 5, il set di risultati conterrà 7 righe.  
  
 È possibile specificare TOP...WITH TIES solo nelle istruzioni SELECT e solo se viene specificata una clausola ORDER BY. L'ordine restituito per l'associazione dei record è arbitrario. ORDER BY non riguarda questa regola.  
  
## <a name="best-practices"></a>Procedure consigliate  
 In un'istruzione SELECT utilizzare sempre una clausola ORDER BY con la clausola TOP. È l'unico modo per indicare prevedibilmente quali righe sono interessate dalla clausola TOP.  
  
 Utilizzare OFFSET e FETCH nella clausola ORDER BY anziché la clausola TOP per implementare una soluzione di paging delle query. Una soluzione di paging, ovvero l'invio di blocchi o "pagine" di dati al client, è di più facile implementazione con le clausole OFFSET e FETCH. Per altre informazioni, vedere [Clausola ORDER BY &#40;Transact-SQL&#41;](../../t-sql/queries/select-order-by-clause-transact-sql.md).  
  
 Utilizzare TOP (o OFFSET e FETCH) anziché SET ROWCOUNT per limitare il numero di righe restituite. Questi metodi vengono preferiti all'utilizzo di SET ROWCOUNT per i motivi seguenti:  
  
-   Come parte di un'istruzione SELECT, query optimizer può considerare il valore di *espressione* nelle clausole TOP o FETCH durante l'ottimizzazione della query. Poiché SET ROWCOUNT viene utilizzato al di fuori di un'istruzione che esegue una query, il relativo valore non può essere utilizzato in un piano di query.  
  
## <a name="compatibility-support"></a>Informazioni sulla compatibilità  
 Per garantire la compatibilità con le versioni precedenti, le parentesi sono facoltative nelle istruzioni SELECT. È consigliabile utilizzare sempre le parentesi per le clausole TOP nelle istruzioni SELECT per coerenza con le istruzioni INSERT, UPDATE, MERGE e DELETE in cui le parentesi sono obbligatorie.  
  
## <a name="interoperability"></a>Interoperabilità  
 L'espressione TOP non influisce sulle istruzioni eventualmente eseguite a causa dell'attivazione di un trigger. Il **inserito** e **eliminato** tabelle nei trigger restituirà solo le righe effettivamente interessate dalle istruzioni INSERT, UPDATE, MERGE o DELETE. Se ad esempio INSERT TRIGGER viene attivato come risultato di un'istruzione INSERT che ha utilizzato una clausola TOP,  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente l'aggiornamento delle righe attraverso le viste. Poiché la clausola TOP può essere inclusa nella definizione della vista, è possibile che alcune righe scompaiano dalla vista in seguito a un aggiornamento se le righe non soddisfano più i requisiti dell'espressione TOP.  
  
 Quando specificato nell'istruzione MERGE, la clausola TOP viene applicata *dopo* unione in join l'intera tabella di origine e l'intera tabella di destinazione e vengono rimosse le righe unite in join non qualificano per un'istruzione insert, update o azione di eliminazione. La clausola TOP riduce ulteriormente il numero di righe unite in join in base al valore specificato e l'azione di inserimento, aggiornamento o eliminazione viene applicata alle righe unite in join rimanenti in modo non ordinato. Ciò significa che le righe vengono distribuite tra le azioni definite nelle clausole WHEN senza alcun ordine. Si supponga ad esempio che l'utilizzo della clausola TOP (10) interessi 10 righe. Di queste righe, 7 possono essere aggiornate e 3 inserite oppure 1 riga può essere eliminata, 5 aggiornate e 4 inserite e così via. Poiché l'istruzione MERGE esegue un'analisi completa di entrambe le tabelle di origine e di destinazione, l'utilizzo della clausola TOP per modificare una tabella di grandi dimensioni creando più batch può influire sulle prestazioni di I/O. In questo scenario è importante assicurare che tutti i batch successivi vengano destinati a nuove righe.  
  
 Prestare attenzione quando si specifica la clausola TOP in una query che contiene un operatore UNION, UNION ALL, EXCEPT o INTERSECT. È possibile scrivere una query che restituisce risultati imprevisti perché l'ordine in cui le clausole TOP e ORDER BY vengono elaborate logicamente non è sempre intuitivo quando questi operatori vengono utilizzati in un'operazione di selezione. Ad esempio, considerati i dati e la tabella seguenti, si supponga di voler ottenere come risultato la macchina rossa meno costosa e la macchina blu più costosa, ovvero la berlina rossa e il furgone blu.  
  
```  
CREATE TABLE dbo.Cars(Model varchar(15), Price money, Color varchar(10));  
INSERT dbo.Cars VALUES  
    ('sedan', 10000, 'red'), ('convertible', 15000, 'blue'),   
    ('coupe', 20000, 'red'), ('van', 8000, 'blue');  
```  
  
 Per ottenere questi risultati, è possibile scrivere la query seguente.  
  
```  
SELECT TOP(1) Model, Color, Price  
FROM dbo.Cars  
WHERE Color = 'red'  
UNION ALL  
SELECT TOP(1) Model, Color, Price  
FROM dbo.Cars  
WHERE Color = 'blue'  
ORDER BY Price ASC;  
```  
  
 Set di risultati:  
  
 ```
 Model         Color      Price  
 ------------- ---------- -------  
 sedan         red        10000.00  
 convertible   blue       15000.00
 ```  
  
 I risultati imprevisti vengono restituiti perché la clausola TOP viene eseguita logicamente prima della clausola ORDER BY che consente di ordinare i risultati dell'operatore (UNION ALL in questo caso). La query precedente restituisce pertanto qualsiasi macchina rossa e qualsiasi macchina blu, quindi ordina il risultato di quell'unione in base al prezzo. Nell'esempio seguente viene illustrato il metodo corretto per scrivere questa query per ottenere il risultato desiderato.  
  
```  
SELECT Model, Color, Price  
FROM (SELECT TOP(1) Model, Color, Price  
      FROM dbo.Cars  
      WHERE Color = 'red'  
      ORDER BY Price ASC) AS a  
UNION ALL  
SELECT Model, Color, Price  
FROM (SELECT TOP(1) Model, Color, Price  
      FROM dbo.Cars  
      WHERE Color = 'blue'  
      ORDER BY Price ASC) AS b;  
```  
  
 Tramite le clausole TOP e ORDER BY in un'operazione sub-SELECT, ci si assicura che i risultati della clausola ORDER BY vengano utilizzati applicati alla clausola TOP e non all'ordinamento del risultato dell'operazione UNION.  
  
 Set di risultati:  
  
 ```
 Model         Color      Price  
 ------------- ---------- -------  
 sedan         red        10000.00  
 van           blue        8000.00
 ```  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Se la clausola TOP viene utilizzata con INSERT, MERGE o DELETE, le righe a cui viene fatto riferimento non vengono disposte in alcun ordine e la clausola ORDER BY non può essere specificata direttamente in tali istruzioni. Se è necessario utilizzare TOP per inserire, eliminare o modificare righe in un ordine cronologico significativo, è necessario utilizzare TOP con una clausola ORDER BY specificata in un'istruzione sub-SELECT. Vedere la sezione Esempi più avanti in questo argomento.  
  
 Non è possibile utilizzare TOP nelle istruzioni UPDATE e DELETE in viste partizionate.  
  
 Non è possibile combinare TOP con OFFSET e FETCH nella stessa espressione di query (nello stesso ambito della query). Per altre informazioni, vedere [Clausola ORDER BY &#40;Transact-SQL&#41;](../../t-sql/queries/select-order-by-clause-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
|Category|Elementi di sintassi inclusi|  
|--------------|------------------------------|  
|[Sintassi di base](#BasicSyntax)|TOP • PERCENT|  
|[Inclusione di valori equivalenti](#tie)|WITH TIES|  
|[Limitazione delle righe interessate da DELETE, INSERT o UPDATE](#DML)|DELETE • INSERT • UPDATE|  
  
###  <a name="BasicSyntax"></a>Sintassi di base  
 Negli esempi contenuti in questa sezione vengono illustrate le funzionalità di base della clausola ORDER BY utilizzando la sintassi minima necessaria.  
  
#### <a name="a-using-top-with-a-constant-value"></a>A. Utilizzo di TOP con un valore costante  
 Negli esempi seguenti viene utilizzato un valore costante per specificare il numero di dipendenti restituiti nel set di risultati della query. Nel primo esempio le prime 10 righe non definite vengono restituite perché non viene utilizzata una clausola ORDER BY. Nel secondo esempio viene utilizzata una clausola ORDER BY per restituire i primi 10 dipendenti assunti di recente.  
  
```  
USE AdventureWorks2012;  
GO  
-- Select the first 10 random employees.  
SELECT TOP(10)JobTitle, HireDate  
FROM HumanResources.Employee;  
GO  
-- Select the first 10 employees hired most recently.  
SELECT TOP(10)JobTitle, HireDate  
FROM HumanResources.Employee  
ORDER BY HireDate DESC;  
  
```  
  
#### <a name="b-using-top-with-a-variable"></a>B. Utilizzo di TOP con una variabile  
 Nell'esempio seguente viene utilizzata una variabile per specificare il numero di dipendenti restituiti nel set di risultati della query.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @p AS int = 10;  
SELECT TOP(@p)JobTitle, HireDate, VacationHours  
FROM HumanResources.Employee  
ORDER BY VacationHours DESC  
GO  
  
```  
  
#### <a name="c-specifying-a-percentage"></a>C. Specifica di una percentuale  
 Nell'esempio seguente viene utilizzato PERCENT per specificare il numero di dipendenti restituiti nel set di risultati della query. Nella tabella `HumanResources.Employee` sono presenti 290 dipendenti. Poiché il 5 percento di 290 è un valore frazionario, il valore viene arrotondato al numero intero più vicino.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TOP(5)PERCENT JobTitle, HireDate  
FROM HumanResources.Employee  
ORDER BY HireDate DESC;  
  
```  
  
###  <a name="tie"></a>Inclusione di valori equivalenti  
  
#### <a name="a-using-with-ties-to-include-rows-that-match-the-values-in-the-last-row"></a>A. Utilizzo di WITH TIES per includere righe corrispondenti ai valori nell'ultima riga  
 Nell'esempio seguente viene restituita la percentuale `10` di tutti i dipendenti che percepiscono lo stipendio più alto in ordine decrescente in base al salario. `WITH TIES` garantisce che nel set di risultati vengano inclusi anche tutti i dipendenti con uno stipendio pari allo stipendio più basso restituito (ultima riga), anche se in questo modo viene superata la percentuale di dipendenti `10`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TOP(10)WITH TIES  
pp.FirstName, pp.LastName, e.JobTitle, e.Gender, r.Rate  
FROM Person.Person AS pp   
    INNER JOIN HumanResources.Employee AS e  
        ON pp.BusinessEntityID = e.BusinessEntityID  
    INNER JOIN HumanResources.EmployeePayHistory AS r  
        ON r.BusinessEntityID = e.BusinessEntityID  
ORDER BY Rate DESC;  
  
```  
  
###  <a name="DML"></a>Limitazione delle righe interessate da DELETE, INSERT o UPDATE  
  
#### <a name="a-using-top-to-limit-the-number-of-rows-deleted"></a>A. Utilizzo di TOP per limitare il numero di righe eliminate  
 Quando TOP (*n*) clausola viene utilizzata con DELETE, l'operazione di eliminazione viene eseguita su una selezione non definita di  *n*  numero di righe. Ovvero, l'istruzione DELETE sceglie qualsiasi (*n*) numero di righe che soddisfano i criteri definiti nella clausola WHERE. Nell'esempio seguente vengono eliminate `20` righe dalla tabella `PurchaseOrderDetail` con scadenze precedenti al 1* luglio 2002.  
  
```  
USE AdventureWorks2012;  
GO  
DELETE TOP (20)   
FROM Purchasing.PurchaseOrderDetail  
WHERE DueDate < '20020701';  
GO  
  
```  
  
 Se è necessario utilizzare TOP per eliminare le righe in un ordine cronologico significativo, è necessario utilizzare TOP insieme a ORDER BY in un'istruzione subselect. Tramite la query seguente vengono eliminate le 10 righe della tabella `PurchaseOrderDetail` contenenti le date di scadenza più imminenti. Per assicurarsi che vengano eliminate solo 10 righe, la colonna specificata nell'istruzione di selezione secondaria (`PurchaseOrderID`) è la chiave primaria della tabella. L'utilizzo di una colonna non chiave nell'istruzione sub-SELECT può avere come conseguenza l'eliminazione di più di 10 righe se la colonna specificata contiene valori duplicati.  
  
```  
USE AdventureWorks2012;  
GO  
DELETE FROM Purchasing.PurchaseOrderDetail  
WHERE PurchaseOrderDetailID IN  
   (SELECT TOP 10 PurchaseOrderDetailID   
    FROM Purchasing.PurchaseOrderDetail   
    ORDER BY DueDate ASC);  
GO  
```  
  
#### <a name="b-using-top-to-limit-the-number-of-rows-inserted"></a>B. Utilizzo di TOP per limitare il numero di righe inserite  
 Nell'esempio seguente viene creata la tabella `EmployeeSales` in cui vengono inseriti il nome e i dati di vendita da inizio anno per i primi 5 dipendenti dalla tabella `HumanResources.Employee`. L'istruzione INSERT sceglie 5 righe qualsiasi restituite dall'istruzione `SELECT` che soddisfano i criteri definiti nella clausola WHERE.  La clausola OUTPUT consente di visualizzare le righe inserite nella tabella `EmployeeSales`. Si noti che la clausola ORDER BY nell'istruzione SELECT non viene utilizzata per determinare i primi 5 dipendenti.  
  
```  
USE AdventureWorks2012 ;  
GO  
IF OBJECT_ID ('dbo.EmployeeSales', 'U') IS NOT NULL  
    DROP TABLE dbo.EmployeeSales;  
GO  
CREATE TABLE dbo.EmployeeSales  
( EmployeeID   nvarchar(11) NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  YearlySales  money NOT NULL  
 );  
GO  
INSERT TOP(5)INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, inserted.LastName, inserted.YearlySales  
    SELECT sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
  
```  
  
 Se è necessario utilizzare TOP per inserire righe in un ordine cronologico significativo, è necessario utilizzare questa clausola insieme a ORDER BY in un'istruzione sub-SELECT, come illustrato nell'esempio seguente. La clausola OUTPUT consente di visualizzare le righe inserite nella tabella `EmployeeSales`. I primi 5 dipendenti vengono ora inseriti in base ai risultati della clausola ORDER BY anziché alle righe non definite.  
  
```  
INSERT INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, inserted.LastName, inserted.YearlySales  
    SELECT TOP (5) sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
  
```  
  
#### <a name="c-using-top-to-limit-the-number-of-rows-updated"></a>C. Utilizzo di TOP per limitare il numero di righe aggiornate  
 Nell'esempio seguente viene utilizzata la clausola TOP per aggiornare righe in una tabella. Quando TOP (*n*) clausola viene utilizzata con l'aggiornamento, l'operazione di aggiornamento viene eseguita su un numero indefinito di righe. Ovvero, l'istruzione UPDATE sceglie qualsiasi (*n*) numero di righe che soddisfano i criteri definiti nella clausola WHERE. Nell'esempio seguente vengono assegnati 10 clienti da un venditore a un altro.  
  
```  
USE AdventureWorks2012;  
UPDATE TOP (10) Sales.Store  
SET SalesPersonID = 276  
WHERE SalesPersonID = 275;  
GO  
```  
  
 Se è necessario utilizzare TOP per applicare gli aggiornamenti in un ordine cronologico significativo, è necessario utilizzare questa clausola insieme a ORDER BY in un'istruzione sub-SELECT. Nell'esempio seguente le ore di ferie dei 10 dipendenti vengono aggiornate con le prime date di assunzione.  
  
```  
UPDATE HumanResources.Employee  
SET VacationHours = VacationHours + 8  
FROM (SELECT TOP 10 BusinessEntityID FROM HumanResources.Employee  
     ORDER BY HireDate ASC) AS th  
WHERE HumanResources.Employee.BusinessEntityID = th.BusinessEntityID;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'esempio seguente restituisce le prime 31 righe corrispondenti ai criteri di query. Il **ORDER BY** clausola viene utilizzata per assicurare che il 31 restituite le righe sono le 31 innanzitutto righe in base a un ordine alfabetico del `LastName` colonna.  
  
 Utilizzando **TOP** senza specificare i valori equivalenti.  
  
```  
SELECT TOP (31) FirstName, LastName   
FROM DimEmployee ORDER BY LastName;  
```  
  
 Risultato: 31 viene restituita.  
  
 Utilizzo di TOP, specificando WITH TIES.  
  
```  
SELECT TOP (31) WITH TIES FirstName, LastName   
FROM DimEmployee ORDER BY LastName;  
```  
  
 Risultato: 33 righe vengono restituite, in quanto i 3 dipendenti denominati Brown tie per la riga 31.  
  
## <a name="see-also"></a>Vedere anche  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Clausola ORDER BY clausola &#40; Transact-SQL &#41;](../../t-sql/queries/select-order-by-clause-transact-sql.md)   
 [SET ROWCOUNT &#40; Transact-SQL &#41;](../../t-sql/statements/set-rowcount-transact-sql.md)   
 [MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  
  
  


