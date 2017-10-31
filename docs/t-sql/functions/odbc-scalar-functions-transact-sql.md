---
title: Funzioni scalari ODBC (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CURDATE ODBC function
- DAYOFMONTH ODBC function
- WEEK ODBC function
- functions, ODBC CONCAT
- SECOND ODBC function
- functions, ODBC CURRENT_TIME
- functions, ODBC HOUR
- functions, ODBC QUARTER
- TRUNCATE ODBC function
- functions, ODBC SECOND
- DAYOFWEEK ODBC function
- CURRENT_DATE ODBC function
- DAYNAME ODBC function
- CURTIME ODBC function
- functions, ODBC CURRENT_DATE
- MINUTE ODBC function
- functions, ODBC BIT_LENGTH
- functions, ODBC OCTET_LENGTH
- CONCAT ODBC function
- MONTHNAME ODBC function
- functions, ODBC DAYOFYEAR
- OCTET_LENGTH ODBC function
- functions [SQL Server], ODBC scalar functions
- BIT_LENGTH ODBC function
- functions, ODBC DAYOFMONTH
- CURRENT_TIME ODBC function
- functions, ODBC CURDATE
- functions, ODBC CURTIME
- functions, ODBC TRUNCATE
- functions, ODBC MONTHNAME
- functions, ODBC DAYNAME
- ODBC scalar functions
- functions, ODBC MINUTE
- functions, ODBC DAYOFWEEK
- QUARTER ODBC function
- DAYOFYEAR ODBC function
- functions, ODBC WEEK
- HOUR ODBC function
ms.assetid: a0df1ac2-6699-4ac0-8f79-f362f23496f1
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b248e52c25e3c4a7cdbb0e52b1df50623e048189
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="odbc-scalar-functions-transact-sql"></a>Funzioni scalari ODBC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  È possibile utilizzare [funzioni scalari ODBC](http://go.microsoft.com/fwlink/?LinkID=88579) in [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni. Queste istruzioni sono interpretate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed è possibile utilizzarle in stored procedure e funzioni definite dall'utente. Queste includono funzioni per i valori stringa, numerici, di ora, di data, di intervallo e di sistema.  
  
## <a name="usage"></a>Utilizzo  
 `SELECT {fn <function_name> [ (<argument>,....n) ] }`  
  
## <a name="functions"></a>Funzioni  
 Nelle tabelle seguenti sono elencate le funzioni scalari ODBC non duplicate in [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
### <a name="string-functions"></a>Funzioni per i valori stringa  
  
|Funzione|Description|  
|--------------|-----------------|  
|BIT_LENGTH(string_exp) (ODBC 3.0)|Restituisce la lunghezza in bit dell'espressione stringa.<br /><br /> Non funziona solo per i dati di tipo stringa. Pertanto, non converte implicitamente string_exp in una stringa ma restituisce le dimensioni interne del tipo di dati fornito.|  
|CONCAT( string_exp1,string_exp2) (ODBC 1.0)|Restituisce la stringa di caratteri che risulta dalla concatenazione di string_exp2 e string_exp1. La stringa risultante dipende da DBMS. Ad esempio, se la colonna rappresentata string_exp1 contiene un valore NULL, DB2 restituisce NULL ma [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce una stringa non Null.|  
|OCTET_LENGTH( string_exp ) (ODBC 3.0)|Restituisce la lunghezza in byte dell'espressione stringa. Il risultato è il più piccolo numero integer non inferiore al numero di bit diviso per 8.<br /><br /> Non funziona solo per i dati di tipo stringa. Pertanto, non converte implicitamente string_exp in una stringa ma restituisce le dimensioni interne del tipo di dati fornito.|  
  
### <a name="numeric-function"></a>Funzione numerica  
  
|Funzione|Description|  
|--------------|-----------------|  
|TRUNCATE( numeric_exp, integer_exp) (ODBC 2.0)|Restituisce numeric_exp troncato in corrispondenza di un numero di posizioni pari a integer_exp a destra del separatore decimale. Se integer_exp è negativo, numeric_exp viene troncato a &#124; integer_exp &#124; posizioni a sinistra del separatore decimale.|  
  
### <a name="time-date-and-interval-functions"></a>Funzioni di data, ora e intervallo  
  
|Funzione|Description|  
|--------------|-----------------|  
|CURRENT_DATE( ) (ODBC 3.0)|Restituisce la data corrente.|  
|CURDATE( ) (ODBC 3.0)|Restituisce la data corrente.|  
|CURRENT_TIME`[( time-precision )]` (ODBC 3.0)|Restituisce l'ora locale corrente. L'argomento time-precision determina la precisione a livello di secondi del valore restituito.|  
|CURTIME() (ODBC 3.0)|Restituisce l'ora locale corrente.|  
|DAYNAME( date_exp ) (ODBC 2.0)|Restituisce una stringa di caratteri che contiene il nome, specifico dell'origine dati, del giorno (ad esempio, da Sunday a Saturday o da Sun a Sat per un'origine dati che utilizza l'inglese o da lunedì a domenica per un'origine dati che utilizza l'italiano) per la parte relativa al giorno dell'argomento date_exp.|  
|DAYOFMONTH( date_exp ) (ODBC 1.0)|Restituisce il giorno del mese in base al campo del mese in date_exp come valore intero nell'intervallo da 1 a 31.|  
|DAYOFWEEK( date_exp ) (ODBC 1.0)|Restituisce il giorno della settimana in base al campo della settimana in date_exp come valore intero nell'intervallo da 1 a 7, dove 1 corrisponde al lunedì.|  
|HOUR( time_exp ) (ODBC 1.0)|Restituisce l'ora in base al campo dell'ora in time_exp come valore intero nell'intervallo da 0 a 23.|  
|MINUTE( time_exp ) (ODBC 1.0)|Restituisce i minuti in base al campo dei minuti in time_exp come valore intero nell'intervallo da 0 a 59.|  
|SECOND( time_exp ) (ODBC 1.0)|Restituisce i secondi in base al campo dei secondi in time_exp come valore intero nell'intervallo da 0 a 59.|  
|MONTHNAME( date_exp ) (ODBC 2.0)|Restituisce una stringa di caratteri che contiene il nome, specifico dell'origine dati, del mese (ad esempio, da January a December o da Jan a Dec per un'origine dati che utilizza l'inglese o da gennaio a dicembre per un'origine dati che utilizza l'italiano) per la parte relativa al mese dell'argomento date_exp.|  
|QUARTER( date_exp ) (ODBC 1.0)|Restituisce il trimestre relativo a date_exp come valore intero nell'intervallo da 1 a 4, dove 1 corrisponde al periodo 1 gennaio-31 marzo.|  
|WEEK( date_exp ) (ODBC 1.0)|Restituisce la settimana dell'anno in base al campo della settimana in date_exp come valore intero nell'intervallo da 1 a 53.|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-an-odbc-function-in-a-stored-procedure"></a>A. Utilizzo di una funzione ODBC in una stored procedure  
 Nell'esempio seguente viene utilizzata una funzione ODBC in una stored procedure:  
  
```  
CREATE PROCEDURE dbo.ODBCprocedure  
    (  
    @string_exp nvarchar(4000)  
    )  
AS  
SELECT {fn OCTET_LENGTH( @string_exp )};  
```  
  
### <a name="b-using-an-odbc-function-in-a-user-defined-function"></a>B. Utilizzo di una funzione ODBC in una funzione definita dall'utente  
 Nell'esempio seguente viene utilizzata una funzione ODBC in una funzione definita dall'utente:  
  
```  
CREATE FUNCTION dbo.ODBCudf  
    (  
    @string_exp nvarchar(4000)  
    )  
RETURNS int  
AS  
BEGIN  
DECLARE @len int  
SET @len = (SELECT {fn OCTET_LENGTH( @string_exp )})  
RETURN(@len)  
END ;  
  
SELECT dbo.ODBCudf('Returns the length.');  
--Returns 38  
  
```  
  
### <a name="c-using-an-odbc-functions-in-select-statements"></a>C. Utilizzo di funzioni ODBC nelle istruzioni SELECT  
 Nella seguente istruzione SELECT vengono utilizzate funzioni ODBC:  
  
```  
DECLARE @string_exp nvarchar(4000) = 'Returns the length.';  
SELECT {fn BIT_LENGTH( @string_exp )};  
-- Returns 304  
SELECT {fn OCTET_LENGTH( @string_exp )};  
-- Returns 38  
  
SELECT {fn CONCAT( 'CONCAT ','returns a character string')};  
-- Returns CONCAT returns a character string  
SELECT {fn TRUNCATE( 100.123456, 4)};  
-- Returns 100.123400  
SELECT {fn CURRENT_DATE( )};  
-- Returns 2007-04-20  
SELECT {fn CURRENT_TIME(6)};  
-- Returns 10:27:11.973000  
  
DECLARE @date_exp nvarchar(30) = '2007-04-21 01:01:01.1234567';  
SELECT {fn DAYNAME( @date_exp )};  
-- Returns Saturday  
SELECT {fn DAYOFMONTH( @date_exp )};  
-- Returns 21  
SELECT {fn DAYOFWEEK( @date_exp )};  
-- Returns 7  
SELECT {fn HOUR( @date_exp)};  
-- Returns 1   
SELECT {fn MINUTE( @date_exp )};  
-- Returns 1  
SELECT {fn SECOND( @date_exp )};  
-- Returns 1  
SELECT {fn MONTHNAME( @date_exp )};  
-- Returns April  
SELECT {fn QUARTER( @date_exp )};  
-- Returns 2  
SELECT {fn WEEK( @date_exp )};  
-- Returns 16  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-an-odbc-function-in-a-stored-procedure"></a>D. Utilizzo di una funzione ODBC in una stored procedure  
 Nell'esempio seguente viene utilizzata una funzione ODBC in una stored procedure:  
  
```  
CREATE PROCEDURE dbo.ODBCprocedure  
    (  
    @string_exp nvarchar(4000)  
    )  
AS  
SELECT {fn BIT_LENGTH( @string_exp )};  
```  
  
### <a name="e-using-an-odbc-function-in-a-user-defined-function"></a>E. Utilizzo di una funzione ODBC in una funzione definita dall'utente  
 Nell'esempio seguente viene utilizzata una funzione ODBC in una funzione definita dall'utente:  
  
```  
CREATE FUNCTION dbo.ODBCudf  
    (  
    @string_exp nvarchar(4000)  
    )  
RETURNS int  
AS  
BEGIN  
DECLARE @len int  
SET @len = (SELECT {fn BIT_LENGTH( @string_exp )})  
RETURN(@len)  
END ;  
  
SELECT dbo.ODBCudf('Returns the length in bits.');  
--Returns 432  
  
```  
  
### <a name="f-using-an-odbc-functions-in-select-statements"></a>F. Utilizzo di funzioni ODBC nelle istruzioni SELECT  
 Nella seguente istruzione SELECT vengono utilizzate funzioni ODBC:  
  
```  
DECLARE @string_exp nvarchar(4000) = 'Returns the length.';  
SELECT {fn BIT_LENGTH( @string_exp )};  
-- Returns 304  
  
SELECT {fn CONCAT( 'CONCAT ','returns a character string')};  
-- Returns CONCAT returns a character string  
SELECT {fn CURRENT_DATE( )};  
-- Returns todays date  
SELECT {fn CURRENT_TIME(6)};  
-- Returns the time  
  
DECLARE @date_exp nvarchar(30) = '2007-04-21 01:01:01.1234567';  
SELECT {fn DAYNAME( @date_exp )};  
-- Returns Saturday  
SELECT {fn DAYOFMONTH( @date_exp )};  
-- Returns 21  
SELECT {fn DAYOFWEEK( @date_exp )};  
-- Returns 7  
SELECT {fn HOUR( @date_exp)};  
-- Returns 1   
SELECT {fn MINUTE( @date_exp )};  
-- Returns 1  
SELECT {fn SECOND( @date_exp )};  
-- Returns 1  
SELECT {fn MONTHNAME( @date_exp )};  
-- Returns April  
SELECT {fn QUARTER( @date_exp )};  
-- Returns 2  
SELECT {fn WEEK( @date_exp )};  
-- Returns 16  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  




