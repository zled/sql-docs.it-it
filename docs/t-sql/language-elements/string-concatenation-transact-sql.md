---
title: + (Concatenazione di stringhe) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- concatenation
- +
- string
dev_langs:
- TSQL
helpviewer_keywords:
- concatenation [SQL Server]
- string concatenation operators
- + (string concatenation)
ms.assetid: 35cb3d7a-48f5-4b13-926c-a9d369e20ed7
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 66f482d424c6be56d89e8ec5b99cff30b2ddab0b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="-string-concatenation-transact-sql"></a>+ (concatenazione di stringhe) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Operatore in un'espressione stringa che consente di concatenare in un'unica espressione due o più stringhe di tipo carattere o binario, colonne o una combinazione di nomi di colonna e stringhe (operatore di stringa).  Ad esempio `SELECT 'book'+'case';` restituisce `bookcase`.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
expression + expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi dei dati di tipi di carattere e categoria di tipi di dati binari, ad eccezione di **immagine**, **ntext**, o **testo**tipi di dati. È necessario che alle due espressioni sia applicato lo stesso tipo di dati oppure che un'espressione possa essere convertita in modo implicito nel tipo di dati dell'altra espressione.  
  
 Per la concatenazione di stringhe binarie e dei caratteri tra le stringhe binarie, è necessario eseguire una conversione esplicita in dati di tipo carattere. Nell'esempio seguente viene illustrato quando `CONVERT`, o `CAST`, deve essere utilizzata con la concatenazione binaria e quando `CONVERT`, o `CAST`, non deve essere utilizzato.  
  
```  
DECLARE @mybin1 varbinary(5), @mybin2 varbinary(5)  
SET @mybin1 = 0xFF  
SET @mybin2 = 0xA5  
-- No CONVERT or CAST function is required because this example   
-- concatenates two binary strings.  
SELECT @mybin1 + @mybin2  
-- A CONVERT or CAST function is required because this example  
-- concatenates two binary strings plus a space.  
SELECT CONVERT(varchar(5), @mybin1) + ' '   
   + CONVERT(varchar(5), @mybin2)  
-- Here is the same conversion using CAST.  
SELECT CAST(@mybin1 AS varchar(5)) + ' '   
   + CAST(@mybin2 AS varchar(5))  
  
```  
  
## <a name="result-types"></a>Tipi restituiti  
 Viene restituito il tipo di dati dell'argomento con precedenza maggiore. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 L'operatore + di concatenazione delle stringhe ha un funzionamento diverso quando viene utilizzato con una stringa vuota, di lunghezza zero, rispetto a quando viene utilizzato con valori NULL, o sconosciuti. Una stringa di caratteri di lunghezza zero può essere specificata con due virgolette singole senza alcun carattere all'interno delle virgolette. Una stringa binaria di lunghezza zero può essere specificata con 0x senza alcun valore byte nella costante esadecimale. La concatenazione di una stringa di valore zero comporta sempre la concatenazione delle due stringhe specificate. Quando si utilizzano stringhe con un valore Null, il risultato della concatenazione dipende dalle impostazioni della sessione. Allo stesso modo di quanto accade per le operazioni aritmetiche eseguite su valori Null, in cui, quando un valore Null viene aggiunto a un valore noto, il risultato è in genere un valore sconosciuto, un'operazione di concatenazione di stringhe eseguita con un valore Null dovrebbe restituire un risultato Null. Tuttavia, è possibile modificare questo comportamento modificando l'impostazione di `CONCAT_NULL_YIELDS_NULL` per la sessione corrente. Per altre informazioni, vedere [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).  
  
 Se il risultato della concatenazione di stringhe supera il limite di 8.000 byte, il risultato viene troncato. Se tuttavia almeno una delle stringhe concatenate è un tipo di dati per valori di grandi dimensioni, il troncamento non avviene.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-string-concatenation"></a>A. Utilizzo della concatenazione di stringhe  
 Nell'esempio seguente viene creata una singola colonna sotto l'intestazione `Name` in base a più colonne di tipo carattere, con il cognome della persona seguito da una virgola, uno spazio e successivamente il nome. Il set di risultati è visualizzato in ordine alfabetico crescente in base prima al cognome e quindi al nome.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + FirstName) AS Name  
FROM Person.Person  
ORDER BY LastName ASC, FirstName ASC;  
```  
  
### <a name="b-combining-numeric-and-date-data-types"></a>B. Combinazione di tipi di dati numeric e date  
 L'esempio seguente usa il `CONVERT` (funzione) per concatenare **numerico** e **data** tipi di dati.  
  
```  
-- Uses AdventureWorks  
  
SELECT 'The order is due on ' + CONVERT(varchar(12), DueDate, 101)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID = 50001;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `------------------------------------------------`  
  
 `The order is due on 04/23/2007`  
  
 `(1 row(s) affected)`  
  
### <a name="c-using-multiple-string-concatenation"></a>C. Utilizzo della concatenazione di più stringhe  
 Nell'esempio seguente vengono concatenate più stringhe per ottenere un'unica stringa di lunghezza maggiore per visualizzare il cognome e l'iniziale del nome dei vicepresidenti in [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]. Vengono aggiunti una virgola dopo il cognome e un punto dopo l'iniziale del nome.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ',' + SPACE(1) + SUBSTRING(FirstName, 1, 1) + '.') AS Name, e.JobTitle  
FROM Person.Person AS p  
    JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle LIKE 'Vice%'  
ORDER BY LastName ASC;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Name               Title`  
  
 `-------------      ---------------`  
  
 `Duffy, T.          Vice President of Engineering`  
  
 `Hamilton, J.       Vice President of Production`  
  
 `Welcker, B.        Vice President of Sales`  
  
 `(3 row(s) affected)`  
 
### <a name="d-using-large-strings-in-concatenation"></a>D. Utilizzo di stringhe di grandi dimensioni in concatenazione
Nell'esempio seguente consente di concatenare più stringhe per formare una stringa lunga e quindi tenta di calcolare la lunghezza della stringa finale. La lunghezza del set di risultati finale è 16000, perché l'espressione di valutazione viene avviata da sinistra che è @x + @z + @y = > (@x + @z) + @y. In questo caso, il risultato di (@x + @z) vengono troncati a 8000 byte e quindi @y viene aggiunto al set di risultati, che rende la lunghezza della stringa finale 16000. Poiché @y è una stringa di tipo di valori di grandi dimensioni, non il troncamento.

```
DECLARE @x varchar(8000) = replicate('x', 8000)
DECLARE @y varchar(max) = replicate('y', 8000)
DECLARE @z varchar(8000) = replicate('z',8000)
SET @y = @x + @z + @y
-- The result of following select is 16000
SELECT len(@y) AS y
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `y      `  
  
 `-------`  
  
 `16000`  
  
  `(1 row(s) affected)`  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-string-concatenation"></a>E. Utilizzo della concatenazione di stringhe  
 Nell'esempio seguente viene creata una singola colonna sotto l'intestazione di colonna `Name` dalle colonne più caratteri, con il cognome del contatto seguito da una virgola, uno spazio e il nome del contatto. Il set di risultati è visualizzato in ordine alfabetico crescente in base prima al cognome e quindi al nome.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + FirstName) AS Name  
FROM DimEmployee  
ORDER BY LastName ASC, FirstName ASC;  
```  
  
### <a name="f-using-multiple-string-concatenation"></a>F. Utilizzo della concatenazione di più stringhe  
 Nell'esempio seguente consente di concatenare più stringhe per formare una stringa lunga per visualizzare il cognome e l'iniziale dei vicepresidenti all'interno di un database di esempio. Vengono aggiunti una virgola dopo il cognome e un punto dopo l'iniziale del nome.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + SUBSTRING(FirstName, 1, 1) + '.') AS Name, Title  
FROM DimEmployee  
WHERE Title LIKE '%Vice Pres%'  
ORDER BY LastName ASC;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Name               Title                                           
-------------      ---------------  
Duffy, T.          Vice President of Engineering  
Hamilton, J.       Vice President of Production  
Welcker, B.        Vice President of Sales  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [+ = &#40; Concatenazione di stringhe &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/string-concatenation-equal-transact-sql.md)  
  
  




