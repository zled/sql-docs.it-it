---
title: DAY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 471aee08a98273f8fe44b599de4c877d40226d16
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce un valore integer che rappresenta il giorno (giorno del mese) del tipo di dati *date* specificato.
  
Per una panoramica di tutti i tipi di dati e delle funzioni di data e ora [!INCLUDE[tsql](../../includes/tsql-md.md)], vedere [Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Argomenti  
*data*  
Espressione che può essere risolta in un valore **time**, **date**, **smalldatetime**, **datetime**, **datetime2** o **datetimeoffset**. L'argomento *date* può essere costituito da un'espressione, un'espressione di colonna, una variabile definita dall'utente o un valore letterale stringa.
  
## <a name="return-type"></a>Tipo restituito  
**int**
  
## <a name="return-value"></a>Valore restituito  
DAY restituisce lo stesso valore di [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**day**, *date*).
  
Se *date* contiene solo una parte dell'ora, il valore restituito è 1, il giorno di base.
  
## <a name="examples"></a>Esempi  
L'istruzione seguente restituisce `30`. Si tratta del numero del giorno.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
L'istruzione seguente restituisce `1900, 1, 1`. L'argomento di *date* è il numero `0`. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `0` viene interpretato come 1 gennaio 1900.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


