---
title: REPLICATE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REPLICATE_TSQL
- REPLICATE
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], repeating
- REPLICATE function
- repeating character expressions
ms.assetid: 0cd467fb-3f22-471a-892c-0039d9f7fa1a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 574f4d115708075ddb8f2a4c2987f97508ae24cb
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="replicate-transact-sql"></a>REPLICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Ripete un valore stringa il numero di volte specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
REPLICATE ( string_expression ,integer_expression )   
```  
  
## <a name="arguments"></a>Argomenti  
 *string_expression*  
 Espressione di dati di tipo stringa di caratteri o binario. *string_expression* può essere character o Binary.  
  
> [!NOTE]  
>  Se *string_expression* non è di tipo **varchar (max)** o **nvarchar (max)**, REPLICATE tronca il valore restituito a 8.000 byte. Per restituire i valori maggiori di 8.000 byte, *string_expression* deve essere impostato in modo esplicito il tipo di dati di valori di grandi dimensioni appropriate.  
  
 *integer_expression*  
 È un'espressione di qualsiasi tipo integer, tra cui **bigint**. Se *integer_expression* è negativo, viene restituito NULL.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce lo stesso tipo *string_expression*.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-replicate"></a>A. Utilizzo di REPLICATE  
 Nell'esempio seguente il carattere `0` viene ripetuto quattro volte davanti al codice della linea di produzione nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT [Name]  
, REPLICATE('0', 4) + [ProductLine] AS 'Line Code'  
FROM [Production].[Product]  
WHERE [ProductLine] = 'T'  
ORDER BY [Name];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Name                                               Line Code  
-------------------------------------------------- ---------  
HL Touring Frame - Blue, 46                        0000T   
HL Touring Frame - Blue, 50                        0000T   
HL Touring Frame - Blue, 54                        0000T   
HL Touring Frame - Blue, 60                        0000T   
HL Touring Frame - Yellow, 46                      0000T   
HL Touring Frame - Yellow, 50                      0000T  
...  
```  
  
### <a name="b-using-replicate-and-datalength"></a>B. Utilizzo di REPLICATE e DATALENGTH  
 Nell'esempio seguente vengono inseriti numeri di riempimento iniziali a sinistra fino alla lunghezza specificata durante la conversione da un tipo di dati numerico a un tipo di dati carattere o Unicode.  
  
```  
IF EXISTS(SELECT name FROM sys.tables  
      WHERE name = 't1')  
   DROP TABLE t1;  
GO  
CREATE TABLE t1   
(  
 c1 varchar(3),  
 c2 char(3)  
);  
GO  
INSERT INTO t1 VALUES ('2', '2'), ('37', '37'),('597', '597');  
GO  
SELECT REPLICATE('0', 3 - DATALENGTH(c1)) + c1 AS 'Varchar Column',  
       REPLICATE('0', 3 - DATALENGTH(c2)) + c2 AS 'Char Column'  
FROM t1;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
Varchar Column        Char Column  
--------------------  ------------  
002                   2    
037                   37   
597                   597  
  
(3 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-replicate"></a>C: utilizzo di REPLICATE  
 Nell'esempio seguente consente di replicare un `0` carattere quattro volte davanti un `ItemCode` valore.  
  
```  
-- Uses AdventureWorks  
  
SELECT EnglishProductName AS Name,  
   ProductAlternateKey AS ItemCode,  
   REPLICATE('0', 4) + ProductAlternateKey AS FullItemCode  
FROM dbo.DimProduct  
ORDER BY Name;  
```  
  
 Di seguito sono le prime righe nel set di risultati.  
  
 ```
Name                     ItemCode       FullItemCode
------------------------ -------------- ---------------
Adjustable Race          AR-5381        0000AR-5381
All-Purpose Bike Stand   ST-1401        0000ST-1401
AWC Logo Cap             CA-1098        0000CA-1098
AWC Logo Cap             CA-1098        0000CA-1098
AWC Logo Cap             CA-1098        0000CA-1098
BB Ball Bearing          BE-2349        0000BE-2349
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [SPACE &#40;Transact-SQL&#41;](../../t-sql/functions/space-transact-sql.md)  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

