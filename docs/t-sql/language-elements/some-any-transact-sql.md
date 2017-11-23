---
title: ALCUNI | QUALSIASI (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
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
- SOME
- SOME_TSQL
dev_langs: TSQL
helpviewer_keywords:
- scalar values
- comparing scalar with single-column set
- ANY operator
- SOME | ANY keyword
- single-column set of values [SQL Server]
ms.assetid: 1f717ad6-f67b-4980-9397-577ecb0e5789
caps.latest.revision: "41"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f962702faec170262f50c3c2ca5c328af3bc266d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="some--any-transact-sql"></a>SOME | ANY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Confronta un valore scalare con un set di valori a colonna singola. SOME e ANY sono equivalenti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
scalar_expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
     { SOME | ANY } ( subquery )   
```  
  
## <a name="arguments"></a>Argomenti  
 *scalar_expression*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Qualsiasi operatore di confronto valido.  
  
 SOME | ANY  
 Specifica che deve essere eseguito un confronto.  
  
 *sottoquery*  
 Sottoquery che include un set di risultati di una colonna. Il tipo di dati della colonna restituita deve essere il tipo di dati stesso come *scalar_expression*.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="result-value"></a>Valore restituito  
 SOME o ANY restituisce **TRUE** quando il confronto specificato è TRUE per qualsiasi coppia (*scalar_expression***,***x*) in cui *x* è un valore nel set di colonna singola; in caso contrario, restituisce **FALSE**.  
  
## <a name="remarks"></a>Osservazioni  
 ALCUNI richiede il *scalar_expression* deve essere confrontato per almeno un valore restituito dalla sottoquery. Per le istruzioni che richiedono il *scalar_expression* per deve essere confrontato con ogni valore viene restituito dalla sottoquery, vedere [tutti &#40; Transact-SQL &#41; ](../../t-sql/language-elements/all-transact-sql.md). Ad esempio, se la sottoquery restituisce i valori 2 e 3, *scalar_expression* = SOME (sottoquery) restituisce TRUE per un *scalar_express* di 2. Se la sottoquery restituisce i valori 2 e 3, *scalar_expression* = ALL (sottoquery) restituisce false, perché alcuni dei valori della sottoquery (il valore 3) non soddisfano i criteri dell'espressione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-running-a-simple-example"></a>A. Esecuzione di un esempio semplice  
 Le istruzioni seguenti consentono di creare una tabella semplice e di aggiungere i valori di `1`, `2`, `3` e `4` alla colonna `ID`.  
  
```  
CREATE TABLE T1  
(ID int) ;  
GO  
INSERT T1 VALUES (1) ;  
INSERT T1 VALUES (2) ;  
INSERT T1 VALUES (3) ;  
INSERT T1 VALUES (4) ;  
```  
  
 Nella query seguente viene restituito `TRUE` perché `3` è inferiore ad alcuni valori della tabella.  
  
```  
IF 3 < SOME (SELECT ID FROM T1)  
PRINT 'TRUE'   
ELSE  
PRINT 'FALSE' ;  
```  
  
 Nella query seguente viene restituito `FALSE` perché `3` non è inferiore a tutti i valori della tabella.  
  
```  
IF 3 < ALL (SELECT ID FROM T1)  
PRINT 'TRUE'   
ELSE  
PRINT 'FALSE' ;  
```  
  
### <a name="b-running-a-practical-example"></a>B. Esecuzione di un esempio pratico  
 Nell'esempio seguente viene creata una stored procedure che determina se tutti i componenti di un oggetto specificato `SalesOrderID` nel `AdventureWorks2012` database può essere prodotti nel numero di giorni specificato. Nell'esempio viene utilizzata una sottoquery per creare un elenco contenente i numeri corrispondenti ai valori di `DaysToManufacture` per tutti i componenti della colonna `SalesOrderID` specifica e viene quindi verificato se alcuni dei valori restituiti dalla sottoquery sono maggiori del numero di giorni specificato. Se ogni valore di `DaysToManufacture` restituito è minore del numero specificato, la condizione è TRUE e viene stampato il primo messaggio.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE ManyDaysToComplete @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays < SOME  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'At least one item for this order cannot be manufactured in specified number of days.'  
ELSE   
PRINT 'All items for this order can be manufactured in the specified number of days or less.' ;  
  
```  
  
 Per testare la procedura, eseguire la procedura utilizzando il `SalesOrderID``49080`, che dispone di un componente che richiede `2` giorni e due componenti che richiedono 0 giorni. La prima istruzione soddisfa i criteri, mentre la seconda no.  
  
```  
EXECUTE ManyDaysToComplete 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in the specified number of days or less.`  
  
```  
EXECUTE ManyDaysToComplete 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `At least one item for this order cannot be manufactured in specified number of days.`  
  
## <a name="see-also"></a>Vedere anche  
 [Tutti i &#40; Transact-SQL &#41;](../../t-sql/language-elements/all-transact-sql.md)   
 [CASE &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/language-elements/in-transact-sql.md)  
  
  
