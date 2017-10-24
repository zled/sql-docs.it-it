---
title: SYSDATETIME (Transact-SQL) | Documenti Microsoft
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
- SYSDATETIME_TSQL
- SYSDATETIME
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], SYSDATETIME
- current date and time [SQL Server]
- functions [SQL Server], time
- system date and time [SQL Server]
- system time [SQL Server]
- SYSDATETIME function [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- dates [SQL Server], system date and time
- time [SQL Server], system
ms.assetid: cba4999e-a9d4-4742-abc9-4a4f109206b6
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e199d8438ca39ead6e9c299925ba83edd6be7ef5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="sysdatetime-transact-sql"></a>SYSDATETIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce un **datetime2 (7)** valore che contiene la data e ora del computer in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione.  
  
> [!NOTE]  
>  La precisione in secondi frazionari di SYSDATETIME e SYSUTCDATETIME è maggiore di quella di GETDATE e GETUTCDATE. SYSDATETIMEOFFSET include la differenza di fuso orario di sistema. SYSDATETIME, SYSUTCDATETIME e SYSDATETIMEOFFSET possono essere assegnate a una variabile di qualsiasi tipo di data e ora.  
  
 Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SYSDATETIME ( )  
```  
  
## <a name="return-type"></a>Tipo restituito  
 **datetime2(7)**  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]le istruzioni possono fare riferimento a SYSDATETIME ovunque possono fare riferimento a un **datetime2 (7)** espressione.  
  
 SYSDATETIME è una funzione non deterministica. Le viste e le espressioni che fanno riferimento a questa funzione in una colonna non sono indicizzabili.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Ottiene i valori di data e ora tramite l'API di Windows GetSystemTimeAsFileTime(). L'accuratezza dipende dall'hardware e dalla versione di Windows del computer in cui è in esecuzione l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La precisione di tale API è fissata sul valore di 100 nanosecondi. L'accuratezza può essere determinato tramite l'API di Windows GetSystemTimeAdjustment().  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti sono utilizzate le sei funzioni di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che restituiscono data e ora corrente per restituire la data, l'ora o entrambe. I valori sono restituiti in serie. Pertanto, i secondi frazionari potrebbero essere diversi.  
  
### <a name="a-getting-the-current-system-date-and-time"></a>A. Recupero della data e dell'ora correnti del sistema  
  
```  
SELECT SYSDATETIME()  
    ,SYSDATETIMEOFFSET()  
    ,SYSUTCDATETIME()  
    ,CURRENT_TIMESTAMP  
    ,GETDATE()  
    ,GETUTCDATE();  
/* Returned:  
SYSDATETIME()      2007-04-30 13:10:02.0474381  
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00  
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381  
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047  
GETDATE()          2007-04-30 13:10:02.047  
GETUTCDATE()       2007-04-30 20:10:02.047  
*/
```    
  
### <a name="b-getting-the-current-system-date"></a>B. Recupero della data corrente del sistema  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
  
/* All returned 2007-04-30 */  
```  
  
### <a name="c-getting-the-current-system-time"></a>C. Recupero dell'ora corrente del sistema  
  
```  
SELECT CONVERT (time, SYSDATETIME())  
    ,CONVERT (time, SYSDATETIMEOFFSET())  
    ,CONVERT (time, SYSUTCDATETIME())  
    ,CONVERT (time, CURRENT_TIMESTAMP)  
    ,CONVERT (time, GETDATE())  
    ,CONVERT (time, GETUTCDATE());  
  
/* Returned  
SYSDATETIME()      13:18:45.3490361  
SYSDATETIMEOFFSET()13:18:45.3490361  
SYSUTCDATETIME()   20:18:45.3490361  
CURRENT_TIMESTAMP  13:18:45.3470000  
GETDATE()          13:18:45.3470000  
GETUTCDATE()       20:18:45.3470000  
*/  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-getting-the-current-system-date-and-time"></a>Unità d: recupero di la data corrente del sistema e dell'ora  
  
```  
SELECT SYSDATETIME();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
--------------------------  
7/20/2013 2:49:59 PM
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Data e ora funzioni e tipi di &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)  
  
  


