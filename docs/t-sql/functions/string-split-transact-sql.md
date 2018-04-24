---
title: STRING_SPLIT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5204f8df5f2267421c27528ef85126e118fe56b5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Divide l'espressione di tipo carattere mediante il separatore specificato.  
  
> [!NOTE]  
>  La funzione **STRING_SPLIT** è disponibile solo nel livello di compatibilità 130. Se il livello di compatibilità del database è inferiore a 130, SQL Server non sarà in grado di trovare ed eseguire la funzione **STRING_SPLIT**. È possibile modificare il livello di compatibilità del database tramite il comando seguente:  
> ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130  
>   
>  Si noti che il livello di compatibilità 120 potrebbe essere predefinito anche nei nuovi database SQL di Microsoft Azure.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>Argomenti  
 *string*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere, come ad esempio **nvarchar**, **varchar**, **nchar** o **char**.  
  
 *separator*  
 È un singolo carattere [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere, come ad esempio **nvarchar(1)**, **varchar (1)**, **nchar (1)** o  **char (1)**, che viene usato come separatore per stringhe concatenate.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce una tabella a colonna singola con frammenti. Il nome della colonna è **value**. Restituisce **nvarchar** se uno qualsiasi degli argomenti di input è **nvarchar** o **nchar**. In caso contrario, restituisce **varchar**. La lunghezza del tipo restituito è uguale a quella dell'argomento di stringa.  
  
## <a name="remarks"></a>Remarks  
 **STRING_SPLIT** usa una stringa che deve essere suddivisa e il separatore che deve essere usato per suddividerla. Restituisce una tabella a colonna singola con substring. Ad esempio, l'istruzione seguente `SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');` che usa il carattere spazio come separatore, restituisce la tabella di risultati seguente:  
  
|Valore|  
|-----------|  
|Lorem|  
|ipsum|  
|dolor|  
|sit|  
|amet.|  
  
 Se la stringa di input è **NULL**, la funzione con valori di tabella **STRING_SPLIT** restituisce una tabella vuota.  
  
 **STRING_SPLIT** richiede almeno la modalità di compatibilità 130.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-split-comma-separated-value-string"></a>A. Dividere una stringa di valori separati da virgola  
 Analizzare un elenco di valori separati da virgole e restituire tutti i token non vuoti:  
  
```  
  
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';  
  
```  
  
 STRING_SPLIT restituirà una stringa vuota se non c'è niente tra i separatori. La condizione RTRIM(value) <> " rimuoverà i token vuoti.  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>B. Dividere una stringa di valori delimitati da virgola in una colonna  
 La tabella Product ha una colonna con un elenco di tag delimitati da virgole illustrato nell'esempio seguente:  
  
|ProductId|nome|Tag|  
|---------------|----------|----------|  
|1|Full-Finger Gloves|clothing,road,touring,bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike, mountain|  
  
 La query seguente trasforma gli elenchi di tag e li unisce alla riga originale:  
  
```  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|ProductId|nome|Valore|  
|---------------|----------|-----------|  
|1|Full-Finger Gloves|clothing|  
|1|Full-Finger Gloves|road|  
|1|Full-Finger Gloves|touring|  
|1|Full-Finger Gloves|bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike|  
|3|HL Mountain Frame|mountain|  
  
### <a name="c-aggregation-by-values"></a>C. Aggregazione per valori  
 Gli utenti devono creare un report che visualizzi il numero di prodotti per ogni tag, ordinati in base al numero di prodotti e che sia possibile filtrare in base ai tag con più di due prodotti.  
  
```  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```  
  
### <a name="d-search-by-tag-value"></a>D. Ricerca in base al valore del tag  
 Gli sviluppatori devono creare query per trovare articoli in base a parole chiave. Possono usare le query seguenti:  
  
 Per trovare i prodotti con un singolo tag (clothing):  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```  
  
 Per trovare i prodotti con due tag specificati (clothing e road):  
  
```  
  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road');  
```  
  
### <a name="e-find-rows-by-list-of-values"></a>E. Trovare le righe in base all'elenco di valori  
 Gli sviluppatori devono creare una query per trovare gli articoli in base a un elenco di ID. Possono usare la query seguente:  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')   
    ON value = ProductId;  
```  
  
 Si tratta di una sostituzione di criteri comuni, ad esempio la creazione di una stringa SQL dinamica nel livello applicazione o [!INCLUDE[tsql](../../includes/tsql-md.md)], oppure l'uso dell'operatore LIKE:  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)  
 [Funzioni per i valori stringa &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
