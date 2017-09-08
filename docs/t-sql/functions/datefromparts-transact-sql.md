---
title: DATEFROMPARTS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEFROMPARTS_TSQL
- DATEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATEFROMPARTS function
ms.assetid: 5b885376-87aa-41f1-9e18-04987aead250
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3365c40b5bc4fb57a8e09cc97e706a16fbd709ec
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Restituisce un **data** valore per l'anno, mese e giorno.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>Argomenti  
*anno*  
Espressione intera che specifica un anno.
  
*mese*  
Espressione intera che specifica un mese, da 1 a 12.
  
*giorno*  
Espressione intera che specifica un giorno.
  
## <a name="return-types"></a>Tipi restituiti
**data**
  
## <a name="remarks"></a>Osservazioni  
**DATEFROMPARTS** restituisce un **data** valore con la parte relativa alla data impostata per l'anno, mese e giorno specificati e la porzione dell'ora impostata sul valore predefinito. Se gli argomenti non sono validi, viene generato un errore. Se gli argomenti obbligatori sono Null, viene restituito un valore Null.
  
Questa funzione può essere eseguita in modalità remota in server con [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive, ma non in server con versioni precedenti a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene illustrato il **DATEFROMPARTS** (funzione).
  
```sql
SELECT DATEFROMPARTS ( 2010, 12, 31 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
----------------------------------  
2010-12-31  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Nell'esempio seguente viene illustrato il **DATEFROMPARTS** (funzione).
  
```sql
SELECT DATEFROMPARTS ( 2010, 12, 31 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
----------------------------------  
2010-12-31  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)
  
  


