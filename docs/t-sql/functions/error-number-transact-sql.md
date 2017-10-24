---
title: ERROR_NUMBER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_NUMBER_TSQL
- ERROR_NUMBER
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], numbers
- TRY...CATCH [SQL Server]
- ERROR_NUMBER function
- CATCH block
ms.assetid: 1de85fff-1ca2-4b31-841b-926e571cb150
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: cb65492a3be74474cd5afccdcaf0487d7cbd5167
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="errornumber-transact-sql"></a>ERROR_NUMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il numero dell'errore che ha causato l'esecuzione del blocco CATCH di un costrutto TRY…CATCH.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ERROR_NUMBER ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="return-value"></a>Valore restituito  
 Se chiamata in un blocco CATCH, questa funzione restituisce il numero di errore del messaggio di errore che ha causato l'esecuzione del blocco CATCH.  
  
 Restituisce NULL se chiamata all'esterno dell'ambito di un blocco CATCH.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione può essere chiamata ovunque all'interno dell'ambito di un blocco CATCH.  
  
 ERROR_NUMBER restituisce il numero di errore indipendentemente dal numero di esecuzioni o dalla posizione in cui viene eseguita nell'ambito del blocco CATCH. È in contrasto con@ERROR, che restituisce solo il numero di errore nell'istruzione immediatamente successiva a quella che provoca un errore o bloccare la prima istruzione di un blocco CATCH.  
  
 In blocchi CATCH nidificati, ERROR_NUMBER restituisce il numero di errore specifico dell'ambito del blocco CATCH che include il riferimento alla funzione. Ad esempio, il blocco CATCH di un costrutto esterno TRY...CATCH potrebbe includere un costrutto TRY...CATCH nidificato. Nell'ambito del blocco CATCH nidificato, ERROR_NUMBER restituisce il numero dell'errore che ha richiamato il blocco CATCH nidificato. Se la funzione ERROR_NUMBER viene eseguita nel blocco CATCH esterno, restituisce il numero dell'errore che ha richiamato tale blocco CATCH.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-errornumber-in-a-catch-block"></a>A. Utilizzo di ERROR_NUMBER in un blocco CATCH  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Viene restituito il numero dell'errore.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_NUMBER() AS ErrorNumber;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>B. Utilizzo di ERROR_NUMBER in un blocco CATCH con altri strumenti di gestione degli errori  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Oltre al numero dell'errore vengono restituite informazioni correlate all'errore.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>C. Utilizzo di ERROR_NUMBER in un blocco CATCH con altri strumenti di gestione degli errori  
 Nell'esempio seguente viene illustrata un'istruzione `SELECT` che genera un errore di divisione per zero. Oltre al numero dell'errore vengono restituite informazioni correlate all'errore.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  


