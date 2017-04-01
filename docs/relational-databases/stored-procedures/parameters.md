---
title: "Parametri | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-non-specified"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "stored procedure [SQL Server], parametri"
  - "funzioni definite dall'utente [SQL Server], parametri"
ms.assetid: c1f9bd93-3271-4098-a23b-7bd7a19ab65b
caps.latest.revision: 2
author: "pmasl"
ms.author: "pelopes"
manager: "jhubbard"
caps.handback.revision: 2
---
# Parametri
I parametri vengono utilizzati per lo scambio di dati tra stored procedure/funzioni e l'applicazione o lo strumento con cui sono state chiamate. 

*  I parametri di input consentono al chiamante di passare un valore di dati alla stored procedure o alla funzione.
*  I parametri di output consentono alla stored procedure di passare nuovamente al chiamante un valore di dati o una variabile di cursore. Con le funzioni definite dall'utente non è possibile specificare parametri di output.
*  Ogni stored procedure restituisce al chiamante un codice integer. Se il valore del codice restituito non è impostato in modo esplicito nella stored procedure, verrà restituito 0.

Nella stored procedure seguente viene illustrato l'utilizzo di un parametro di input, di un parametro di output e di un codice restituito.
```
-- Create a procedure that takes one input parameter and returns one output parameter and a return code.
CREATE PROCEDURE SampleProcedure @EmployeeIDParm INT,
         @MaxTotal INT OUTPUT
AS
-- Declare and initialize a variable to hold @@ERROR.
DECLARE @ErrorSave INT
SET @ErrorSave = 0

-- Do a SELECT using the input parameter.
SELECT FirstName, LastName, JobTitle
FROM HumanResources.vEmployee
WHERE EmployeeID = @EmployeeIDParm

-- Save any nonzero @@ERROR value.
IF (@@ERROR <> 0)
   SET @ErrorSave = @@ERROR

-- Set a value in the output parameter.
SELECT @MaxTotal = MAX(TotalDue)
FROM Sales.SalesOrderHeader;

IF (@@ERROR <> 0)
   SET @ErrorSave = @@ERROR

-- Returns 0 if neither SELECT statement had an error; otherwise, returns the last error.
RETURN @ErrorSave
GO
```

Quando si esegue una stored procedure o una funzione, il valore dei parametri di input può essere impostato su una costante o sul valore di una variabile. I valori dei parametri di output e dei codici restituiti devono essere restituiti in una variabile. I valori dei dati di parametri e di codici restituiti possono inoltre essere scambiati sia con le variabili di Transact-SQL sia con quelle dell'applicazione.

Se una stored procedure viene chiamata da un batch o da uno script, per i valori dei parametri e dei codici restituiti è possibile usare le variabili di Transact-SQL definite nello stesso batch. Nell'esempio seguente viene illustrato un batch che esegue la stored procedure creata in precedenza. Il parametro di input è specificato come costante, mentre il parametro di output e il codice restituito inseriscono i propri valori nelle variabili di Transact-SQL:
```
-- Declare the variables for the return code and output parameter.
DECLARE @ReturnCode INT
DECLARE @MaxTotalVariable INT

-- Execute the stored procedure and specify which variables
-- are to receive the output parameter and return code values.
EXEC @ReturnCode = SampleProcedure @EmployeeIDParm = 19,
   @MaxTotal = @MaxTotalVariable OUTPUT

-- Show the values returned.
PRINT ' '
PRINT 'Return code = ' + CAST(@ReturnCode AS CHAR(10))
PRINT 'Maximum Quantity = ' + CAST(@MaxTotalVariable AS CHAR(10))
GO
```

Per consentire lo scambio di dati tra variabili di applicazione, parametri e codici restituiti, in un'applicazione è possibile utilizzare gli indicatori di parametro associati alle variabili di applicazione.

## <a name="see-also"></a>Vedere anche
[CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)   
 [Sezione Parametri e riutilizzo del piano di esecuzione](../../relational-databases/query-processing-architecture-guide.md)   
 [Variabili (Transact-SQL)](../../t-sql/language-elements/variables-transact-sql.md)