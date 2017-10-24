---
title: SYSUTCDATETIME (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/01/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSUTCDATETIME
- SYSUTCDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- date and time [SQL Server], SYSUTCDATETIME
- SYSUTCDATETIME function [SQL Server]
- time [SQL Server], system
ms.assetid: f14fc2cd-9ea8-4daf-88f4-418cf523ab55
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: b01ce3327bbedb114df93e89fb7c5ee94f5ec58a
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="sysutcdatetime-transact-sql"></a>SYSUTCDATETIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce un **datetime2** valore che contiene la data e ora del computer in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. La data e l'ora viene restituito come ora UTC (Coordinated Universal Time). Le frazioni di secondo specifica precisione dispone di un intervallo da 1 a 7 cifre. La precisione predefinita è 7 cifre.  
  
> [!NOTE]  
>  SYSDATETIME e SYSUTCDATE è maggiore precisione frazionaria dei secondi quella di GETDATE e GETUTCDATE. SYSDATETIMEOFFSET include la differenza di fuso orario del sistema. SYSDATETIME, SYSUTCDATE e SYSDATETIMEOFFSET possono essere assegnati a una variabile di uno qualsiasi dei tipi di data e ora.  
  
 Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [funzioni e tipi di dati ora e data](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SYSUTCDATETIME ( )  
```  
  
## <a name="return-type"></a>Tipo restituito  
 **datetime2**  
  
## <a name="remarks"></a>Sezione Osservazioni  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]le istruzioni possono fare riferimento a SYSUTCDATETIME ovunque possono fare riferimento a un **datetime2** espressione.  
  
 SYSUTCDATETIME è una funzione non deterministica. Viste e le espressioni che fanno riferimento a questa funzione in una colonna non possono essere indicizzate.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Ottiene i valori di data e ora tramite l'API di Windows GetSystemTimeAsFileTime(). La precisione dipende da hardware del computer e versione di Windows in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. La precisione di questa API è pari a 100 nanosecondi. L'accuratezza può essere determinato tramite l'API di Windows GetSystemTimeAdjustment().  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa i sei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzioni di sistema che restituiscono una data corrente e l'ora per restituire la data, ora o entrambi. I valori vengono restituiti in serie. Pertanto, i secondi frazionari potrebbero essere diversi.  
  
### <a name="a-showing-the-formats-that-are-returned-by-the-date-and-time-functions"></a>A. Visualizzazione dei formati restituiti dalle funzioni di data e ora  
 L'esempio seguente mostra i diversi formati restituiti dalle funzioni di data e ora.  
  
```  
SELECT SYSDATETIME() AS SYSDATETIME  
    ,SYSDATETIMEOFFSET() AS SYSDATETIMEOFFSET  
    ,SYSUTCDATETIME() AS SYSUTCDATETIME  
    ,CURRENT_TIMESTAMP AS CURRENT_TIMESTAMP  
    ,GETDATE() AS GETDATE  
    ,GETUTCDATE() AS GETUTCDATE;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
SYSDATETIME()      2007-04-30 13:10:02.0474381
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047
GETDATE()          2007-04-30 13:10:02.047
GETUTCDATE()       2007-04-30 20:10:02.047
```  
  
### <a name="b-converting-date-and-time-to-date"></a>B. Conversione di data e ora in una data  
 Nell'esempio seguente viene illustrato come convertire i valori di data e ora per `date`.  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
```  
  
### <a name="c-converting-date-and-time-values-to-time"></a>C. Conversione dei valori di data e ora di tempo  
 Nell'esempio seguente viene illustrato come convertire i valori di data e ora per `time`.  
  
 ```
DECLARE @DATETIME DATETIME = GetDate();
DECLARE @TIME TIME
SELECT @TIME = CONVERT(time, @DATETIME)
SELECT @TIME AS 'Time', @DATETIME AS 'Date Time'
```
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Time             Date Time  
13:49:33.6330000 2009-04-22 13:49:33.633
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Data e ora funzioni e tipi di &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [FUSO orario &AMP; #40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  



