---
title: FREETEXT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREETEXT
- FREETEXT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- full-text search [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXT predicate (Transact-SQL)
- words in predicate [full-text search]
- column searches [full-text search]
ms.assetid: 2f199d3c-440e-4bcf-bdb5-82bb3994005d
caps.latest.revision: "44"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6687946e13dd6c801fcd256a0e463bdacb3779f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="freetext-transact-sql"></a>FREETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Predicato utilizzato nel [!INCLUDE[tsql](../../includes/tsql-md.md)] [clausola WHERE](../../t-sql/queries/where-transact-sql.md) di un [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione SELECT per eseguire un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ricerca full-text full-text indicizzate colonne contenenti tipi di dati di tipo carattere. Questo predicato esegue la ricerca dei valori che corrispondono al significato e non solo all'esatta formulazione delle parole nella condizione di ricerca. Quando si utilizza FREETEXT, il motore di query full-text esegue internamente le azioni seguenti sul *freetext_string*, assegna un peso a ogni termine e quindi cerca le corrispondenze:  
  
-   Separazione della stringa in singole parole in base ai delimitatori di parola (word breaking).  
  
-   Generazione di forme flessive delle parole (stemming).  
  
-   Identificazione di una lista di espansioni o sostituzioni dei termini in base alle corrispondenze nel thesaurus.  
  
> [!NOTE]  
>  Per informazioni sulle forme di ricerca full-text supportate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md).  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FREETEXT ( { column_name | (column_list) | * }   
          , 'freetext_string' [ , LANGUAGE language_term ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *column_name*  
 Nome di una o più colonne indicizzate full-text della tabella specificata nella clausola FROM. Le colonne possono essere di tipo **char**, **varchar**, **nchar**, **nvarchar**, **testo**, **ntext**, **immagine**, **xml**, **varbinary**, o **varbinary (max)**.  
  
 *column_list*  
 Viene indicato che è possibile specificare più colonne, separate da virgola. *column_list* devono essere racchiusi tra parentesi. A meno che non *language_term* è specificato, la lingua di tutte le colonne di *column_list* devono essere uguali.  
  
 \*  
 Specifica che tutte le colonne che sono state registrate per la ricerca full-text devono essere utilizzate per cercare il dato *freetext_string*. Se più di una tabella nella clausola FROM, \* deve essere qualificato dal nome della tabella. A meno che non *language_term* è specificato, la lingua di tutte le colonne della tabella deve essere lo stesso.  
  
 *freetext_string*  
 Testo da cercare nella *column_name*. È possibile specificare qualsiasi testo, comprese parole e frasi. Vengono generate corrispondenze se nell'indice full-text viene trovato un termine o vengono trovate le forme di un termine.  
  
 A differenza di CONTAINS e CONTAINSTABLE ricerca condizione where ed è una parola chiave, se utilizzata in *freetext_string* la parola 'and' viene considerata una parola non significativa, o [parola non significativa](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)e verrà ignorata.  
  
 Non è consentito utilizzare WEIGHT, FORMSOF, caratteri jolly, NEAR e altra sintassi. *freetext_string* sillabazione, le forme e passato attraverso il thesaurus.  
  
 *freetext_string* è **nvarchar**. Viene eseguita una conversione implicita quando si utilizza come input un tipo di dati character diverso. Varchar (max) e nvarchar (max) i tipi di dati di stringa di grandi dimensioni non possono essere utilizzati. Nell'esempio seguente la variabile `@SearchWord`, definita come `varchar(30)`, causa una conversione implicita nel predicato `FREETEXT`.  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 "Lo sniffing dei parametri" funziona nella conversione, utilizzare **nvarchar** per ottenere prestazioni migliori. Nell'esempio dichiarare `@SearchWord` come `nvarchar(30)`.  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 È inoltre possibile utilizzare l'hint per la query OPTIMIZE FOR nei casi in cui venga generato un piano non ottimale.  
  
 LINGUA *language_term*  
 Lingua le cui risorse verranno utilizzate per il word breaking, lo stemming, il thesaurus e la rimozione di parole non significative come parte della query. Questo parametro è facoltativo e può essere specificato come valore stringa, intero o esadecimale corrispondente all'identificatore delle impostazioni locali (LCID) di una lingua. Se *language_term* è specificato, la lingua rappresentata verrà applicata a tutti gli elementi della condizione di ricerca. Se non si specifica alcun valore, verrà utilizzata la lingua full-text della colonna.  
  
 Se documenti di lingue diverse vengono archiviati insieme come oggetti BLOB in una singola colonna, l'identificatore delle impostazioni locali (LCID) di un documento specifico determina la lingua da utilizzare per indicizzarne il contenuto. Quando una query su una colonna di questo tipo, specifica *LANGUAGE * * language_term* può aumentare la probabilità di ottenere una corrispondenza.  
  
 Quando specificato come stringa, *language_term* corrisponde alla **alias** valore della colonna nella [Sys. syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) vista di compatibilità.  La stringa deve essere racchiuso tra virgolette singole, come '*language_term*'. Quando specificato come un numero intero, *language_term* è l'identificatore LCID effettivo che identifica la lingua. Quando specificato come valore esadecimale, *language_term* è 0x seguito dal valore esadecimale del LCID. Il valore esadecimale non deve superare le otto cifre, inclusi gli zeri iniziali.  
  
 Se il valore è nel formato di double byte character set (DBCS), [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene convertito in Unicode.  
  
 Se la lingua specificata non è valida o non vi sono risorse installate corrispondenti a tale lingua, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore. Per utilizzare le risorse di lingua neutra, specificare 0x0 *language_term*.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 I predicati e le funzioni full-text possono essere utilizzati in una singola tabella, specificata in modo implicito nel predicato FROM. Per cercare in più tabelle, utilizzare una tabella unita in join nella clausola FROM, che consente di eseguire una ricerca in un set di risultati prodotto da due o più tabelle.  
  
Le query full-text che utilizzano il predicato FREETEXT sono meno precise delle query che utilizzano il predicato CONTAINS. Il motore di ricerca full-text di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifica le parole e le frasi importanti. Non viene fornito alcun significato speciale per tutte le parole chiave riservate o caratteri jolly che hanno generalmente significato specificato nella \<contains_search_condition > parametro del predicato CONTAINS.
  
 I predicati full-text non sono consentiti nel [clausola OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) quando il livello di compatibilità del database è impostato su 100.  
  
> [!NOTE]  
>  La funzione FREETEXTTABLE è utile per gli stessi tipi di corrispondenze del predicato FREETEXT. È possibile fare riferimento a questa funzione come un normale nome di tabella nel [dalla clausola](../../t-sql/queries/from-transact-sql.md) di un'istruzione SELECT. Per ulteriori informazioni, vedere [FREETEXTTABLE &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/freetexttable-transact-sql.md).  
  
## <a name="querying-remote-servers"></a>Esecuzione di query in server remoti  
 È possibile utilizzare un nome composto da quattro parti nel [CONTAINS](../../t-sql/queries/contains-transact-sql.md) o predicato FREETEXT per eseguire una query full-text indicizzate le colonne delle tabelle di destinazione in un server collegato. Per preparare un server remoto alla ricezione di query full-text, creare un indice full-text delle tabelle di destinazione e delle colonne nel server remoto, quindi aggiungere il server remoto come server collegato.  
  
## <a name="comparison-of-like-to-full-text-search"></a>Confronto tra LIKE e la ricerca full-text  
 Contrariamente alla ricerca full-text, il predicato [LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] funziona unicamente con i modelli di caratteri. Non è inoltre possibile utilizzare il predicato LIKE per eseguire query su dati binari formattati. Inoltre, l'esecuzione di una query LIKE su una grande quantità di dati di testo non strutturati è molto più lenta dell'esecuzione di una query full-text equivalente sugli stessi dati. Una query LIKE eseguita su milioni di righe di dati di testo può richiedere diversi minuti, mentre per una query full-text sugli stessi dati possono essere necessari al massimo pochi secondi, a seconda del numero di righe restituite.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-freetext-to-search-for-words-containing-specified-character-values"></a>A. Utilizzo di FREETEXT per la ricerca di parole contenenti valori di carattere specificati  
 Nell'esempio seguente viene eseguita la ricerca di tutti i documenti contenenti le parole associate a "vital", "safety" e "components".  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components' );  
GO  
```  
  
### <a name="b-using-freetext-with-variables"></a>B. Utilizzo di FREETEXT con variabili  
 Nell'esempio seguente viene utilizzata una variabile anziché un termine di ricerca specifico.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30);  
SET @SearchWord = N'high-performance';  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione alla ricerca full-text](../../relational-databases/search/get-started-with-full-text-search.md)   
 [Creare e gestire i cataloghi Full-Text](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CREARE il catalogo full-text &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Creazione e gestione di indici full-text](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [Query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md)   
 [Creare query di ricerca full-text &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
