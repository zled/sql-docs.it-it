---
title: CURSOR_STATUS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURSOR_STATUS
- CURSOR_STATUS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], cursors
- CURSOR_STATUS function
- cursors [SQL Server], status information
ms.assetid: 3a4a840e-04f8-43bd-aada-35d78c3cb6b0
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 764198ef1fd0f5b18985d985be894fcadf8fa3ce
ms.contentlocale: it-it
ms.lasthandoff: 10/12/2017

---
# <a name="cursorstatus-transact-sql"></a>CURSOR_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Funzione scalare che consente al chiamante di una stored procedure di determinare se la procedura ha restituito o meno un cursore e un set di risultati per un determinato parametro.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CURSOR_STATUS   
     (  
          { 'local' , 'cursor_name' }   
          | { 'global' , 'cursor_name' }   
          | { 'variable' , 'cursor_variable' }   
     )  
```  
  
## <a name="arguments"></a>Argomenti  
'local'  
Specifica una costante che indica che l'origine del cursore è un nome di cursore locale.
  
'*cursor_name*'  
Nome del cursore. I nomi di cursore devono essere conformi alle regole per gli identificatori.
  
'global'  
Specifica una costante che indica che l'origine del cursore è un nome di cursore globale.
  
'variable'  
Specifica una costante che indica che l'origine del cursore è una variabile locale.
  
'*cursor_variable*'  
Nome di una variabile cursore. Una variabile di cursore deve essere definita utilizzando il **cursore** tipo di dati.
  
## <a name="return-types"></a>Tipi restituiti
**smallint**
  
|Valore restituito|Nome cursore|Variabile cursore|  
|---|---|---|
|1|Il set di risultati del cursore include almeno una riga.<br /><br /> Nel caso di cursori INSENSITIVE e KEYSET, il set di risultati include almeno una riga.<br /><br /> Nel caso di cursori dinamici, il set di risultati può includere una o più righe oppure nessuna riga.|Il cursore allocato a questa variabile è aperto.<br /><br /> Nel caso di cursori INSENSITIVE e KEYSET, il set di risultati include almeno una riga.<br /><br /> Nel caso di cursori dinamici, il set di risultati può includere una o più righe oppure nessuna riga.|  
|0|Il set di risultati del cursore è vuoto.*|Il cursore allocato a questa variabile è aperto, ma il set di risultati è vuoto.*|  
|-1|Il cursore è chiuso.|Il cursore allocato a questa variabile è chiuso.|  
|-2|Non applicabile.|I possibili valori sono i seguenti:<br /><br /> Tramite la procedura chiamata in precedenza, a questa variabile di OUTPUT non è stato assegnato alcun cursore.<br /><br /> Tramite la procedura chiamata in precedenza, a questa variabile di OUTPUT è stato assegnato un cursore, che tuttavia al completamento della procedura era chiuso. Il cursore viene pertanto deallocato e non viene restituito alla procedura chiamante.<br /><br /> A una variabile cursore dichiarata non è assegnato alcun cursore.|  
|-3|Il cursore specificato non esiste.|La variabile cursore specificata non esiste oppure esiste ma non è ancora stato allocato un cursore.|  
  
* I cursori dinamici non restituiscono mai questo risultato.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene utilizzata la funzione `CURSOR_STATUS` per visualizzare lo stato di un cursore prima e dopo la relativa apertura o chiusura.
  
```sql
CREATE TABLE #TMP  
(  
   ii int  
)  
GO  
  
INSERT INTO #TMP(ii) VALUES(1)  
INSERT INTO #TMP(ii) VALUES(2)  
INSERT INTO #TMP(ii) VALUES(3)  
  
GO  
  
--Create a cursor.  
DECLARE cur CURSOR  
FOR SELECT * FROM #TMP  
  
--Display the status of the cursor before and after opening  
--closing the cursor.  
  
SELECT CURSOR_STATUS('global','cur') AS 'After declare'  
OPEN cur  
SELECT CURSOR_STATUS('global','cur') AS 'After Open'  
CLOSE cur  
SELECT CURSOR_STATUS('global','cur') AS 'After Close'  
  
--Remove the cursor.  
DEALLOCATE cur  
  
--Drop the table.  
DROP TABLE #TMP  
  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
After declare
---------------
-1  
  
After Open
----------
1  
  
After Close
-----------
-1
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni di cursore &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-functions-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

