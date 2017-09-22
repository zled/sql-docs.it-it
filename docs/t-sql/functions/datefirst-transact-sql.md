---
title: '@@DATEFIRST (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATE_FORMAT_TSQL
- DATE FORMAT
- '@@DATEFIRST_TSQL'
- '@@DATEFIRST'
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], SET DATEFIRST
- first day of week [SQL Server]
- dates [SQL Server], first day of week
- day of week [SQL Server]
- SET DATEFIRST option [SQL Server]
- date and time [SQL Server], DATEFIRST
- DATEFIRST option [SQL Server]
- date and time [SQL Server], @@DATEFIRST
- weekdays [SQL Server]
- '@@DATEFIRST function [SQL Server]'
- functions [SQL Server], date and time
- options [SQL Server], date
ms.assetid: a178868e-49d5-4bd5-a5e2-1283409c8ce6
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 2dfe63f2d59cb3e3a1b563d524693af0d3dd1b51
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40datefirst-transact-sql"></a>& #x 40; & #x 40; DATEFIRST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il valore corrente, per una sessione, di [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni & #40; Transact-SQL & #41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```
@@DATEFIRST  
```  
  
## <a name="return-type"></a>Tipo restituito  
**tinyint**
  
## <a name="remarks"></a>Osservazioni  
SET DATEFIRST specifica il primo giorno della settimana. L'impostazione predefinita per la lingua Inglese Stati Uniti è 7, ovvero la domenica.
  
Questa impostazione relativa alla lingua influisce sull'interpretazione di stringhe di caratteri, nel momento in cui queste vengono convertite in valori di data per l'archiviazione nel database, e sulla visualizzazione sui valori di data archiviati nel database. Questa impostazione non influisce sul formato di archiviazione dei dati relativi alla data. Nell'esempio seguente la lingua viene innanzitutto impostata su `Italian`. L'istruzione `SELECT @@DATEFIRST;` restituisce `1`. La lingua viene quindi impostata su `us_english`. L'istruzione `SELECT @@DATEFIRST;` restituisce `7`.
  
```sql
SET LANGUAGE Italian;  
GO  
SELECT @@DATEFIRST;  
GO  
SET LANGUAGE us_english;  
GO  
SELECT @@DATEFIRST;  
```  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente il primo giorno della settimana viene impostato su `5` (venerdì) e viene presupposto che il giorno corrente, `Today`, sia sabato. L'istruzione `SELECT` restituisce il valore di `DATEFIRST` e il numero del giorno corrente della settimana.
  
```sql
SET DATEFIRST 5;  
SELECT @@DATEFIRST AS 'First Day'  
    ,DATEPART(dw, SYSDATETIME()) AS 'Today';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
First Day         Today  
----------------  --------------  
5                 2  
```  
  
## <a name="example"></a>Esempio
 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT @@DATEFIRST;  
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni di configurazione & #40; Transact-SQL & #41;](../../t-sql/functions/configuration-functions-transact-sql.md)
  
  


