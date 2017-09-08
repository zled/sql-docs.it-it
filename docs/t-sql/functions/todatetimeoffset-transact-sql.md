---
title: TODATETIMEOFFSET (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TO_DATETIMEOFFSET_TSQL
- SWITCH_TZ_TSQL
- SWITCH_TZ
- TO_DATETIMEOFFSET
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], TODATETIMEOFFSET
- TODATETIMEOFFSET function
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: b5fafc08-efd4-4a3b-a0b3-068981a0a685
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77d42b2484563d162d78e1caad28389cc26f6cee
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="todatetimeoffset-transact-sql"></a>TODATETIMEOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce un **datetimeoffset** valore convertito da un **datetime2** espressione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
TODATETIMEOFFSET ( expression , time_zone )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) che viene risolta in un [datetime2](../../t-sql/data-types/datetime2-transact-sql.md) valore.  
  
> [!NOTE]  
>  L'espressione non può essere di tipo **testo**, **ntext**, o **immagine** perché questi tipi possono essere convertiti in modo implicito **varchar** o **nvarchar**.  
  
 *fuso orario*  
 Espressione che rappresenta la differenza di fuso orario in minuti (se è numero intero), ad esempio -120, o in ore e minuti (se è una stringa), ad esempio ‘+13.00’. L'intervallo è compreso tra +14 e -14 (in ore). L'espressione viene interpretata come ora locale in base al valore time_zone specificato.  
  
> [!NOTE]  
>  Se l'espressione è una stringa di caratteri, il formato deve essere {+|-}TZH:THM.  
  
## <a name="return-type"></a>Tipo restituito  
 **DateTimeOffset**. La precisione frazionaria è lo stesso come il *datetime* argomento.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-time-zone-offset-of-the-current-date-and-time"></a>A. Modifica della differenza di fuso orario della data e ora correnti  
 Nell'esempio seguente viene impostata la differenza di fuso orario della data e ora correnti sul valore `-07:00`.  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="b-changing-the-time-zone-offset-in-minutes"></a>B. Modifica della differenza di fuso orario in minuti  
 Nell'esempio seguente la differenza di fuso orario viene impostata sul valore `-120` minuti.  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="c-adding-a-13-hour-time-zone-offset"></a>C. Aggiunta di una differenza di fuso orario di 13 ore  
 Nell'esempio seguente viene aggiunta una differenza di fuso orario di 13 ore a una data e a un'ora.  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-changing-the-time-zone-offset-of-the-current-date-and-time"></a>D. Modifica della differenza di fuso orario della data e ora correnti  
 Nell'esempio seguente viene impostata la differenza di fuso orario della data e ora correnti sul valore `-07:00`.  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="e-changing-the-time-zone-offset-in-minutes"></a>E. Modifica della differenza di fuso orario in minuti  
 Nell'esempio seguente la differenza di fuso orario viene impostata sul valore `-120` minuti.  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="f-adding-a-13-hour-time-zone-offset"></a>F. Aggiunta di una differenza di fuso orario di 13 ore  
 Nell'esempio seguente viene aggiunta una differenza di fuso orario di 13 ore a una data e a un'ora.  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Data e ora funzioni e tipi di &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [FUSO orario &AMP; #40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  


