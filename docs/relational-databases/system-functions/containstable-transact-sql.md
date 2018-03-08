---
title: CONTAINSTABLE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTAINSTABLE
- CONTAINSTABLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- precise or fuzzy (less precise) matches [full-text search]
- fuzzy (less precise) word or phrase search [full-text search]
- word searches [full-text search]
- weighted values [full-text search]
- values [SQL Server], ranked
- LANGUAGE option
- NEAR option [full-text search]
- RANK column
- phrase searches [full-text search]
- conditions [SQL Server], CONTAINSTABLE
- relevance ranking values [full-text search]
- proximity searches [full-text search]
- CONTAINSTABLE function (Transact-SQL)
- ranked results [full-text search]
- rankings [full-text search]
- less precise (fuzzy) searches [full-text search]
ms.assetid: e580c210-cf57-419d-9544-7f650f2ab814
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a9f4ab666351984b62e47d664d17d9e2769337cd
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="containstable-transact-sql"></a>CONTAINSTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una tabella contenente una o più righe o nessuna riga per le colonne che includono corrispondenze più o meno esatte di singole parole e frasi, della prossimità delle parole a una certa distanza l'una dall'altra o di corrispondenze ponderate. CONTAINSTABLE viene utilizzata la [dalla clausola](../../t-sql/queries/from-transact-sql.md) di un [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione SELECT e viene fatto riferimento come se fosse un normale nome di tabella. Esegue una ricerca full-text di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in colonne indicizzate full-text che contengono tipi di dati basati su caratteri.  
  
 CONTAINSTABLE è utile per gli stessi tipi di corrispondenze di [predicato CONTAINS](../../t-sql/queries/contains-transact-sql.md) e utilizza le stesse condizioni di ricerca CONTAINS.  
  
 Tuttavia, a differenza di CONTAINS, le query che utilizzano la funzione CONTAINSTABLE restituiscono un valore di classificazione della pertinenza (RANK) e una chiave full-text (KEY) per ogni riga.  Per informazioni sulle forme di ricerca full-text supportate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CONTAINSTABLE   
( table , { column_name | ( column_list ) | * } , ' <contains_search_condition> '   
     [ , LANGUAGE language_term]   
  [ , top_n_by_rank ]   
)   
  
<contains_search_condition> ::=   
    { <simple_term>   
    | <prefix_term>   
    | <generation_term>   
    | <generic_proximity_term>   
    | <custom_proximity_term>   
    |  <weighted_term>   
    }   
    | { ( <contains_search_condition> )   
    { { AND | & } | { AND NOT | &! } | { OR | | } }   
     <contains_search_condition> [ ...n ]   
    }  
  
<simple_term> ::=   
     { word | "phrase" }  
<prefix term> ::=   
     { "word*" | "phrase*" }   
<generation_term> ::=   
     FORMSOF ( { INFLECTIONAL | THESAURUS } , <simple_term> [ ,...n ] )   
  
<generic_proximity_term> ::=   
     { <simple_term> | <prefix_term> } { { { NEAR | ~ }   
     { <simple_term> | <prefix_term> } } [ ...n ] }  
  
<custom_proximity_term> ::=   
  NEAR (   
     {  
        { <simple_term> | <prefix_term> } [ ,…n ]  
     |  
        ( { <simple_term> | <prefix_term> } [ ,…n ] )   
      [, <maximum_distance> [, <match_order> ] ]  
     }  
       )   
  
      <maximum_distance> ::= { integer | MAX }  
      <match_order> ::= { TRUE | FALSE }   
  
<weighted_term> ::=   
     ISABOUT  
    ( { {   
  <simple_term>   
  | <prefix_term>   
  | <generation_term>   
  | <proximity_term>   
  }   
   [ WEIGHT ( weight_value ) ]   
   } [ ,...n ]   
    )  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *table*  
 Nome di una tabella indicizzata full-text. *tabella* può essere uno - due, tre o nome di oggetto di database in quattro parti. L'esecuzione della ricerca in una vista può interessare solo una tabella di base con indicizzazione full-text.  
  
 *tabella* non è possibile specificare un nome di server e non può essere utilizzato nelle query su server collegati.  
  
 *column_name*  
 Nome di una o più colonne indicizzate per la ricerca full-text. Le colonne possono essere di tipo **char**, **varchar**, **nchar**, **nvarchar**, **testo**, **ntext**, **immagine**, **xml**, **varbinary**, o **varbinary (max)**.  
  
 *column_list*  
 Viene indicato che è possibile specificare più colonne, separate da virgola. *column_list* devono essere racchiusi tra parentesi. A meno che non *language_term* è specificato, la lingua di tutte le colonne di *column_list* devono essere uguali.  
  
 \*  
 Specifica che tutti full-text indicizzate colonne *tabella* deve essere utilizzato per cercare la condizione di ricerca specificato. A meno che non *language_term* è specificato, la lingua di tutte le colonne della tabella deve essere lo stesso.  
  
 LINGUA *language_term*  
 È la lingua il cui risorse verranno utilizzate per la suddivisione delle parole, lo stemming e thesaurus e parole non significative (o [parola non significativa](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) rimozione come parte della query. Questo parametro è facoltativo e può essere specificato come valore stringa, intero o esadecimale corrispondente all'identificatore delle impostazioni locali (LCID) di una lingua. Se *language_term* è specificato, la lingua rappresentata verrà applicata a tutti gli elementi della condizione di ricerca. Se non si specifica alcun valore, verrà utilizzata la lingua full-text della colonna.  
  
 Se documenti di lingue diverse vengono archiviati insieme come oggetti BLOB in una singola colonna, l'identificatore delle impostazioni locali (LCID) di un documento specifico determina la lingua da utilizzare per indicizzarne il contenuto. Quando una query su una colonna di questo tipo, specifica *LANGUAGE * * language_term* può aumentare la probabilità di ottenere una corrispondenza.  
  
 Quando specificato come stringa, *language_term* corrisponde al **alias** valore colonna il [Sys. syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) vista di compatibilità.  La stringa deve essere racchiuso tra virgolette singole, come '*language_term*'. Quando specificato come un numero intero, *language_term* è l'identificatore LCID effettivo che identifica la lingua. Quando specificato come valore esadecimale, *language_term* è 0x seguito dal valore esadecimale del LCID. Il valore esadecimale non deve superare le otto cifre, inclusi gli zeri iniziali.  
  
 Se il valore è nel formato di double byte character set (DBCS), [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene convertito in Unicode.  
  
 Se la lingua specificata non è valida o non vi sono risorse installate corrispondenti a tale lingua, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore. Per utilizzare le risorse di lingua neutra, specificare 0x0 *language_term*.  
  
 *top_n_by_rank*  
 Specifica che solo il  *n*  corrispondenze di pertinenza maggiore in ordine decrescente, vengono restituite. Si applica solo quando un valore intero,  *n* , viene specificato. Se il parametro *top_n_by_rank* viene combinato con altri parametri, la query potrebbe restituire un numero inferiore di righe rispetto al numero di righe effettivamente corrispondenti a tutti i predicati. *top_n_by_rank* consente di migliorare le prestazioni delle query richiamando solo i risultati più rilevanti.  
  
 <contains_search_condition>  
 Specifica il testo da cercare nella *column_name* e le condizioni per una corrispondenza. Per informazioni sulle condizioni di ricerca, vedere [CONTAINS &#40; Transact-SQL &#41; ](../../t-sql/queries/contains-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 I predicati e le funzioni full-text possono essere utilizzati in una singola tabella, specificata in modo implicito nel predicato FROM. Per cercare in più tabelle, utilizzare una tabella unita in join nella clausola FROM, che consente di eseguire una ricerca in un set di risultati prodotto da due o più tabelle.  
  
 La tabella restituita include una colonna denominata **chiave** che contiene i valori chiave full-text. Ogni tabella indicizzata full-text è una colonna i cui valori sono necessariamente univoci e i valori restituiti nella **chiave** colonna sono i valori di chiave full-text delle righe che soddisfano i criteri di selezione specificati di ricerca contains condizione. Il **TableFulltextKeyColumn** proprietà, ottenuta dalla funzione OBJECTPROPERTYEX, fornisce l'identità di questa colonna chiave univoca. Per ottenere l'ID della colonna associata alla chiave full-text dell'indice full-text, utilizzare **fulltext_indexes**. Per ulteriori informazioni, vedere [fulltext_indexes &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
 Per ottenere le righe desiderate dalla tabella originale, specificare un join per le righe CONTAINSTABLE. La forma tipica della clausola FROM per un'istruzione SELECT che utilizza la funzione CONTAINSTABLE è la seguente:  
  
```  
SELECT select_list  
FROM table AS FT_TBL INNER JOIN  
   CONTAINSTABLE(table, column, contains_search_condition) AS KEY_TBL  
   ON FT_TBL.unique_key_column = KEY_TBL.[KEY];  
```  
  
 La tabella restituita dalla funzione CONTAINSTABLE include una colonna denominata **RANK**. Il **RANK** colonna è un valore (da 0 a 1000) per ogni riga che indica come una riga di corrispondenza tra i criteri di selezione. Questo valore di pertinenza viene normalmente utilizzato nell'istruzione SELECT in uno dei modi seguenti:  
  
-   Nella clausola ORDER BY per ottenere le righe a cui sono stati assegnati i valori di pertinenza massimi nelle prime posizioni della tabella.  
  
-   Nell'elenco di selezione per visualizzare il valore di pertinenza assegnato a ogni riga.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione sono disponibili solo per gli utenti che dispongono dei privilegi appropriati per l'istruzione SELECT nella tabella o nelle colonne della tabella a cui viene fatto riferimento.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-example"></a>A. Esempio semplice  
 Nell'esempio seguente crea e popola una tabella semplice delle due colonne, elenco di 3 regioni e i colori nei flag. L'it crea e popola un catalogo full-text e l'indice della tabella. Il **CONTAINSTABLE** viene illustrata la sintassi. In questo esempio viene illustrato come il valore di pertinenza si espande superiore quando il valore di ricerca viene soddisfatta più volte. In ultima query, Tanzania che contiene sia verde e nera ha priorità più alta rispetto Italia che contengono solo uno dei colori richiesti.  
  
```  
CREATE TABLE Flags (Country nvarchar(30) NOT NULL, FlagColors varchar(200));  
CREATE UNIQUE CLUSTERED INDEX FlagKey ON Flags(Country);  
INSERT Flags VALUES ('France', 'Blue and White and Red');  
INSERT Flags VALUES ('Italy', 'Green and White and Red');  
INSERT Flags VALUES ('Tanzania', 'Green and Yellow and Black and Yellow and Blue');  
SELECT * FROM Flags;  
GO  
  
CREATE FULLTEXT CATALOG TestFTCat;  
CREATE FULLTEXT INDEX ON Flags(FlagColors) KEY INDEX FlagKey ON TestFTCat;  
GO   
  
SELECT * FROM Flags;  
SELECT * FROM CONTAINSTABLE (Flags, FlagColors, 'Green') ORDER BY RANK DESC;  
SELECT * FROM CONTAINSTABLE (Flags, FlagColors, 'Green or Black') ORDER BY RANK DESC;  
```  
  
### <a name="b-returning-rank-values"></a>B. Restituzione di valori di rango  
 Nell'esempio seguente viene eseguita una ricerca dei nomi di prodotto che includono le parole "frame", "wheel" o "tire". Ogni parola viene ponderata in modo diverso. Per ogni riga restituita corrispondente ai criteri di ricerca, viene illustrata la prossimità relativa (valore di rango assegnato) della corrispondenza. Le righe di rango superiore vengono restituite per prime.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Name, KEY_TBL.RANK  
    FROM Production.Product AS FT_TBL   
        INNER JOIN CONTAINSTABLE(Production.Product, Name,   
        'ISABOUT (frame WEIGHT (.8),   
        wheel WEIGHT (.4), tire WEIGHT (.2) )' ) AS KEY_TBL  
            ON FT_TBL.ProductID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
### <a name="c-returning-rank-values-greater-than-a-specified-value"></a>C. Restituzione di valori di rango superiori a un valore specificato  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
 Nell'esempio seguente viene utilizzato NEAR per cercare "`bracket`" e "`reflector`" vicini nella tabella `Production.Document`. Vengono restituite solo le righe con un valore di pertinenza maggiore o uguale a 50.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable   
INNER JOIN CONTAINSTABLE(Production.Document, Document,  
  'NEAR(bracket, reflector)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 50  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
> [!NOTE]  
>  Se una query full-text non specifica un valore intero come distanza massima, un documento che contiene solo riscontri il cui gap è maggiore di 100 termini logici non soddisferà i requisiti NEAR e il relativo rango sarà pari a 0.  
  
### <a name="d-returning-top-5-ranked-results-using-topnbyrank"></a>D. Restituzione dei primi 5 valori con pertinenza maggiore utilizzando top_n_by_rank  
 Nell'esempio seguente viene restituita la descrizione dei primi 5 prodotti la cui colonna `Description` include la parola "aluminum" accanto alla parola "light" o "lightweight".  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY];  
GO  
```  
  
 `GO`  
  
### <a name="e-specifying-the-language-argument"></a>E. Utilizzo dell'argomento LANGUAGE  
 Nell'esempio seguente viene illustrato l'utilizzo dell'argomento `LANGUAGE`.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)',  
      LANGUAGE N'English',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY];  
GO  
```  
  
> [!NOTE]  
>  Il linguaggio *language_term* argumentis non necessarie per l'uso *top_n_by_rank.*  
  
## <a name="see-also"></a>Vedere anche  
 [Limitazione dei risultati della ricerca mediante RANK](../../relational-databases/search/limit-search-results-with-rank.md)   
 [Query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md)   
 [Creare query di ricerca full-text &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [Query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)  
  
  
