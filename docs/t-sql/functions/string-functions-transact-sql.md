---
title: Funzioni (Transact-SQL) stringa | Documenti Microsoft
ms.custom: 
ms.date: 08/15/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], strings
- strings [SQL Server], functions
- string functions
- strings [SQL Server]
ms.assetid: 6940a83d-5374-4af3-bb27-5d89c8af83ac
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 33df9a7082ee7e637b60e3a1ca7911e127040a08
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="string-functions-transact-sql"></a>Funzioni per i valori stringa (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Le funzioni scalari elencate di seguito eseguono un'operazione su un valore di input stringa e restituiscono un valore stringa o numerico.  
  
||||  
|-|-|-| 
|[ASCII](../../t-sql/functions/ascii-transact-sql.md)|[CHAR](../../t-sql/functions/char-transact-sql.md)|[CHARINDEX](../../t-sql/functions/charindex-transact-sql.md)|
|[CONCAT](../../t-sql/functions/concat-transact-sql.md)|[CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md)|[DIFFERENZA](../../t-sql/functions/difference-transact-sql.md) |
|[FORMATO](../../t-sql/functions/format-transact-sql.md)|[LEFT](../../t-sql/functions/left-transact-sql.md)|[LEN](../../t-sql/functions/len-transact-sql.md) |
|[INFERIORE](../../t-sql/functions/lower-transact-sql.md)|[LTRIM](../../t-sql/functions/ltrim-transact-sql.md)|[NCHAR](../../t-sql/functions/nchar-transact-sql.md) |
|[PATINDEX](../../t-sql/functions/patindex-transact-sql.md)|[QUOTENAME](../../t-sql/functions/quotename-transact-sql.md)|[REPLACE](../../t-sql/functions/replace-transact-sql.md) |
|[LA REPLICA](../../t-sql/functions/replicate-transact-sql.md)|[REVERSE](../../t-sql/functions/reverse-transact-sql.md) |[RIGHT](../../t-sql/functions/right-transact-sql.md) |
|[RTRIM](../../t-sql/functions/rtrim-transact-sql.md)|[SOUNDEX](../../t-sql/functions/soundex-transact-sql.md) |[SPAZIO](../../t-sql/functions/space-transact-sql.md) |
|[STR](../../t-sql/functions/str-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|[STRING_ESCAPE](../../t-sql/functions/string-escape-transact-sql.md) |
|[STRING_SPLIT](../../t-sql/functions/string-split-transact-sql.md)|[STUFF](../../t-sql/functions/stuff-transact-sql.md)|[SUBSTRING](../../t-sql/functions/substring-transact-sql.md) |
|[TRADUCI](../../t-sql/functions/translate-transact-sql.md)|[TRIM](../../t-sql/functions/trim-transact-sql.md)|[UNICODE](../../t-sql/functions/unicode-transact-sql.md) |
|[SUPERIORE](../../t-sql/functions/upper-transact-sql.md) | | |


  
 Funzioni di stringa incorporata tutti tranne `FORMAT` sono deterministiche. ovvero restituiscono sempre lo stesso valore ogni volta che vengono richiamate in base a un set di valori di input specifico. Per ulteriori informazioni sulle funzioni deterministiche, vedere [funzioni deterministiche e non](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
 Quando le funzioni per i valori stringa vengono passate come argomenti che non sono valori stringa, il tipo di input viene convertito in modo implicito in un tipo di dati testo. Per ulteriori informazioni, vedere [conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  


