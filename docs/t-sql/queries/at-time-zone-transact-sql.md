---
title: NEL fuso orario (Transact-SQL) | Documenti Microsoft
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AT TIME ZONE
- AT_TIME_ZONE_TSQL
helpviewer_keywords:
- AT TIME ZONE function
ms.assetid: 311f682f-7f1b-43b6-9ea0-24e36b64f73a
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f0983cbd76b1ec3a71985537f098f8faf002b93e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="at-time-zone-transact-sql"></a>NEL fuso orario (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Converte un *inputdate* corrispondenti *datetimeoffset* valore nel fuso orario di destinazione. Se *inputdate* viene fornito senza informazioni relative all'offset, la funzione viene applicata l'offset del fuso orario, supponendo che *inputdate* valore viene fornito nel fuso orario di destinazione. Se *inputdate* viene fornito come un *datetimeoffset* valore, più **AT TIME ZONE** clausola lo converte nel fuso orario di destinazione utilizzando regole di conversione di fuso orario.  
  
 **NEL fuso orario** implementazione si basa su un meccanismo di Windows per convertire **datetime** valori tra fusi orari.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
inputdate AT TIME ZONE timezone  
```  
  
## <a name="arguments"></a>Argomenti  
 *inputdate*  
 È un'espressione che può essere risolta in un **smalldatetime**, **datetime**, **datetime2**, o **datetimeoffset** valore.  
  
 *fuso orario*  
 Nome del fuso orario di destinazione. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]si basa sui fusi orari che vengono archiviati nel Registro di sistema Windows. Tutti i fusi orari installati nel computer sono archiviati nell'hive del Registro di sistema seguente: **KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones**. Un elenco dei fusi orari installati viene inoltre esposta attraverso il [Sys. time_zone_info &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-time-zone-info-transact-sql.md) visualizzazione.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce il tipo di dati di **datetimeoffset**  
  
## <a name="return-value"></a>Valore restituito  
 Il **datetimeoffset** valore nel fuso orario di destinazione.  
  
## <a name="remarks"></a>Osservazioni  
 **NEL fuso orario** applicate regole specifiche per la conversione di valori di input **smalldatetime**, **datetime** e **datetime2** tipi di dati che rientrano in un intervallo che è interessato dalla modifica dell'ora legale:  
  
-   Quando è impostata con l'orologio è presente un gap nell'ora locale in cui la durata dipende dalla durata della regolazione dell'orologio (in genere 1 ora, ma può essere 30 o 45 minuti, a seconda di fuso orario). In tal caso, vengono convertiti i punti nel tempo che appartengono a questo divario con l'offset *dopo* all'ora legale.  
  
    ```  
    /*  
        Moving to DST in "Central European Standard Time" zone: 
        offset changes from +01:00 -> +02:00   
        Change occurred on March 29th, 2015 at 02:00:00.   
        Adjusted local time became 2015-03-29 03:00:00.  
    */  
    
    --Time before DST change has standard time offset (+01:00)
    SELECT CONVERT(datetime2(0), '2015-03-29T01:01:00', 126)     
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 01:01:00 +01:00   
  
    /*
      Adjusted time from the "gap interval" (between 02:00 and 03:00)
      is moved 1 hour ahead and presented with the summer time offset
      (after the DST change) 
    */
    SELECT CONVERT(datetime2(0), '2015-03-29T02:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 03:01:00 +02:00
      
    --Time after 03:00 is presented with the summer time offset (+02:00)
    SELECT CONVERT(datetime2(0), '2015-03-29T03:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 03:01:00 +02:00  
  
    ```  
  
- Quando l'orologio viene reimpostato, 2 ore dall'ora locale si sovrappongono in un'ora.  In tal caso, vengono presentati i punti nel tempo che appartengono all'intervallo sovrapposto all'offset *prima* la modifica dell'orologio:  
  
    ```  
    /*  
        Moving back from DST to standard time in 
        "Central European Standard Time" zone: 
        offset changes from +02:00 -> +01:00.  
        Change occurred on October 25th, 2015 at 03:00:00.   
        Adjusted local time became 2015-10-25 02:00:00   
    */  
    
    --Time before the change has DST offset (+02:00)
    SELECT CONVERT(datetime2(0), '2015-10-25T01:01:00', 126)      
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 01:01:00 +02:00  
    
    /*
      Time from the "overlapped interval" is presented with standard time 
      offset (before the change)    
    */
    SELECT CONVERT(datetime2(0), '2015-10-25T02:00:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 02:00:00 +02:00  
    
    
    --Time after 03:00 is regularly presented with the standard time offset (+01:00)    
    SELECT CONVERT(datetime2(0), '2015-10-25T03:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 03:01:00 +01:00
  
    ```  

Poiché alcune informazioni (ad esempio le regole di fuso orario) vengono mantenute all'esterno di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e sono soggetti a modifiche occasionali, il **AT TIME ZONE** funzione è classificata come non deterministiche. 
  
## <a name="examples"></a>Esempi  
  
### <a name="a-add-target-time-zone-offset-to-datetime-without-offset-information"></a>A. Aggiungere datetime senza informazioni relative all'offset di differenza di fuso orario di destinazione  
 Utilizzare **AT TIME ZONE** per aggiungere l'offset in base alle regole di fuso orario, quando si è certi che originale **datetime** valori vengono forniti nello stesso fuso orario:  
  
```  
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="b-convert-values-between-different-time-zones"></a>B. Convertire valori tra fusi orari diversi  
 Nell'esempio seguente converte i valori compresi tra fusi orari diversi:  
  
```  
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST,  
    OrderDate AT TIME ZONE 'Pacific Standard Time'   
    AT TIME ZONE 'Central European Standard Time' AS OrderDate_TimeZoneCET  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="c-query-temporal-tables-using-local-time-zone"></a>C. Eseguire query su tabelle temporali con fuso orario locale  
 L'esempio seguente seleziona i dati da una tabella temporale.  
  
```  
USE AdventureWorks2016;  
GO  
  
DECLARE @ASOF datetimeoffset;  
SET @ASOF = DATEADD (month, -1, GETDATE()) AT TIME ZONE 'UTC';  
  
-- Query state of the table a month ago projecting period   
-- columns as Pacific Standard Time  
SELECT BusinessEntityID, PersonType, NameStyle, Title,   
    FirstName, MiddleName,  
    ValidFrom AT TIME ZONE 'Pacific Standard Time' 
FROM  Person.Person_Temporal  
FOR SYSTEM_TIME AS OF @ASOF;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi data e ora](../../t-sql/data-types/date-and-time-types.md)   
 [Data e ora funzioni e tipi di &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)  
  
  

