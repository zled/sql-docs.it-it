---
title: THROW (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- THROW_TSQL
- THROW
dev_langs:
- TSQL
helpviewer_keywords:
- THROW statement
ms.assetid: 43661b89-8f13-4480-ad53-70306cbb14c5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7aff73be9d9213cea3c9336a926a0ad0de0a3c80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803259"
---
# <a name="throw-transact-sql"></a>THROW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Genera un'eccezione e trasferisce l'esecuzione a un blocco CATCH di un costrutto TRY…CATCH in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
THROW [ { error_number | @local_variable },  
        { message | @local_variable },  
        { state | @local_variable } ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *error_number*  
 Costante o variabile che rappresenta l'eccezione. *error_number* è di tipo **int** e deve essere maggiore o uguale a 50000 e minore o uguale a 2147483647.  
  
 *message*  
 Stringa o variabile in cui viene descritta l'eccezione. *message* è di tipo **nvarchar(2048)**.  
  
 *state*  
 Costante o variabile compresa tra 0 e 255 tramite cui viene indicato lo stato da associare al messaggio. *state* è di tipo **tinyint**.  
  
## <a name="remarks"></a>Remarks  
 L'istruzione che precede l'istruzione THROW deve essere seguita dal carattere di terminazione punto e virgola (;).  
  
 Se non è disponibile un costrutto TRY...CATCH, il batch di istruzioni viene terminato. Vengono impostate la procedura e numero di riga in cui viene generata l'eccezione. La gravità viene impostata su 16.  
  
 Se l'istruzione THROW viene specificata senza parametri, è necessario che venga visualizzata in un blocco CATCH. In questo modo verrà generata l'eccezione rilevata. Tutti gli errori che si verificano in un'istruzione THROW causano la terminazione del batch di istruzioni.  
  
 % è un carattere riservato nel testo del messaggio di un'istruzione THROW e deve essere preceduto da un carattere di escape. Raddoppiare il carattere % per restituire % come parte del testo del messaggio, ad esempio "L'aumento ha superato il 15% del valore originale".  
  
## <a name="differences-between-raiserror-and-throw"></a>Differenze tra RAISERROR e THROW  
 Nella tabella seguente vengono elencate le differenze tra le istruzioni RAISERROR e THROW.  
  
|istruzione RAISERROR|Istruzione THROW|  
|-------------------------|---------------------|  
|Se *msg_id* viene passato a RAISERROR, l'ID deve essere definito in sys.messages.|Il parametro *error_number* non deve essere definito in sys.messages.|  
|Il parametro *msg_str* può contenere stili di formattazione **printf**.|Il parametro *message* non accetta stili di formattazione **printf**.|  
|Il parametro *severity* specifica la gravità dell'eccezione.|Non esiste un parametro *severity*. La gravità dell'eccezione viene sempre impostata su 16.|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-throw-to-raise-an-exception"></a>A. Utilizzo di THROW per generare un'eccezione  
 Nell'esempio seguente viene illustrato come utilizzare l'istruzione `THROW` per generare un'eccezione.  
  
```sql  
THROW 51000, 'The record does not exist.', 1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Msg 51000, Level 16, State 1, Line 1  
  
 The record does not exist.
 ```  
  
### <a name="b-using-throw-to-raise-an-exception-again"></a>B. Utilizzo di THROW per generare nuovamente un'eccezione  
 Nell'esempio seguente viene illustrato come utilizzare l'istruzione `THROW` per generare nuovamente l'ultima eccezione generata.  
  
```sql  
USE tempdb;  
GO  
CREATE TABLE dbo.TestRethrow  
(    ID INT PRIMARY KEY  
);  
BEGIN TRY  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
--  Force error 2627, Violation of PRIMARY KEY constraint to be raised.  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
END TRY  
BEGIN CATCH  
  
    PRINT 'In catch block.';  
    THROW;  
END CATCH;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 PRINT 'In catch block.';  
 Msg 2627, Level 14, State 1, Line 1  
 Violation of PRIMARY KEY constraint 'PK__TestReth__3214EC272E3BD7D3'. Cannot insert duplicate key in object 'dbo.TestRethrow'.  
 The statement has been terminated.
 ```  
  
### <a name="c-using-formatmessage-with-throw"></a>C. Utilizzo di FORMATMESSAGE con THROW  
 Nell'esempio seguente viene illustrato come utilizzare la funzione `FORMATMESSAGE` con `THROW` per generare un messaggio di errore personalizzato. Nell'esempio viene prima creato un messaggio di errore definito dall'utente tramite `sp_addmessage`. Poiché l'istruzione THROW non consente parametri di sostituzione nel parametro *message* come invece avviene con RAISERROR, la funzione FORMATMESSAGE viene utilizzata per passare i tre valori dei parametri previsti nel messaggio di errore 60000.  
  
```sql  
EXEC sys.sp_addmessage  
     @msgnum   = 60000  
,@severity = 16  
,@msgtext  = N'This is a test message with one numeric parameter (%d), one string parameter (%s), and another string parameter (%s).'  
    ,@lang = 'us_english';   
GO  
  
DECLARE @msg NVARCHAR(2048) = FORMATMESSAGE(60000, 500, N'First string', N'second string');   
  
THROW 60000, @msg, 1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Msg 60000, Level 16, State 1, Line 2  
 This is a test message with one numeric parameter (500), one string parameter (First string), and another string parameter (second string).
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)   
 [Gravità degli errori del motore di database](../../relational-databases/errors-events/database-engine-error-severities.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [GOTO &#40;Transact-SQL&#41;](../../t-sql/language-elements/goto-transact-sql.md)   
 [BEGIN...END &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [XACT_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/xact-state-transact-sql.md)   
 [SET XACT_ABORT &#40;Transact-SQL&#41;](../../t-sql/statements/set-xact-abort-transact-sql.md)  
  
  

