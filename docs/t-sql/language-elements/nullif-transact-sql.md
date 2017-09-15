---
title: NULLIF (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NULLIF
- NULLIF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], equivalent expressions
- expressions [SQL Server], null values
- NULLIF function
- equivalent expressions [SQL Server]
ms.assetid: 44c7b67e-74c7-4bb9-93a4-7a3016bd2feb
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fe8e4663688ce510d9600ebeba9d3c30703ee3aa
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="nullif-transact-sql"></a>NULLIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce un valore Null se le due espressioni specificate sono uguali. Ad esempio, `SELECT NULLIF(4,4) AS Same, NULLIF(5,7) AS Different;` restituisce NULL per la prima colonna (4 e 4) perché i due valori di input sono uguali. La seconda colonna restituisce il primo valore (5), poiché i due valori di input sono diversi. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
NULLIF ( expression , expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 Qualsiasi valore valido scalare [espressione](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce lo stesso tipo del primo *espressione*.  
  
 NULLIF restituisce il primo *espressione* se le due espressioni non sono uguali. Se le espressioni sono uguali, NULLIF restituisce un valore null del tipo del primo *espressione*.  
  
## <a name="remarks"></a>Osservazioni  
 NULLIF è equivalente a un'espressione CASE avanzata in cui le due espressioni sono uguali e l'espressione risultante è Null.  
  
 È consigliabile non utilizzare funzioni dipendenti dal tempo, ad esempio RAND(), in una funzione NULLIF. Ciò potrebbe causare la funzione deve essere valutata due volte e restituire risultati diversi dalle due chiamate.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-budget-amounts-that-have-not-changed"></a>A. Restituzione degli importi del budget non modificati  
 Nell'esempio seguente viene creata una tabella `budgets` per visualizzare un reparto (`dept`), il relativo budget corrente (`current_year`) e il relativo budget precedente (`previous_year`). Per l'anno in corso, viene utilizzato `NULL` per i reparti in cui il budget dell'anno corrente è uguale a quello dell'anno precedente e `0` per i budget non ancora definiti. Per trovare la media solo dei reparti che ricevono un budget e includere inoltre il valore del budget dell'anno precedente (utilizzare il valore `previous_year` se `current_year` è `NULL`), vengono combinate le funzioni `NULLIF` e `COALESCE`.  
  
```sql  
CREATE TABLE dbo.budgets  
(  
   dept            tinyint   IDENTITY,  
   current_year      decimal   NULL,  
   previous_year   decimal   NULL  
);  
INSERT budgets VALUES(100000, 150000);  
INSERT budgets VALUES(NULL, 300000);  
INSERT budgets VALUES(0, 100000);  
INSERT budgets VALUES(NULL, 150000);  
INSERT budgets VALUES(300000, 250000);  
GO    
SET NOCOUNT OFF;  
SELECT AVG(NULLIF(COALESCE(current_year,  
   previous_year), 0.00)) AS 'Average Budget'  
FROM budgets;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Average Budget  
 --------------  
 212500.000000  
 (1 row(s) affected)
 ```  
  
### <a name="b-comparing-nullif-and-case"></a>B. Confronto tra NULLIF e CASE  
 Per illustrare la somiglianza tra `NULLIF` e `CASE`, nelle query seguenti viene determinato se i valori nelle colonne `MakeFlag` e `FinishedGoodsFlag` corrispondono. La prima query utilizza `NULLIF`. La seconda query utilizza l'espressione `CASE`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,   
   NULLIF(MakeFlag,FinishedGoodsFlag)AS 'Null if Equal'  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,'Null if Equal' =  
   CASE  
       WHEN MakeFlag = FinishedGoodsFlag THEN NULL  
       ELSE MakeFlag  
   END  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
```  

### <a name="c-returning-budget-amounts-that-contain-no-data"></a>C: restituzione degli importi del budget che non contengono dati  
 Nell'esempio seguente viene creato un `budgets` tabella, carica i dati e Usa `NULLIF` per restituire un valore null se non si specifica `current_year` né `previous_year` contiene dati.  
  
```sql  
CREATE TABLE budgets (  
   dept           tinyint,  
   current_year   decimal(10,2),  
   previous_year  decimal(10,2)  
);  
  
INSERT INTO budgets VALUES(1, 100000, 150000);  
INSERT INTO budgets VALUES(2, NULL, 300000);  
INSERT INTO budgets VALUES(3, 0, 100000);  
INSERT INTO budgets VALUES(4, NULL, 150000);  
INSERT INTO budgets VALUES(5, 300000, 300000);  
  
SELECT dept, NULLIF(current_year,  
   previous_year) AS LastBudget  
FROM budgets;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 dept   LastBudget  
 ----   -----------  
 1      100000.00  
 2      null 
 3      0.00  
 4      null  
 5      null
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [CASE &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Decimal e numeric &#40; Transact-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [Funzioni di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


