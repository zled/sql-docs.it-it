---
title: STRING_AGG (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- STRING_AGG
- STRING_AGG_TSQL
helpviewer_keywords:
- STRING_AGG function
ms.assetid: 8860ef3f-142f-4cca-aa64-87a123e91206
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bf74698e9e61f456726b1e6a62126a8d78a09777
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="stringagg-transact-sql"></a>STRING_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

Concatena i valori delle espressioni della stringa e inserisce i valori dei separatori tra di essi. Il separatore non viene aggiunto alla fine della stringa.
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
STRING_AGG ( expression, separator ) [ <order_clause> ]

<order_clause> ::=   
    WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )   
```

## <a name="arguments"></a>Argomenti 

*separatore*  
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di `NVARCHAR` o `VARCHAR` tipo utilizzato come separatore per concatenata stringhe. Può essere letterale o variabile. 

*espressione*  
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo. Le espressioni vengono convertite in `NVARCHAR` o `VARCHAR` tipi durante la concatenazione. Tipi stringa non vengono convertiti in `NVARCHAR` tipo.


< order_clause >   
Specificare l'ordine dei risultati di concatenati `WITHIN GROUP` clausola:
```
WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )
```   
< order_by_expression_list >   
 
  Elenco non costante [espressioni](../../t-sql/language-elements/expressions-transact-sql.md) che può essere utilizzato per l'ordinamento dei risultati. Un solo `order_by_expression` è consentito per ogni query. Per impostazione predefinita, l'ordinamento è crescente.   
  

## <a name="return-types"></a>Tipi restituiti 

È di tipo restituito dipende dal primo argomento (espressione). Se l'argomento di input è di tipo stringa (`NVARCHAR`, `VARCHAR`), tipo di risultato sarà lo stesso come tipo di input. Nella tabella seguente sono elencate le conversioni automatico:  

|Tipo di espressione di input |Risultato | 
|-------|-------|
|NVARCHAR(MAX) |NVARCHAR(MAX) |
|VARCHAR(MAX) |VARCHAR(MAX) |
|NVARCHAR (1... 4000) |NVARCHAR (4000) |
|VARCHAR (1... 8000) |VARCHAR(8000) |
|int, bigint, smallint, tinyint, numeric, float, real, bit, decimal, smallmoney, money, datetime, datetime2, |NVARCHAR (4000) |


## <a name="remarks"></a>Osservazioni  
 
`STRING_AGG`funzione di aggregazione accetta tutte le espressioni da righe e concatenati in una singola stringa. I valori dell'espressione vengono convertiti in modo implicito in tipi di stringa e quindi concatenati. Per la conversione implicita in stringhe vengono seguite le regole esistenti per le conversioni dei tipi di dati. Per ulteriori informazioni sulle conversioni dei tipi di dati, vedere [CAST e CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md). 

Se l'espressione di input è di tipo `VARCHAR`, il separatore non può essere di tipo `NVARCHAR`. 

I valori null vengono ignorati e non è stato aggiunto il separatore corrispondente. Per restituire un segnaposto per i valori null, utilizzare il `ISNULL` funzione come illustrato nell'esempio B.

`STRING_AGG`è disponibile in qualsiasi livello di compatibilità.


## <a name="examples"></a>Esempi 

### <a name="a-generate-list-of-names-separated-in-new-lines"></a>A. Generare l'elenco di nomi separati in nuove righe 
Nell'esempio seguente genera un elenco di nomi in una cella singolo risultato, separati con ritorno a capo.
```tsql
SELECT STRING_AGG (FirstName, CHAR(13)) AS csv 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|csv | 
|--- |
|Syed <br />Catherine <br />Kim <br />Kim <br />Kim <br />Hazem <br />... | 

`NULL`i valori presenti nelle `name` celle non vengono restituite nel risultato.   
> [!NOTE]  
>  Se si utilizza l'Editor di Query di Management Studio, il **risultati in formato griglia** opzione non può implementare il ritorno a capo. Passare a **risultati in formato testo** per visualizzare il risultato impostato correttamente.   


### <a name="b-generate-list-of-names-separated-with-comma-without-null-values"></a>B. Generare l'elenco di nomi separati da virgola senza valori NULL   
Nell'esempio seguente sostituisce i valori null con 'N/d' e restituisce i nomi separati da virgole in una cella singolo risultato.  
```tsql
SELECT STRING_AGG ( ISNULL(FirstName,'N/A'), ',') AS csv 
FROM Person.Person; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
 

|CSV | 
|--- |
|Giorgio, n/d, Mike, Peter, n/d, n/d, Alice, Bob |  


### <a name="c-generate-comma-separated-values"></a>C. Generare valori separati da virgola 

```tsql   
SELECT 
STRING_AGG(CONCAT(FirstName, ' ', LastName, ' (', ModifiedDate, ')'), CHAR(13)) 
  AS names 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|nomi | 
|--- |
|Davide Sánchez (8 in febbraio 2003 12:00 AM) <br />Terri Duffy (24 in febbraio 2002 12:00 AM) <br />Roberto Tamburello (5 in dicembre 2001 12:00 AM) <br />Ezio Alboni (29 in dicembre 2001 12:00 AM) <br />... |

> [!NOTE]  
>  Se si utilizza l'Editor di Query di Management Studio, il **risultati in formato griglia** opzione non può implementare il ritorno a capo. Passare a **risultati in formato testo** per visualizzare il risultato impostato correttamente.   
 

### <a name="d-return-news-articles-with-related-tags"></a>D. Restituire news con tag correlati 

Articolo e nei tag vengono suddivisi in tabelle diverse. Sviluppatore desidera restituire una riga per ogni articolo con tutti i tag associati. Utilizzo di query riportata di seguito: 
```tsql
SELECT a.articleId, title, STRING_AGG (tag, ',') as tags 
FROM dbo.Article AS a       
LEFT JOIN dbo.ArticleTag AS t 
    ON a.ArticleId = t.ArticleId 
GROUP BY a.articleId, title;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|ID articolo |title |tags |
|--- |--- |--- |
|172 |Esegue il polling indica elezione Chiudi risultati |politica, sondaggi, municipio | 
|176 |Nuovo autostrada previsto per ridurre la congestione |NULL |
|177 |Dogs continuano a essere più cats |esegue il polling, animali| 

### <a name="e-generate-list-of-emails-per-towns"></a>E. Generare l'elenco di messaggi di posta elettronica per ogni città

La query seguente consente di trovare gli indirizzi di posta elettronica dei dipendenti e li raggruppa in base a città: 
```tsql
SELECT town, STRING_AGG (email, ';') AS emails 
FROM dbo.Employee 
GROUP BY town; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|Città |messaggi di posta elettronica |
|--- |--- |
|Seattle |syed0@adventure-works.com;catherine0@adventure-works.com;kim2@adventure-works.com |
|LA |sam1@adventure-works.com;hazem0@adventure-works.com |

Messaggi di posta elettronica restituito nella colonna può essere utilizzata per inviare messaggi di posta elettronica al gruppo di persone impegnate in alcune città particolare direttamente i messaggi di posta elettronica. 

### <a name="f-generate-a-sorted-list-of-emails-per-towns"></a>F. Generare un elenco ordinato di messaggi di posta elettronica per ogni città   
   
Simile all'esempio precedente, la query seguente consente di trovare gli indirizzi di posta elettronica dei dipendenti, li raggruppa in base a città e ordina i messaggi di posta elettronica:   
```tsql
SELECT town, 
    STRING_AGG (email, ';') WITHIN GROUP (ORDER BY email ASC) AS emails 
FROM dbo.Employee 
GROUP BY town; 
```
   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|Città |messaggi di posta elettronica |
|--- |--- |
|Seattle |catherine0@adventure-works.com;kim2@adventure-works.com;syed0@adventure-works.com |
|LA |hazem0@adventure-works.com;sam1@adventure-works.com |


## <a name="see-also"></a>Vedere anche  

[Funzioni stringa (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  


