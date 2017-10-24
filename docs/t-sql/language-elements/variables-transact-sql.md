---
title: Variabili (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f372ae86-a003-40af-92de-fa52e3eea13f
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c77c323f8e9dbb2abc010c3fbc9e6d2b349c8ae1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="variables-transact-sql"></a>Variabili (Transact-SQL)
[!INCLUDE[tsql-appliesto-tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Una variabile locale di Transact-SQL è un oggetto che può contenere un singolo valore di dati di un tipo specifico. Le variabili vengono in genere utilizzate in batch e script per gli scopi seguenti: 

* Contare o controllare il numero di esecuzioni di un ciclo fungendo da contatori.
* Archiviare un valore di dati che deve essere testato da un'istruzione per il controllo di flusso.
* Salvare un valore di dati che deve essere restituito dal codice restituito di una stored procedure o dal valore restituito da una funzione.

> [!NOTE]
> I nomi di alcune funzioni di sistema Transact-SQL iniziano con due *in* Chiocciole (@ @). Benché nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], @@functions vengono definite a come le variabili globali, non sono variabili e non è simile a quello delle variabili. Il @@functions sono funzioni di sistema e relativa sintassi segue le regole per le funzioni.

Lo script seguente crea e popola con 26 righe una piccola tabella di prova. Lo script utilizza una variabile per eseguire tre operazioni: 

* Controllare il numero di righe inserite verificando il numero di esecuzioni del ciclo.
* Specificare il valore inserito nella colonna integer.
* Funzionare come parte dell'espressione che genera le lettere da inserire nella colonna di tipo carattere.  

```sql
-- Create the table.
CREATE TABLE TestTable (cola int, colb char(3));
GO
SET NOCOUNT ON;
GO
-- Declare the variable to be used.
DECLARE @MyCounter int;

-- Initialize the variable.
SET @MyCounter = 0;

-- Test the variable to see if the loop is finished.
WHILE (@MyCounter < 26)
BEGIN;
   -- Insert a row into the table.
   INSERT INTO TestTable VALUES
       -- Use the variable to provide the integer value
       -- for cola. Also use it to generate a unique letter
       -- for each row. Use the ASCII function to get the
       -- integer value of 'a'. Add @MyCounter. Use CHAR to
       -- convert the sum back to the character @MyCounter
       -- characters after 'a'.
       (@MyCounter,
        CHAR( ( @MyCounter + ASCII('a') ) )
       );
   -- Increment the variable to count this iteration
   -- of the loop.
   SET @MyCounter = @MyCounter + 1;
END;
GO
SET NOCOUNT OFF;
GO
-- View the data.
SELECT cola, colb
FROM TestTable;
GO
DROP TABLE TestTable;
GO
```

## <a name="declaring-a-transact-sql-variable"></a>Dichiarazione di una variabile Transact-SQL
L'istruzione DECLARE Inizializza una variabile Transact-SQL tramite: 
* Assegnazione di un nome. Il nome deve iniziare con il carattere chiocciola (@).
* Assegnazione di un tipo di dati definito dall'utente o di sistema, nonché la lunghezza del tipo di dati. Alle variabili numeriche vengono inoltre assegnate precisione e scala. Alle variabili XML è possibile assegnare una raccolta di schemi facoltativa.
* Impostazione del valore su NULL.

Ad esempio, **DECLARE** istruzione crea una variabile locale denominata  **@mycounter**  con un tipo di dati int.  
```sql
DECLARE @MyCounter int;
```
Per dichiarare più variabili locali, è necessario inserire una virgola dopo la prima variabile locale e quindi specificare il nome della variabile locale successiva con il tipo di dati corrispondente.

Ad esempio, **DECLARE** istruzione crea le tre variabili locali  **@LastName** ,  **@FirstName**  e  **@StateProvince** e la inizializza con il valore NULL:  
```sql
DECLARE @LastName nvarchar(30), @FirstName nvarchar(20), @StateProvince nchar(2);
```

L'ambito di una variabile è le istruzioni di intervallo di Transact-SQL che possono fare riferimento alla variabile. L'ambito inizia in corrispondenza del punto in cui la variabile è stata dichiarata e termina alla fine del batch o della stored procedure che include la dichiarazione. Lo script seguente, ad esempio, genera un errore di sintassi, perché la variabile viene dichiarata in un batch ma vi viene fatto riferimento in un altro batch:  
```sql
USE AdventureWorks2014;
GO
DECLARE @MyVariable int;
SET @MyVariable = 1;
-- Terminate the batch by using the GO keyword.
GO 
-- @MyVariable has gone out of scope and no longer exists.

-- This SELECT statement generates a syntax error because it is
-- no longer legal to reference @MyVariable.
SELECT BusinessEntityID, NationalIDNumber, JobTitle
FROM HumanResources.Employee
WHERE BusinessEntityID = @MyVariable;
```

Le variabili hanno un ambito locale e sono disponibili unicamente nel batch o nella stored procedure in cui sono state definite. Nell'esempio seguente, l'ambito nidificato creato per l'esecuzione di sp_executesql non può accedere alla variabile dichiarata nell'ambito superiore e pertanto viene restituito un errore.  

```sql
DECLARE @MyVariable int;
SET @MyVariable = 1;
EXECUTE sp_executesql N'SELECT @MyVariable'; -- this produces an error
```

## <a name="setting-a-value-in-a-transact-sql-variable"></a>Impostazione di un valore in una variabile Transact-SQL

Quando si dichiara una variabile, il valore corrispondente viene impostato su NULL. Per assegnare un valore alla variabile, utilizzare l'istruzione SET. È consigliabile adottare sempre questo metodo. Per assegnare un valore a una variabile, è inoltre possibile fare riferimento alla variabile stessa nell'elenco di selezione di un'istruzione SELECT.

Se si desidera utilizzare l'istruzione SET per assegnare un valore a una variabile, specificare il nome della variabile e il valore da assegnarvi. È consigliabile adottare sempre questo metodo. Nel batch seguente vengono dichiarate due variabili, alle quali vengono quindi assegnati valori, utilizzati successivamente nella clausola `WHERE` di un'istruzione `SELECT`:  

```sql
USE AdventureWorks2014;
GO
-- Declare two variables.
DECLARE @FirstNameVariable nvarchar(50),
   @PostalCodeVariable nvarchar(15);

-- Set their values.
SET @FirstNameVariable = N'Amy';
SET @PostalCodeVariable = N'BA5 3HX';

-- Use them in the WHERE clause of a SELECT statement.
SELECT LastName, FirstName, JobTitle, City, StateProvinceName, CountryRegionName
FROM HumanResources.vEmployee
WHERE FirstName = @FirstNameVariable
   OR PostalCode = @PostalCodeVariable;
GO
```

Quando si assegna un valore a una variabile tramite un riferimento in un elenco di selezione, è necessario assegnare un valore scalare oppure l'istruzione SELECT deve restituire una sola riga. Esempio:  

```sql
USE AdventureWorks2014;
GO
DECLARE @EmpIDVariable int;

SELECT @EmpIDVariable = MAX(EmployeeID)
FROM HumanResources.Employee;
GO
```

> [!WARNING]
> Se in una singola istruzione SELECT sono presenti più clausole di assegnazione, l'ordine di valutazione delle espressioni non viene garantito. Si noti che gli effetti sono visibili sole se sono presenti riferimenti per le assegnazioni.

Se un'istruzione SELECT restituisce più di una riga e la variabile fa riferimento a un'espressione non scalare, la variabile è impostata sul valore restituito per l'espressione nell'ultima riga del set di risultati. Ad esempio, nel batch seguente  **@EmpIDVariable**  è impostato sul **BusinessEntityID** valore dell'ultima riga restituita, ovvero 1:  

```sql
USE AdventureWorks2014;
GO
DECLARE @EmpIDVariable int;

SELECT @EmpIDVariable = BusinessEntityID
FROM HumanResources.Employee
ORDER BY BusinessEntityID DESC;

SELECT @EmpIDVariable;
GO
```

## <a name="see-also"></a>Vedere anche  
 [Dichiarare@local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
 [SET @local_variable](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
  
 [SELEZIONARE@local_variable](../../t-sql/language-elements/select-local-variable-transact-sql.md)  
  
  

