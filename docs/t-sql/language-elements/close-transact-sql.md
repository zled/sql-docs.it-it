---
title: CLOSE (Transact-SQL) | Documenti Microsoft
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
- CLOSE_TSQL
- CLOSE
dev_langs:
- TSQL
helpviewer_keywords:
- closing cursors
- cursors [SQL Server], closing
- CLOSE statement
ms.assetid: 21546874-97e3-4b93-970f-87c27f6b78c7
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7315b45fa3b13b96fa01c7833ed1370f72e4bab8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="close-transact-sql"></a>CLOSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Chiude un cursore aperto rilasciando il set di risultati corrente e liberando i blocchi dei cursori mantenuti attivi sulle righe in cui è posizionato il cursore. L'istruzione CLOSE mantiene le strutture dei dati disponibili per successive operazioni di apertura. Le operazioni di recupero e di aggiornamento posizionato, tuttavia, sono consentite solo dopo la riapertura del cursore. È necessario eseguire l'istruzione CLOSE su un cursore aperto. L'esecuzione non è consentita su cursori solo dichiarati o già chiusi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CLOSE { { [ GLOBAL ] cursor_name } | cursor_variable_name }  
```  
  
## <a name="arguments"></a>Argomenti  
 GLOBAL  
 Specifica che *cursor_name* fa riferimento a un cursore globale.  
  
 *cursor_name*  
 Nome di un cursore aperto. Se sono presenti sia globale e un cursore locale con *cursor_name* per il proprio nome, *cursor_name* fa riferimento il cursore globale quando globale è specificata; in caso contrario, *cursor_name* fa riferimento al cursore locale.  
  
 *cursor_variable_name*  
 Nome di una variabile di cursore associata a un cursore aperto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata la posizione corretta dell'istruzione `CLOSE` in un processo basato su cursori.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT EmployeeID, Title FROM AdventureWorks2012.HumanResources.Employee;  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Cursori](../../relational-databases/cursors.md)   
 [Cursori &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DEALLOCARE &#40; Transact-SQL &#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [Operazione di recupero &#40; Transact-SQL &#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [Apri &#40; Transact-SQL &#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  

