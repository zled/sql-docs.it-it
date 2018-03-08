---
title: '@@FETCH_STATUS (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@FETCH_STATUS'
- '@@FETCH_STATUS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- status information [SQL Server], FETCH
- '@@FETCH_STATUS function'
ms.assetid: 93659193-e4ff-4dfb-9043-0c4114921b91
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9bc4027eb6be9d79599cb06f7935bd2d052bb2a2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40fetchstatus-transact-sql"></a>&#x40;&#x40;FETCH_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce lo stato dell'ultima istruzione FETCH eseguita su qualsiasi cursore attualmente aperto dalla connessione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@@FETCH_STATUS  
```  
  
## <a name="return-type"></a>Tipo restituito  
 **integer**  
  
## <a name="return-value"></a>Valore restituito  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0|L'istruzione FETCH ha avuto esito positivo.|  
|-1|L'istruzione FETCH ha avuto esito negativo oppure la riga non è compresa nel set di risultati.|  
|-2|La riga recuperata è mancante.|
|-9|Il cursore non sta eseguendo un'operazione di recupero.|  
  
## <a name="remarks"></a>Osservazioni  
 Poiché @@FETCH_STATUS è globale per tutti i cursori in una connessione, utilizzare @@FETCH_STATUS con attenzione. Dopo l'esecuzione di un'istruzione FETCH, il test per @@FETCH_STATUS deve verificarsi prima che qualsiasi altra istruzione FETCH viene eseguita su un altro cursore. Il valore di @@FETCH_STATUS prima di operazioni di recupero si sono verificati per la connessione non è definito.  
  
 Un utente, ad esempio, può eseguire un'istruzione FETCH da un cursore e richiamare quindi una stored procedure che apre ed elabora i risultati di un altro cursore. Quando il controllo viene restituito dalla stored procedure chiamata, @@FETCH_STATUS riflette l'ultima istruzione FETCH eseguita nella stored procedure, non l'istruzione FETCH eseguita prima che venga chiamata la stored procedure.  
  
 Per recuperare l'ultimo stato di un cursore specifico, eseguire una query di **fetch_status** colonna il **Sys.dm exec_cursors** funzione a gestione dinamica.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata la funzione `@@FETCH_STATUS` per controllare le attività del cursore in un ciclo `WHILE`.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT BusinessEntityID, JobTitle  
FROM AdventureWorks2012.HumanResources.Employee;  
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
 [Funzioni per i cursori &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md)   
 [Operazione di recupero &#40; Transact-SQL &#41;](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  
