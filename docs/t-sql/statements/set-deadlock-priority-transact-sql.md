---
title: SET DEADLOCK_PRIORITY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET DEADLOCK_PRIORITY
- DEADLOCK_PRIORITY_TSQL
- SET_DEADLOCK_PRIORITY_TSQL
- DEADLOCK_PRIORITY
dev_langs:
- TSQL
helpviewer_keywords:
- deadlocks [SQL Server], priority settings
- DEADLOCK_PRIORITY option
- locking [SQL Server], deadlocks
- priority deadlock settings [SQL Server]
- SET DEADLOCK_PRIORITY statement
ms.assetid: 810a3a8e-3da3-4bf9-bb15-7b069685a1b6
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 12be78ffb2e899170095415a03dccc69511f7424
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-deadlockpriority-transact-sql"></a>SET DEADLOCK_PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Specifica la priorità relativa della sessione corrente nel caso in cui venga coinvolta in un deadlock con un'altra sessione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET DEADLOCK_PRIORITY { LOW | NORMAL | HIGH | <numeric-priority> | @deadlock_var | @deadlock_intvar }  
  
<numeric-priority> ::= { -10 | -9 | -8 | … | 0 | … | 8 | 9 | 10 }  
```  
  
## <a name="arguments"></a>Argomenti  
 LOW  
 Specifica che la sessione corrente sarà vittima del deadlock se coinvolta in un deadlock e se la priorità di deadlock delle altre sessioni coinvolte nella catena del deadlock è impostata su NORMAL o HIGH o su un valore integer maggiore di -5. Se le altre sessioni dispongono di una priorità di deadlock impostata su un valore intero minore di -5, la sessione corrente non sarà vittima del deadlock. Specifica inoltre che la sessione corrente può essere vittima del deadlock se un'altra sessione dispone di una priorità di deadlock impostata su LOW o su un valore intero uguale a -5.  
  
 NORMAL  
 Specifica che la sessione corrente sarà vittima del deadlock se la priorità di deadlock delle altre sessioni coinvolte nella catena del deadlock è impostata su HIGH o su un valore integer maggiore di 0, ma non sarà tale se la priorità di deadlock delle altre sessioni è impostata su LOW o su un valore integer minore di 0. Specifica inoltre che la sessione corrente può essere vittima del deadlock se un'altra sessione dispone di una priorità di deadlock impostata su NORMAL o su un valore intero uguale a 0. Il valore predefinito è NORMAL.  
  
 HIGH  
 Specifica che la sessione corrente sarà vittima del deadlock se la priorità di deadlock delle altre sessioni coinvolte nella catena del deadlock è impostata su un valore intero maggiore di 5 oppure che può essere scelta come vittima del deadlock se la priorità di deadlock di un'altra sessione è anch'essa impostata su HIGH o su un valore intero uguale a 5.  
  
 \<priorità numerica >  
 Intervallo di valori interi (da -10 a 10) per fornire 21 livelli di priorità del deadlock. Specifica che la sessione corrente sarà vittima del deadlock se altre sessioni della catena del deadlock vengono eseguite con una priorità di deadlock maggiore, ma non sarà vittima del deadlock se le altre sessioni vengono eseguite con la priorità di deadlock impostata su un valore minore di quello della sessione corrente. Specifica inoltre che la sessione corrente può essere vittima del deadlock se un'altra sessione viene eseguita con una priorità di deadlock uguale a quella della sessione corrente. LOW corrisponde a -5, NORMAL a 0 e HIGH a 5.  
  
 **@***deadlock_var*  
 Variabile di tipo carattere che specifica la priorità del deadlock. La variabile deve essere impostata su uno dei valori seguenti: 'LOW', 'NORMAL' o 'HIGH'. Le dimensioni della variabili devono essere tali da contenere l'intera stringa.  
  
 **@***deadlock_intvar*  
 Variabile di tipo integer che specifica la priorità del deadlock. La variabile deve essere impostata su un valore intero compreso nell'intervallo (da -10 a 10).  
  
## <a name="remarks"></a>Osservazioni  
 Il deadlock si verifica quando due sessioni sono entrambe in attesa di accedere a risorse bloccate dall'altra sessione. Quando un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rileva che due sessioni sono coinvolte in un deadlock, risolve il deadlock scegliendo una delle sessioni come vittima del deadlock. Viene eseguito il rollback della transazione corrente della sessione vittima del deadlock e al client viene restituito il messaggio di errore relativo al deadlock 1205. In questo modo tutti i blocchi della sessione vengono rilasciati e l'altra sessione può proseguire.  
  
 La scelta della sessione che sarà vittima del deadlock dipende dalla priorità di deadlock delle sessioni:  
  
-   Se entrambe le sessioni hanno la stessa priorità di deadlock, l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sceglie come vittima del deadlock la sessione per cui risulta meno oneroso eseguire il rollback. Se, ad esempio, la priorità di deadlock di entrambe le sessioni è impostata su HIGH, l'istanza sceglierà come vittima la sessione per cui ritiene che sia meno oneroso eseguire il rollback.  
  
-   Se le priorità di deadlock delle sessioni sono diverse, come vittima del deadlock verrà scelta la sessione con la priorità di deadlock inferiore.  
  
 L'opzione SET DEADLOCK_PRIORITY viene impostata in fase di esecuzione, non in fase di analisi.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata una variabile per impostare la priorità di deadlock su `LOW`.  
  
```  
DECLARE @deadlock_var NCHAR(3);  
SET @deadlock_var = N'LOW';  
  
SET DEADLOCK_PRIORITY @deadlock_var;  
GO  
```  
  
 Nell'esempio seguente la priorità di deadlock viene impostata su `NORMAL`.  
  
```  
SET DEADLOCK_PRIORITY NORMAL;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [@@LOCK_TIMEOUT &#40;Transact-SQL&#41;](../../t-sql/functions/lock-timeout-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET LOCK_TIMEOUT &#40; Transact-SQL &#41;](../../t-sql/statements/set-lock-timeout-transact-sql.md)  
  
  

