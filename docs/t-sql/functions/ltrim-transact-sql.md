---
title: LTRIM (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LTRIM
- LTRIM_TSQL
dev_langs: TSQL
helpviewer_keywords:
- leading blanks
- deleting blank spaces
- characters [SQL Server], blanks
- removing blank spaces
- LTRIM function
- blank characters [SQL Server]
ms.assetid: 369ed340-1a09-4597-a9eb-6720156cd39a
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 438975b08700cb87c534f0cb4e3021a4167ae8b1
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="ltrim-transact-sql"></a>LTRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una espressione di caratteri dopo aver rimosso gli spazi vuoti iniziali.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
LTRIM ( character_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di dati carattere o binario. *character_expression* può essere una costante, variabile o colonna. *character_expression* deve essere un tipo di dati, eccetto **testo**, **ntext**, e **immagine**, che è implicitamente convertibile in **varchar** . In caso contrario, utilizzare [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) per convertire esplicitamente *character_expression*.  
  
## <a name="return-type"></a>Tipo restituito  
 **varchar** o **nvarchar**  
  
## <a name="examples"></a>Esempi  

### <a name="a-simple-example"></a>A. Esempio semplice   

 Nell'esempio seguente usa LTRIM per rimuovere gli spazi iniziali da un'espressione di caratteri.  
  
```sql  
SELECT LTRIM('     Five spaces are at the beginning of this string.') FROM sys.databases;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ---------------------------------------------------------------  
  Five spaces are at the beginning of this string.
  ```  

### <a name="b-example-using-a-variable"></a>B: esempio utilizzo di una variabile   
  
 Nell'esempio seguente viene utilizzato `LTRIM` per rimuovere gli spazi iniziali da una variabile di tipo carattere.  
  
```  
DECLARE @string_to_trim varchar(60);  
SET @string_to_trim = '     5 spaces are at the beginning of this string.';  
SELECT 
    @string_to_trim AS 'Original string',
    LTRIM(@string_to_trim) AS 'Without spaces';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Original string Without spaces
--------------------------------------------------- ---------------------------------------------
     5 spaces are at the beginning of this string.  5 spaces are at the beginning of this string.
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


