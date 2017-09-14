---
title: RIPRISTINARE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERT_TSQL
- REVERT
dev_langs:
- TSQL
helpviewer_keywords:
- REVERT statement
- context switching [SQL Server], reverting
- reverting execution context
- REVERT WITH COOKIE statement
- execution context [SQL Server]
- COOKIE clause
ms.assetid: 4688b17a-dfd1-4f03-8db4-273a401f879f
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2074ef0a9e434ac5c427c5438633c61ead0eb25a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="revert-transact-sql"></a>REVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Riporta il contesto di esecuzione al chiamante dell'ultima istruzione EXECUTE AS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
REVERT  
    [ WITH COOKIE = @varbinary_variable ]  
```  
  
## <a name="arguments"></a>Argomenti  
 WITH COOKIE = @*varbinary_variable*  
 Specifica il cookie creato in un oggetto corrispondente [EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md) istruzione autonoma. *@varbinary_variable*è **varbinary(100)**.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile specificare REVERT all'interno di un modulo, ad esempio una stored procedure o una funzione definita dall'utente, oppure come un'istruzione autonoma. Se specificata all'interno di un modulo, l'istruzione REVERT è applicabile solo alle istruzioni EXECUTE AS definite nel modulo. Ad esempio, la stored procedure seguente esegue un'istruzione `EXECUTE AS` seguita da un'istruzione `REVERT`.  
  
```  
CREATE PROCEDURE dbo.usp_myproc   
  WITH EXECUTE AS CALLER  
AS   
    SELECT SUSER_NAME(), USER_NAME();  
    EXECUTE AS USER = 'guest';  
    SELECT SUSER_NAME(), USER_NAME();  
    REVERT;  
    SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
 Si supponga che nella sessione in cui viene eseguita la stored procedure il contesto di esecuzione della sessione venga modificato in modo esplicito in `login1`, come illustrato nell'esempio seguente.  
  
```  
  -- Sets the execution context of the session to 'login1'.  
EXECUTE AS LOGIN = 'login1';  
GO  
EXECUTE dbo.usp_myproc;   
```  
  
 L'istruzione `REVERT` definita all'interno di `usp`_`myproc` cambia il contesto di esecuzione impostato all'interno del modulo, ma non quello impostato al suo esterno. In sintesi, il contesto di esecuzione della sessione rimane impostato su `login1`.  
  
 Se specificata come istruzione autonoma, l'istruzione REVERT è applicabile alle istruzioni EXECUTE AS definite all'interno di un batch o una sessione. L'istruzione REVERT non ha alcun effetto se la corrispondente istruzione EXECUTE AS contiene la clausola WITH NO REVERT. In questo caso, il contesto di esecuzione rimane valido fino all'eliminazione della sessione.  
  
## <a name="using-revert-with-cookie"></a>Utilizzo di REVERT WITH COOKIE  
 EXECUTE come istruzione che viene utilizzata per impostare il contesto di esecuzione di una sessione può includere la clausola facoltativa WITH NO REVERT COOKIE = @*varbinary_variabl*e. Quando si esegue questa istruzione, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] passa il cookie a @*varbinary_variabl*e. Il contesto di esecuzione impostato tale istruzione può essere ripristinata al contesto precedente se il chiamante REVERT WITH COOKIE = @*varbinary_variable* istruzione contiene corrette  *@varbinary_variable*  valore.  
  
 Questo meccanismo risulta utile in un ambiente in cui vengono utilizzati pool di connessioni. Tramite i pool di connessioni vengono gestiti i gruppi di connessioni al database in modo che tali connessioni possano essere riutilizzate dalle applicazioni tra più utenti finali. Poiché il valore passato a  *@varbinary_variable*  è noto solo al chiamante dell'EXECUTE come istruzione (in questo caso, l'applicazione), il chiamante può garantire che il contesto di esecuzione stabilito non può essere modificato dall'utente finale che richiama l'applicazione. Dopo il ripristino del contesto di esecuzione l'applicazione può cambiare il contesto a un'altra entità.  
  
## <a name="permissions"></a>Permissions  
 Non sono necessarie autorizzazioni.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-execute-as-and-revert-to-switch-context"></a>A. Utilizzo di EXECUTE AS e REVERT per cambiare contesto  
 Nell'esempio seguente viene creato uno stack di contesti di esecuzione utilizzando più entità. Viene quindi utilizzata l'istruzione REVERT per ripristinare il contesto di esecuzione al chiamante precedente. L'istruzione REVERT viene eseguita più volte per innalzare di livello lo stack finché il contesto di esecuzione viene impostato sul chiamante originale.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create two temporary principals.  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE LOGIN login2 WITH PASSWORD = 'Uor80$23b';  
GO  
CREATE USER user1 FOR LOGIN login1;  
CREATE USER user2 FOR LOGIN login2;  
GO  
-- Give IMPERSONATE permissions on user2 to user1  
-- so that user1 can successfully set the execution context to user2.  
GRANT IMPERSONATE ON USER:: user2 TO user1;  
GO  
-- Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- Set the execution context to login1.   
EXECUTE AS LOGIN = 'login1';  
-- Verify that the execution context is now login1.  
SELECT SUSER_NAME(), USER_NAME();  
-- Login1 sets the execution context to login2.  
EXECUTE AS USER = 'user2';  
-- Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- The execution context stack now has three principals: the originating caller, login1, and login2.  
-- The following REVERT statements will reset the execution context to the previous context.  
REVERT;  
-- Display the current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
REVERT;  
-- Display the current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
  
-- Remove the temporary principals.  
DROP LOGIN login1;  
DROP LOGIN login2;  
DROP USER user1;  
DROP USER user2;  
GO  
```  
  
### <a name="b-using-the-with-cookie-clause"></a>B. Utilizzo della clausola WITH COOKIE  
 Nell'esempio seguente imposta il contesto di esecuzione di una sessione a un utente specificato e specifica di WITH NO REVERT COOKIE = @*varbinary_variabl*clausola. Nell'istruzione `REVERT` è necessario specificare il valore passato alla variabile `@cookie` nell'istruzione `EXECUTE AS` per ripristinare correttamente il contesto al chiamante originale. Per eseguire questo esempio, l'account di accesso `login1` e l'utente `user1` creato nell'esempio A devono esistere.  
  
```  
DECLARE @cookie varbinary(100);  
EXECUTE AS USER = 'user1' WITH COOKIE INTO @cookie;  
-- Store the cookie somewhere safe in your application.  
-- Verify the context switch.  
SELECT SUSER_NAME(), USER_NAME();  
--Display the cookie value.  
SELECT @cookie;  
GO  
-- Use the cookie in the REVERT statement.  
DECLARE @cookie varbinary(100);  
-- Set the cookie value to the one from the SELECT @cookie statement.  
SET @cookie = <value from the SELECT @cookie statement>;  
REVERT WITH COOKIE = @cookie;  
-- Verify the context switch reverted.  
SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ESEGUIRE AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)   
 [Clausola EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [SUSER_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/suser-name-transact-sql.md)   
 [USER_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)  
  
  
