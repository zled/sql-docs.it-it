---
title: TRANSLATE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e7ea679043b83d8cee26f431602450d023516647
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Restituisce la stringa fornita come primo argomento, dopo alcuni caratteri specificati nel secondo argomento vengono convertite in un set di caratteri di destinazione.

## <a name="syntax"></a>Sintassi   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>Argomenti   

inputString   
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere (nvarchar, varchar, nchar, char).

caratteri   
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere contenente caratteri che devono essere sostituiti.

traduzioni   
È un carattere [espressione](../../t-sql/language-elements/expressions-transact-sql.md) corrispondente secondo argomento di tipo e lunghezza.

## <a name="return-types"></a>Tipi restituiti   
Restituisce un'espressione di caratteri dello stesso tipo `inputString` in caratteri del secondo argomento vengono sostituiti con i caratteri corrispondenti dal terzo argomento.

## <a name="remarks"></a>Osservazioni   

`TRANSLATE`funzione restituirà un errore se i caratteri e le traduzioni hanno lunghezze diverse. `TRANSLATE`funzione deve restituire input subisce modifiche se i valori null vengono forniti come argomenti di sostituzione o di caratteri. Il comportamento del `TRANSLATE` funzione deve essere identica al [sostituire](../../t-sql/functions/replace-transact-sql.md) (funzione).   

Il comportamento del `TRANSLATE` funzione equivale a utilizzare più `REPLACE` funzioni.

`TRANSLATE`è sempre le regole di confronto SC specifico.

## <a name="examples"></a>Esempi   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Sostituire quadrate e parentesi graffe con parentesi graffe regolare    
La query seguente sostituisce quadrate e parentesi graffe nella stringa di input con parentesi:
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

>  [!NOTE]
>  Il `TRANSLATE` funzione in questo esempio è equivalente a ma molto contratti rispetto all'utilizzo di istruzione seguenti `REPLACE`:`SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[3+4]/{7-2}','[','('), ']', ')'), '{', '('), '}', ')');` 


###  <a name="b-convert-geojson-points-into-wkt"></a>B. Convertire i punti GeoJSON WKT    
GeoJSON è un formato per la codifica di un'ampia gamma di strutture di dati geografici. Con il `TRANSLATE` (funzione), gli sviluppatori è possono convertire facilmente i punti GeoJSON in formato WKT e viceversa. La query seguente sostituisce quadrate e parentesi graffe nell'input con parentesi graffe regolari:   
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
 [Funzioni stringa (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   

