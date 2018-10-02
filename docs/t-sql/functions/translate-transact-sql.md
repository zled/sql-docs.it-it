---
title: TRANSLATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 125ce02e483cc927cf5b6a1d37f4209dcc3dcb22
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836659"
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Restituisce la stringa fornita come primo argomento dopo che alcuni caratteri specificati nel secondo argomento sono stati convertiti in un set di caratteri di destinazione.

## <a name="syntax"></a>Sintassi   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>Argomenti   

inputString   
[Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere (nvarchar, varchar, nchar, char).

caratteri   
[Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere contenente caratteri da sostituire.

traduzioni   
[Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di caratteri che corrisponde al secondo argomento per tipo e lunghezza.

## <a name="return-types"></a>Tipi restituiti   
Restituisce un'espressione di caratteri dello stesso tipo di `inputString` in cui i caratteri del secondo argomento vengono sostituiti con i caratteri corrispondenti del terzo argomento.

## <a name="remarks"></a>Remarks   

La funzione `TRANSLATE` restituirà un errore se i caratteri e le conversioni hanno lunghezze diverse. La funzione `TRANSLATE` restituisce lo stesso input se come caratteri o argomenti di sostituzione vengono specificati valori Null. Il comportamento della funzione `TRANSLATE` deve essere identico a quello della funzione [REPLACE](../../t-sql/functions/replace-transact-sql.md).   

Il comportamento della funzione `TRANSLATE` equivale all'uso di più funzioni `REPLACE`.

`TRANSLATE` riconosce sempre le regole di confronto SC.

## <a name="examples"></a>Esempi   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Sostituire le parentesi quadrate e graffe con parentesi normali    
La query seguente sostituisce le parentesi quadrate e graffe nella stringa di input con parentesi normali:
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

>  [!NOTE]
>  La funzione `TRANSLATE` in questo esempio equivale all'istruzione seguente che usa `REPLACE`, ma è molto più semplice: `SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[3+4]/{7-2}','[','('), ']', ')'), '{', '('), '}', ')');` 


###  <a name="b-convert-geojson-points-into-wkt"></a>B. Convertire i punti GeoJSON in WKT (well-known text)    
GeoJSON è un formato per la codifica di un'ampia gamma di strutture di dati geografici. La funzione `TRANSLATE` consente agli sviluppatori di convertire facilmente i punti GeoJSON in formato WKT e viceversa. La query seguente sostituisce le parentesi quadrate e graffe nell'input con parentesi normali:   
```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|Punto  |Coordinate |  
---------|--------- |
(137.4  72.3) |[137.4,72.3] |


## <a name="see-also"></a>Vedere anche
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [Funzioni per i valori stringa (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   

