---
title: TRIM (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TRIM
- TRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
caps.latest.revision: 4
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 64cef84a613d71e65b33bed1c1e740dc59eeed9d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="trim-transact-sql"></a>TRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

Rimuove il carattere spazio `char(32)` o altri caratteri dall'inizio o alla fine di una stringa specificate.  
 
## <a name="syntax"></a>Sintassi   
```
TRIM ( [ characters FROM ] string ) 
```
[//]: # "[ENTRAMBI | INIZIALI | FINALI] non ancora disponibile."

## <a name="arguments"></a>Argomenti   

caratteri   
È un valore letterale, una variabile o una chiamata di funzione di qualsiasi tipo di carattere non LOB (`nvarchar`, `varchar`, `nchar`, o `char`) contenente i caratteri che devono essere rimossi. `nvarchar(max)`e `varchar(max)` tipi non sono consentiti.

string   
È un'espressione di qualsiasi tipo di carattere (`nvarchar`, `varchar`, `nchar`, o `char`) in cui caratteri devono essere rimossi.

## <a name="return-types"></a>Tipi restituiti   
Restituisce un'espressione di caratteri con un tipo di argomento di tipo stringa in cui il carattere spazio `char(32)` o altri caratteri specificate vengono rimossi da entrambi i lati. Restituisce `NULL` se la stringa di input è `NULL`.

## <a name="remarks"></a>Osservazioni   
Per impostazione predefinita `TRIM` funzione rimuove il carattere spazio `char(32)` da entrambi i lati. che equivale a `LTRIM(RTRIM(@string))`. Comportamento di `TRIM ` funzione con i caratteri specificati è identico al comportamento di `REPLACE` funzione in cui i caratteri dall'inizio o fine vengono sostituite con le stringhe vuote.


## <a name="examples"></a>Esempi
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Rimuove il carattere di spazio da entrambi i lati della stringa   
Nell'esempio seguente rimuove gli spazi dal prima e dopo la parola `test`.   
```tsql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>B.  Entrambi i lati della stringa di caratteri specificati contenuti rimuove   
Nell'esempio seguente rimuove un punto finale e gli spazi finali.
```tsql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>Vedere anche
[Funzioni stringa (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
[LTRIM (Transact-SQL)](../../t-sql/functions/ltrim-transact-sql.md)   
[RTRIM (Transact-SQL)](../../t-sql/functions/rtrim-transact-sql.md)   
[REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)   

