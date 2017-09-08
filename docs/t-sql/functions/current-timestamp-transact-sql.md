---
title: CURRENT_TIMESTAMP (Transact-SQL) | Documenti Microsoft
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
- CURRENT_TIMESTAMP
- CURRENT_TIMESTAMP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- niladic functions
- current date and time [SQL Server]
- time [SQL Server], current
- date and time [SQL Server], CURRENT_TIMESTAMP
- functions [SQL Server], time
- system date and time [SQL Server]
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- dates [SQL Server], system date and time
- CURRENT_TIMESTAMP function [SQL Server]
- time [SQL Server], system
ms.assetid: c724d9cc-7b1f-4c71-bdf5-08bc52b33afc
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0a9896ac36bbcfa34cb2697634445dcc2a77cfa2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="currenttimestamp-transact-sql"></a>CURRENT_TIMESTAMP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il timestamp di sistema di database corrente come un **datetime** valore senza differenza di fuso orario del database. Questo valore deriva dal sistema operativo del computer in cui è in esecuzione l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
> [!NOTE]  
>  La precisione in secondi frazionari di SYSDATETIME e SYSUTCDATE è maggiore di quella di GETDATE e GETUTCDATE. SYSDATETIMEOFFSET include la differenza di fuso orario di sistema. SYSDATETIME, SYSUTCDATE e SYSDATETIMEOFFSET possono essere assegnate a una variabile di qualsiasi tipo di data e ora.  
  
Questa funzione è l'equivalente di ANSI SQL [GETDATE](../../t-sql/functions/getdate-transact-sql.md).
  
Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [funzioni e tipi di dati ora e data](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
CURRENT_TIMESTAMP  
```  
  
## <a name="arguments"></a>Argomenti  
Questa istruzione non accetta argomenti.
  
## <a name="return-type"></a>Tipo restituito  
**datetime**
  
## <a name="remarks"></a>Osservazioni  
[!INCLUDE[tsql](../../includes/tsql-md.md)]le istruzioni possono fare riferimento a CURRENT_TIMESTAMP ovunque possono fare riferimento a un **datetime** espressione.
  
CURRENT_TIMESTAMP è una funzione non deterministica. Le viste e le espressioni in cui viene fatto riferimento a questa colonna non sono indicizzabili.
  
## <a name="examples"></a>Esempi  
Negli esempi seguenti sono utilizzate le sei funzioni di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che restituiscono data e ora corrente per restituire la data, l'ora o entrambe. I valori sono restituiti in serie. Pertanto, i secondi frazionari potrebbero essere diversi.
  
### <a name="a-get-the-current-system-date-and-time"></a>A. Recupero della data e dell'ora correnti del sistema  
  
```sql
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
```  
  
### <a name="b-get-the-current-system-date"></a>B. Recupero della data corrente del sistema  
  
```sql
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
  
/* Returned   
SYSDATETIME()      2007-05-03  
SYSDATETIMEOFFSET()2007-05-03  
SYSUTCDATETIME()   2007-05-04  
CURRENT_TIMESTAMP  2007-05-03  
GETDATE()          2007-05-03  
GETUTCDATE()       2007-05-04  
*/  
```  
  
### <a name="c-get-the-current-system-time"></a>C. Recupero dell'ora corrente del sistema  
  
```sql
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
  
```sql
SELECT CURRENT_TIMESTAMP;  
```  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


