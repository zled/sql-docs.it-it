---
title: ORIGINAL_LOGIN (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ORIGINAL_LOGIN_TSQL
- ORIGINAL_LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], context switches
- context switching [SQL Server], login names
- original login names [SQL Server]
- ORIGINAL_LOGIN function
- names [SQL Server], logins
ms.assetid: ddfb0991-cde3-4b97-a5b7-ee450133f160
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1f97da47505e5c812e43f4481d9f36027bf14c9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="originallogin-transact-sql"></a>ORIGINAL_LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il nome dell'account di accesso utilizzato per la connessione all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile utilizzare questa funzione per restituire l'identità dell'account di accesso originale in sessioni in cui si verificano numerosi cambi di contesto espliciti o impliciti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ORIGINAL_LOGIN( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **sysname**  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione può essere utile per il controllo dell'identità del contesto di connessione originale. Mentre le funzioni come [SESSION_USER](../../t-sql/functions/session-user-transact-sql.md) e [CURRENT_USER](../../t-sql/functions/current-user-transact-sql.md) restituito il contesto di esecuzione corrente, ORIGINAL_LOGIN restituisce l'identità dell'account di accesso prima di tutto è connessa all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in tale sessione.  
  
 Restituisce NULL in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il contesto di esecuzione della sessione corrente viene cambiato dal chiamante delle istruzioni in `login1`. Le funzioni `SUSER_SNAME` e `ORIGINAL_LOGIN` vengono utilizzate per restituire rispettivamente l'utente della sessione corrente, ovvero l'utente su cui è stato impostato il contesto, e l'account di accesso originale.  
  
```  
USE AdventureWorks2012;  
GO  
--Create a temporary login and user.  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE USER user1 FOR LOGIN login1;  
GO  
--Execute a context switch to the temporary login account.  
DECLARE @original_login sysname;  
DECLARE @current_context sysname;  
EXECUTE AS LOGIN = 'login1';  
SET @original_login = ORIGINAL_LOGIN();  
SET @current_context = SUSER_SNAME();  
SELECT 'The current executing context is: '+ @current_context;  
SELECT 'The original login in this session was: '+ @original_login  
GO  
-- Return to the original execution context  
-- and remove the temporary principal.  
REVERT;  
GO  
DROP LOGIN login1;  
DROP USER user1;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ESEGUIRE AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)   
 [Ripristina &#40; Transact-SQL &#41;](../../t-sql/statements/revert-transact-sql.md)  
  
  
