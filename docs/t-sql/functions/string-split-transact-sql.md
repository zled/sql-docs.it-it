---
title: STRING_SPLIT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRING_SPLIT
- STRING_SPLIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_SPLIT function
ms.assetid: 3273dbf3-0b4f-41e1-b97e-b4f67ad370b9
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 049bdf1021d57e28ed94e11c89aa997ee0eba5e5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Divide l'espressione di tipo carattere utilizzando il separatore specificato.  
  
> [!NOTE]  
>  Il **STRING_SPLIT** funzione è disponibile solo nel livello di compatibilità 130. Se il livello di compatibilità del database è inferiore a 130, SQL Server non sarà in grado di trovare ed eseguire **STRING_SPLIT** (funzione). È possibile modificare il livello di compatibilità del database tramite il comando seguente:  
> ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130  
>   
>  Si noti che il livello di compatibilità 120 potrebbe essere predefinito anche nel nuovo database SQL di Azure.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>Argomenti  
 *string*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere (ad esempio **nvarchar**, **varchar**, **nchar** o **char**).  
  
 *separatore*  
 È un singolo carattere [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere (ad esempio **nvarchar(1)**, **varchar (1)**, **nchar (1)** o  **Char (1)**) che viene utilizzato come separatore per stringhe concatenate.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce una tabella a colonna singola con frammenti. Il nome della colonna è **valore**. Restituisce **nvarchar** se uno qualsiasi degli argomenti di input sono **nvarchar** o **nchar**. In caso contrario restituisce **varchar**. La lunghezza del tipo restituito è lo stesso come la lunghezza dell'argomento stringa.  
  
## <a name="remarks"></a>Osservazioni  
 **STRING_SPLIT** accetta una stringa che deve essere divisi e il separatore utilizzato per dividere una stringa. Restituisce una tabella a colonna singola con sottostringhe. Ad esempio, l'istruzione seguente `SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');` utilizzando il carattere spazio come separatore, restituisce seguenti tabella dei risultati:  
  
|Valore|  
|-----------|  
|Lorem|  
|Ipsum|  
|dolor|  
|sit|  
|Amet.|  
  
 Se la stringa di input è **NULL**, **STRING_SPLIT** funzione con valori di tabella restituisce una tabella vuota.  
  
 **STRING_SPLIT** richiede almeno la modalità di compatibilità 130.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-split-comma-separated-value-string"></a>A. Stringa del valore di separati da virgola di divisione  
 Analizzare un elenco separato da virgole dei valori e restituire tutti i token non vuoto:  
  
```  
  
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';  
  
```  
  
 STRING_SPLIT restituirà una stringa vuota se non c'è niente tra separatore. Condizione RTRIM(value) <> ' rimuoverà i token vuoti.  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>B. Stringa del valore in una colonna di separati da virgola di divisione  
 Tabella Product dispone di una colonna con elenco separato da virgole di tag illustrato nell'esempio seguente:  
  
|productId|Nome|Tag|  
|---------------|----------|----------|  
|1|Un dito full guanti|abbigliamento, strada, touring, bike|  
|2|LL cuffie|biciclette|  
|3|HL Mountain Frame|bike, mountain|  
  
 La query seguente trasforma ogni elenco di tag e le unisce con la riga originale:  
  
```  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|productId|Nome|Valore|  
|---------------|----------|-----------|  
|1|Un dito full guanti|abbigliamento|  
|1|Un dito full guanti|strada|  
|1|Un dito full guanti|Touring|  
|1|Un dito full guanti|biciclette|  
|2|LL cuffie|biciclette|  
|3|HL Mountain Frame|biciclette|  
|3|HL Mountain Frame|mountain|  
  
### <a name="c-aggregation-by-values"></a>C. Aggregazione di valori  
 Gli utenti devono creare un report che mostra il numero di prodotti per ogni tag, ordinati in base al numero di prodotti e per filtrare solo i tag con i prodotti più di 2.  
  
```  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```  
  
### <a name="d-search-by-tag-value"></a>D. Ricerca in base al valore del tag  
 Gli sviluppatori devono creare query per trovare articoli dalle parole chiave. Sono utilizzare le seguenti query:  
  
 Per trovare i prodotti con un singolo tag (abbigliamento):  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```  
  
 Trovare i prodotti con due tag specificato (abbigliamento e road):  
  
```  
  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road');  
```  
  
### <a name="e-find-rows-by-list-of-values"></a>E. Trovare le righe dall'elenco di valori  
 Gli sviluppatori devono creare una query per trovare articoli da un elenco di ID. Possono utilizzare query riportata di seguito:  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')   
    ON value = ProductId;  
```  
  
 Si tratta di sostituzione per anti-pattern comuni, ad esempio la creazione di una stringa SQL dinamica nel livello applicazione o [!INCLUDE[tsql](../../includes/tsql-md.md)], oppure utilizzando l'operatore LIKE:  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [SOTTOSTRINGA &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
  
  

