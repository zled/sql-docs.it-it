---
title: ISNULL (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISNULL
- ISNULL_TSQL
- IFNULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- replacing null values
- null values [SQL Server], ISNULL
- null values [SQL Server], replacement values
- ISNULL function
ms.assetid: 6f3e5802-864b-4e77-9862-657bb5430b68
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8d364548d3303de493343365bd16677ffdfd5641
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="isnull-transact-sql"></a>ISNULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Sostituisce il valore NULL con il valore di sostituzione specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ISNULL ( check_expression , replacement_value )  
```  
  
## <a name="arguments"></a>Argomenti  
 *check_expression*  
 È il [espressione](../../t-sql/language-elements/expressions-transact-sql.md) da controllare i valori NULL. *check_expression* può essere di qualsiasi tipo.  
  
 *replacement_value*  
 Espressione da restituire se *check_expression* è NULL. *replacement_value* deve essere di un tipo convertibile in modo implicito nel tipo di *check_expresssion*.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce lo stesso tipo *check_expression*. Se un valore NULL letterale viene fornito come *check_expression*, restituisce il tipo di dati di *replacement_value*. Se un valore NULL letterale viene fornito come *check_expression* e no *replacement_value* è specificato, restituisce un **int**.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di *check_expression* viene restituito se non è NULL; in caso contrario, *replacement_value* restituito dopo la conversione implicita nel tipo di *check_expression*, se i tipi sono diversi. *replacement_value* può essere troncato se *replacement_value* è più lungo di *check_expression*.  
  
> [!NOTE]  
>  Utilizzare [COALESCE &#40; Transact-SQL &#41; ](../../t-sql/language-elements/coalesce-transact-sql.md) per restituire il primo valore non null.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-isnull-with-avg"></a>A. Utilizzo di ISNULL con AVG  
 Nell'esempio seguente viene calcolato il valore medio del peso di tutti i prodotti. Viene inoltre sostituito il valore `50` per tutte le voci NULL nella colonna `Weight` della tabella `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT AVG(ISNULL(Weight, 50))  
FROM Production.Product;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `--------------------------`  
  
 `59.79`  
  
 `(1 row(s) affected)`  
  
### <a name="b-using-isnull"></a>B. Utilizzo di ISNULL  
 Nell'esempio seguente vengono selezionate la descrizione, la percentuale di sconto, la quantità minima e la quantità massima per tutte le offerte speciali in `AdventureWorks2012`. Se la quantità massima per una determinata offerta speciale è NULL, il valore di `MaxQty` visualizzato nel set di risultati è `0.00`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Description, DiscountPct, MinQty, ISNULL(MaxQty, 0.00) AS 'Max Quantity'  
FROM Sales.SpecialOffer;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|  Description       |  DiscountPct    |   MinQty    |   Quantità massima       |
|  ---------------   |  -------------  |   --------  |   ---------------    |
|  No Discount       |  0,00           |   0         |   0                  |
|  Volume Discount   |  0.02           |   11        |   14                 |
|  Volume Discount   |  0.05           |   15        |   4                  |
|  Volume Discount   |  0.10           |   25        |   0                  |
|  Volume Discount   |  0.15           |   41        |   0                  |
|  Volume Discount   |  0.20           |   61        |   0                  |
|  Mountain-100 Cl   |  0.35           |   0         |   0                  |
|  Sport Helmet SEN   |  0.10           |   0         |   0                  |
|  Road-650 Overst   |  0.30           |   0         |   0                  |
|  Mountain Tire, S   |  0,50           |   0         |   0                  |
|  Sport Helmet SEN   |  0.15           |   0         |   0                  |
|  LL Road Frame S   |  0.35           |   0         |   0                  |
|  Codice Pr Touring-3000   |  0.15           |   0         |   0                  |
|  Codice Pr Touring-1000   |  0.20           |   0         |   0                  |
|  Metà prezzo Peda   |  0,50           |   0         |   0                  |
|  Si mountain-500   |  0.40           |   0         |   0                  |

 `(16 row(s) affected)`  
  
### <a name="c-testing-for-null-in-a-where-clause"></a>C. Verifica dei valori NULL in una clausola WHERE  
 Per trovare i valori NULL, non utilizzare ISNULL, bensì IS NULL. Nell'esempio seguente vengono trovati tutti i prodotti con valore `NULL` nella colonna relativa al peso. Si noti lo spazio tra `IS` e `NULL`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name, Weight  
FROM Production.Product  
WHERE Weight IS NULL;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-isnull-with-avg"></a>D. Utilizzo di ISNULL con AVG  
 Nell'esempio seguente consente di trovare il valore medio del peso di tutti i prodotti in una tabella di esempio. Viene inoltre sostituito il valore `50` per tutte le voci NULL nella colonna `Weight` della tabella `Product`.  
  
```  
-- Uses AdventureWorks  
  
SELECT AVG(ISNULL(Weight, 50))  
FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------------------------   
52.88   
```  
  
### <a name="e-using-isnull"></a>E. Utilizzo di ISNULL  
 L'esempio seguente usa ISNULL per verificare i valori NULL nella colonna `MinPaymentAmount` e visualizzare il valore `0.00` per le righe.  
  
```  
-- Uses AdventureWorks  
  
SELECT ResellerName,   
       ISNULL(MinPaymentAmount,0) AS MinimumPayment  
FROM dbo.DimReseller  
ORDER BY ResellerName;  
  
```  
  
 Set di risultati parziale:  
  
|  ResellerName                |  MinimumPayment    |
|  -------------------------   |  --------------    |
|  Un'associazione di biciclette       |     0.0000         |
|  Un archivio di biciclette                |     0.0000         |
|  Un reparto di ciclo                |     0.0000         |
|  Un'azienda di biciclette eccellente     |     0.0000         |
|  Un reparto Bike tipico         |   200.0000         |
|  Servizio & Sales accettabile  |     0.0000         |
  
### <a name="f-using-is-null-to-test-for-null-in-a-where-clause"></a>F. Uso di IS NULL per verificare i valori NULL in una clausola WHERE  
 Nell'esempio seguente consente di individuare tutti i prodotti con `NULL` nel `Weight` colonna. Si noti lo spazio tra `IS` e `NULL`.  
  
```  
-- Uses AdventureWorks  
  
SELECT EnglishProductName, Weight  
FROM dbo.DimProduct  
WHERE Weight IS NULL;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [È NULL &#40; Transact-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)   
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [COALESCE &#40; Transact-SQL &#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  


