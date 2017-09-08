---
title: ISDATE (Transact-SQL) | Documenti Microsoft
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
- ISDATETIME
- ISDATE_TSQL
- ISDATE
- ISDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], ISDATE
- validate dates times [SQL Server]
- formats [SQL Server], time
- dates [SQL Server], validate
- verify dates times [SQL Server]
- functions [SQL Server], time
- formats [SQL Server], dates
- functions [SQL Server], date and time
- time [SQL Server], functions
- time [SQL Server], validate
- ISDATE function [SQL Server]
ms.assetid: 8e2c9ee7-388a-432f-b2c9-7b398f26bf85
caps.latest.revision: 54
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e005b11ad15170dcc2f6f45441d62e6ccc29570
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="isdate-transact-sql"></a>ISDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce 1 se il *espressione* valido **data**, **ora**, o **datetime** valore; in caso contrario, 0.  
  
 ISDATE restituisce 0 se il *espressione* è un **datetime2** valore.  
  
 Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md). Si noti che l'intervallo di dati datetime è compreso tra 1753-01-01 e 9999-12-31, mentre l'intervallo di dati relativi alla data è compreso tra 0001-01-01 e 9999-12-31.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
ISDATE ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È una stringa di caratteri o [espressione](../../t-sql/language-elements/expressions-transact-sql.md) che può essere convertito in una stringa di caratteri. L'espressione deve essere di lunghezza inferiore a 4.000 caratteri. I tipi di dati relativi a data e ora, ad eccezione di datetime e smalldatetime, non sono consentiti come argomento di ISDATE.  
  
## <a name="return-type"></a>Tipo restituito  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 ISDATE è deterministica solo se si utilizza con la [CONVERTIRE](../../t-sql/functions/cast-and-convert-transact-sql.md) funzione, se viene specificato il parametro di stile CONVERT e lo stile non è uguale a 0, 100, 9 o 109.  
  
 Il valore restituito di ISDATE dipende dalle impostazioni definite da [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md), [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) e [configurare l'opzione di configurazione Server default language](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md).  
  
## <a name="isdate-expression-formats"></a>Formati di espressione ISDATE  
 Per esempi di formati validi per i quali ISDATE restituisce 1, vedere la sezione "Stringa letterale formati supportati per datetime" nel [datetime](../../t-sql/data-types/datetime-transact-sql.md) e [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) argomenti. Per ulteriori esempi, vedere anche la colonna di Input/Output nella sezione "Argomenti" di [CAST e CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 Nella tabella seguente sono riepilogati i formati di espressione non validi e che restituiscono 0 o un errore.  
  
|Espressione ISDATE|Valore restituito ISDATE|  
|-----------------------|-------------------------|  
|NULL|0|  
|I valori dei tipi di dati elencati nella [tipi di dati](../../t-sql/data-types/data-types-transact-sql.md) in qualsiasi categoria di tipi di dati diverso da stringhe di caratteri, stringhe di caratteri Unicode o data e ora.|0|  
|I valori di **testo**, **ntext**, o **immagine** tipi di dati.|0|  
|Qualsiasi valore con una scala di precisione in secondi frazionari maggiore di 3 (da 0,0000 a 0,0000000... n) ISDATE restituisce 0 se il *espressione* è un **datetime2** valore, ma viene restituito 1 se il *espressione* valido **datetime** valore.|0|  
|Qualsiasi valore che combina una data valida con un valore non valido, ad esempio 1995-10-1a.|0|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-isdate-to-test-for-a-valid-datetime-expression"></a>A. Utilizzo di ISDATE per il test di un'espressione datetime valida  
 Nell'esempio seguente viene illustrato come utilizzare `ISDATE` per verificare se una stringa di caratteri è un valore valido **datetime**.  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    PRINT 'VALID'  
ELSE  
    PRINT 'INVALID';  
```  
  
### <a name="b-showing-the-effects-of-the-set-dateformat-and-set-language-settings-on-return-values"></a>B. Effetti delle impostazioni di SET DATEFORMAT e SET LANGUAGE sui valori restituiti  
 Nelle istruzioni seguenti sono mostrati i valori restituiti come risultato delle impostazioni di `SET DATEFORMAT` e `SET LANGUAGE`.  
  
```  
/* Use these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
/* Expression in mdy dateformat */  
SELECT ISDATE('04/15/2008'); --Returns 1.  
/* Expression in mdy dateformat */  
SELECT ISDATE('04-15-2008'); --Returns 1.   
/* Expression in mdy dateformat */  
SELECT ISDATE('04.15.2008'); --Returns 1.   
/* Expression in myd  dateformat */  
SELECT ISDATE('04/2008/15'); --Returns 1.  
  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET DATEFORMAT dmy;  
SELECT ISDATE('15/04/2008'); --Returns 1.  
SET DATEFORMAT dym;  
SELECT ISDATE('15/2008/04'); --Returns 1.  
SET DATEFORMAT ydm;  
SELECT ISDATE('2008/15/04'); --Returns 1.  
SET DATEFORMAT ymd;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET LANGUAGE English;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET LANGUAGE Hungarian;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET LANGUAGE Swedish;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET LANGUAGE Italian;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
/* Return to these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-isdate-to-test-for-a-valid-datetime-expression"></a>C. Utilizzo di ISDATE per il test di un'espressione datetime valida  
 Nell'esempio seguente viene illustrato come utilizzare `ISDATE` per verificare se una stringa di caratteri è un valore valido **datetime**.  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    SELECT 'VALID';  
ELSE  
    SELECT 'INVALID';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


