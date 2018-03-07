---
title: CONTAINS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTAINS_TSQL
- CONTAINS
dev_langs:
- TSQL
helpviewer_keywords:
- precise or fuzzy (less precise) matches [full-text search]
- CONTAINS predicate (Transact-SQL)
- conditions [SQL Server], CONTAINS
- fuzzy (less precise) word or phrase search [full-text search]
- word weighting values [full-text search]
- word searches [full-text search]
- weighted values [full-text search]
- LANGUAGE option
- word inflectionally generated from another [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- word near another word search [full-text search]
- full-text search [SQL Server], searching on a property
- proximity searches [full-text search]
- less precise (fuzzy) searches [full-text search]
- property searching [SQL Server], searching on a property
- inflectional forms [full-text search]
- prefix searches [full-text search]
ms.assetid: 996c72fc-b1ab-4c96-bd12-946be9c18f84
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 81b231ce95ae1b87bbda2f2fd786d12cb709e9fe
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="contains-transact-sql"></a>CONTAINS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Cerca corrispondenze precise o fuzzy (meno precise) a singole parole e frasi, parole a una certa distanza una dall'altra o corrispondenze ponderate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. CONTAINS è un predicato utilizzato nella [clausola WHERE](../../t-sql/queries/where-transact-sql.md) di un [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione SELECT per eseguire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ricerca full-text full-text indicizzate colonne contenenti tipi di dati di tipo carattere.  
  
 Il predicato CONTAINS consente di cercare:  
  
-   Una parola o una frase.  
  
-   Il prefisso di una parola o di una frase.  
  
-   Una parola accanto a una parola specifica.  
  
-   Una parola generata da un'altra per flessione, ad esempio le parole guida, guidare, guidando e guidare derivanti dalla radice guida.  
  
-   Una parola sinonimo di un'altra parola utilizzando il thesaurus, ad esempio le parole alluminio e acciaio possono essere sinonimi della parola metallo.  
  
 Per informazioni sulle forme di ricerca full-text supportate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md).  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CONTAINS (   
     {   
        column_name | ( column_list )   
      | *   
      | PROPERTY ( { column_name }, 'property_name' )    
     }   
     , '<contains_search_condition>'  
     [ , LANGUAGE language_term ]  
   )   
  
<contains_search_condition> ::=   
  {   
      <simple_term>   
    | <prefix_term>   
    | <generation_term>   
    | <generic_proximity_term>   
    | <custom_proximity_term>   
    | <weighted_term>   
    }   
  |   
    { ( <contains_search_condition> )   
        [ { <AND> | <AND NOT> | <OR> } ]   
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
   ( {   
        {   
          <simple_term>   
        | <prefix_term>   
        | <generation_term>   
        | <proximity_term>   
        }   
      [ WEIGHT ( weight_value ) ]   
      } [ ,...n ]   
   )   
  
<AND> ::=   
  { AND | & }  
  
<AND NOT> ::=   
  { AND NOT | &! }  
  
<OR> ::=   
  { OR | | }  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *column_name*  
 Nome di una colonna con indicizzazione full-text della tabella specificata nella clausola FROM. Le colonne possono essere di tipo **char**, **varchar**, **nchar**, **nvarchar**, **testo**, **ntext**, **immagine**, **xml**, **varbinary**, o **varbinary (max)**.  
  
 *column_list*  
 Specifica due o più colonne, separate da virgole. *column_list* devono essere racchiusi tra parentesi. A meno che non *language_term* è specificato, la lingua di tutte le colonne di *column_list* devono essere uguali.  
  
 \*  
 Indica che la query cerca tutte le colonne con indicizzazione full-text nella tabella specificata nella clausola FROM per la condizione di ricerca specificato. Le colonne nella clausola CONTAINS devono appartenere a una singola tabella che include un indice full-text. A meno che non *language_term* è specificato, la lingua di tutte le colonne della tabella deve essere lo stesso.  
  
 PROPRIETÀ ( *column_name* , '*property_name*')  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Specifica una proprietà di documento in cui cercare la condizione di ricerca specificata.  
  
> [!IMPORTANT]  
>  Per la query restituisca delle righe, *property_name* deve essere specificato nella proprietà di ricerca elenco dell'indice full-text e l'indice full-text deve contenere voci specifiche di proprietà *property_name*. Per altre informazioni, vedere [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 LINGUA *language_term*  
 È la lingua da utilizzare per la suddivisione delle parole, stemming, espansioni del thesaurus e sostituzioni e parole non significative (o [parola non significativa](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) rimozione come parte della query. Questo parametro è facoltativo.  
  
 Se documenti di lingue diverse vengono archiviati insieme come oggetti BLOB in una singola colonna, l'identificatore delle impostazioni locali (LCID) di un documento specifico determina la lingua da utilizzare per indicizzarne il contenuto. Quando si eseguono query su una colonna di questo tipo, specifica di linguaggio *language_term* può aumentare la probabilità di ottenere una corrispondenza.  
  
 *language_term* può essere specificato come stringa, intero o esadecimale corrispondente all'identificatore LCID della lingua. Se *language_term* è specificata, la lingua rappresentata viene applicata a tutti gli elementi della condizione di ricerca. Se non si specifica alcun valore, verrà utilizzata la lingua full-text della colonna.  
  
 Quando specificato come stringa, *language_term* corrisponde al **alias** valore colonna il [Sys. syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) vista di compatibilità. La stringa deve essere racchiuso tra virgolette singole, come '*language_term*'. Quando specificato come un numero intero, *language_term* è l'identificatore LCID effettivo che identifica la lingua. Quando specificato come valore esadecimale, *language_term* è 0x seguito dal valore esadecimale del LCID. Il valore esadecimale non deve superare le otto cifre, inclusi gli zeri iniziali.  
  
 Se il valore è nel formato di double byte character set (DBCS), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lo converte in Unicode.  
  
 Se la lingua specificata non è valida o non vi sono risorse installate corrispondenti a tale lingua, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore. Per utilizzare le risorse di lingua neutra, specificare 0x0 *language_term*.  
  
 \<*contains_search_condition*>  
 Specifica il testo da cercare nella *column_name* e le condizioni per una corrispondenza.  
  
*\<contains_search_condition >* è **nvarchar**. Viene eseguita una conversione implicita quando si utilizza come input un tipo di dati character diverso. Varchar (max) e nvarchar (max) i tipi di dati di stringa di grandi dimensioni non possono essere utilizzati. Nell'esempio seguente la variabile `@SearchWord`, definita come `varchar(30)`, causa una conversione implicita nel predicato `CONTAINS`.
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 "Lo sniffing dei parametri" funziona nella conversione, utilizzare **nvarchar** per ottenere prestazioni migliori. Nell'esempio dichiarare `@SearchWord` come `nvarchar(30)`.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 È inoltre possibile utilizzare l'hint per la query OPTIMIZE FOR per i casi in cui viene generato un piano non ottimale.  
  
 *word*  
 Stringa di caratteri senza spazi o punteggiatura.  
  
 *phrase*  
 Una o più parole separate da uno spazio.  
  
> [!NOTE]  
>  In alcune lingue, ad esempio quelle asiatiche, sono possibili frasi composte da una o più parole non separate da alcuno spazio.  
  
\<simple_term>  
Specifica che deve essere trovata l'esatta corrispondenza di una parola o di una frase. Esempi di termini semplici validi sono "copri capo", copricapo e "Microsoft SQL Server". Le frasi devono essere racchiuse tra virgolette doppie (""). Parole in una frase devono trovarsi nello stesso ordine come specificato in  *\<contains_search_condition >* come vengono visualizzati nella colonna del database. La distinzione tra maiuscole e minuscole non è rilevante per la ricerca di caratteri nella parola o nella frase. Le parole non significative (o [parole non significative](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) (ad esempio a e, o) in colonne indicizzate full-text non vengono archiviati nell'indice full-text. Se una parola non significativa viene utilizzata nella ricerca di una singola parola, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un messaggio di errore che indica che la query contiene solo parole non significative. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include un elenco standard di parole non significative, disponibile nella directory \Mssql\Binn\FTERef di ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La punteggiatura viene ignorata. `CONTAINS(testing, "computer failure")`, pertanto, consente di trovare una riga contenente il valore "Where is my computer? Failure to find it would be expensive". Per ulteriori informazioni sul comportamento del word breaker, vedere [configurare e gestire Word breaker e stemmer per la ricerca](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
 \<prefix_term>  
 Specifica che devono essere trovate parole o frasi che iniziano con il testo specificato. Racchiudere un prefisso tra virgolette doppie ("") e aggiungere un asterisco (\*) prima delle virgolette finale, in modo che tutto il testo inizia con il termine semplice specificato prima dell'asterisco esiste una corrispondenza. La clausola deve essere specificata nel seguente modo: `CONTAINS (column, '"text*"')` L'asterisco corrisponde a zero, uno o più caratteri della parola o delle parole radice della parola o della frase. Se il testo e l'asterisco non sono racchiusi tra virgolette doppie, per cui vengono letti dal predicato come `CONTAINS (column, 'text*')`, nella ricerca full-text l'asterisco viene interpretato come carattere e viene eseguita la ricerca esatta di `text*`. Il motore full-text non troverà parole con l'asterisco (\*) perché word breaker ignorano in genere tali caratteri.  
  
 Quando  *\<prefix_term >* è una frase, ogni parola della frase viene considerata un prefisso distinto. Una query che specifica il prefisso "sviluppo foto*", pertanto, consente di individuare tutte le righe che includono il testo "sviluppo fotografie", "sviluppo fotografie e ritocco" e così via.  
  
 \<generation_term>  
 Specifica che devono essere trovate le parole i cui termini semplici includono varianti della parola originale da cercare.  
  
 INFLECTIONAL  
 Specifica che deve essere utilizzato lo stemmer specifico della lingua per il termine semplice specificato. Il comportamento dello stemmer dipende dalle regole di stemming di ogni lingua specifica. Alla lingua neutra non è associato alcuno stemmer. Per individuare lo stemmer corretto, viene utilizzata la lingua delle colonne in cui viene eseguita la ricerca. Se *language_term* è specificato, lo stemmer corrispondente che viene utilizzata una lingua.  
  
 Un determinato  *\<simple_term >* all'interno di un  *\<generation_term >* non corrisponderanno sia sostantivi che verbi.  
  
 THESAURUS  
 Specifica che verrà utilizzato il thesaurus corrispondente alla lingua full-text per le colonne oppure alla lingua specificata nella query. Il modello o i modelli da più lungo di  *\<simple_term >* vengono confrontati con il thesaurus e vengono generati termini aggiuntivi per espandere o sostituire il modello originale. Se non viene trovata una corrispondenza per tutta o parte di  *\<simple_term >*, la parte non corrispondente viene considerata come un *simple_term*. Per ulteriori informazioni sul thesaurus ricerca full-text, vedere [configurare e gestire i file del Thesaurus per la ricerca Full-Text](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).  
  
 \<generic_proximity_term>  
 Specifica che devono essere trovate parole o frasi incluse nel documento in cui viene eseguita la ricerca.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]È consigliabile utilizzare \<custom_proximity_term >.  
  
 NEAR | ~  
 Indica che le parole o le frasi a sinistra e a destra dell'operatore NEAR o ~ devono essere incluse in un documento in modo che venga restituita una corrispondenza. È necessario specificare due termini di ricerca. Un termine di ricerca può essere una parola o una frase che è delimitata da virgolette doppie ("*frase*").  
  
 È possibile concatenare più termini vicini, come in `a NEAR b NEAR c` o `a ~ b ~ c`. I termini vicini concatenati devono essere tutti presenti nel documento affinché venga restituita una corrispondenza.  
  
 Ad esempio, `CONTAINS(*column_name*, 'fox NEAR chicken')` e `CONTAINSTABLE(*table_name*, *column_name*, 'fox ~ chicken')` restituirebbero tutti i documenti nella colonna specificata che contengono sia "volpe" che "pollo". CONTAINSTABLE, inoltre, restituisce una pertinenza per ogni documento in base alla prossimità delle parole "volpe" e "pollo". Ad esempio, se un documento contiene la frase "La volpe mangia il pollo", il relativo rango è elevato perché i termini sono più vicini uno all'altro che negli altri documenti.  
  
 Per ulteriori informazioni sui termini vicini generici, vedere [cercare parole vicine a un'altra parola con NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).  
  
 \<custom_proximity_term>  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
 Specifica una corrispondenza di parole o frasi e facoltativamente la distanza massima consentita tra termini di ricerca. è inoltre possibile specificare che i termini di ricerca devono trovarsi nell'ordine esatto in cui vengono specificati (\<match_order >).  
  
 Un termine di ricerca può essere una parola o una frase che è delimitata da virgolette doppie ("*frase*"). Ogni termine specificato deve trovarsi nel documento affinché venga restituita una corrispondenza. È necessario specificare almeno due termini di ricerca. Il numero massimo di termini di ricerca è 64.  
  
 Per impostazione predefinita, il termine vicino personalizzato restituisce qualsiasi riga contenente i termini specificati indipendentemente dalla distanza e dall'ordine. Ad esempio, per trovare una corrispondenza con la query seguente, un documento dovrebbe semplicemente contenere `term1` e "`term3 term4`" in qualsiasi punto e in qualsiasi ordine:  
  
```  
CONTAINS(column_name, 'NEAR(term1,"term3 term4")')  
```  
  
 I parametri facoltativi sono i seguenti:  
  
 \<maximum_distance>  
 Specifica la distanza massima consentita tra i termini di ricerca all'inizio e alla fine di una stringa affinché tale stringa possa essere ritenuta una corrispondenza.  
  
 *integer*  
 Specifica un intero positivo compreso tra 0 e 4294967295. Questo valore determina il numero di termini non di ricerca che possono esistere tra il primo e l'ultimo termine di ricerca, esclusi eventuali termini di ricerca specificati aggiuntivi.  
  
 Ad esempio, la query seguente cerca `AA` e `BB`, in qualsiasi ordine, entro una distanza massima di cinque.  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB),5)')  
```  
  
 La stringa `AA one two three four five BB` sarebbe una corrispondenza. Nell'esempio seguente, la query specifica Cerca tre termini di ricerca, `AA`, `BB`, e `CC` entro una distanza massima di cinque:  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB,CC),5)')  
```  
  
 La query troverebbe una corrispondenza per la stringa seguente in cui la distanza totale è cinque:  
  
 `BB   one two   CC   three four five A  A`  
  
 Si noti che un termine, di ricerca interna `CC`, non viene conteggiato.  
  
 **MAX**  
 Restituisce le righe che contengono i termini specificati indipendentemente dalla distanza esistente tra di essi. Impostazione predefinita.  
  
 \<match_order>  
 Specifica se i termini devono trovarsi nell'ordine specificato che deve essere restituito da una query di ricerca. Per specificare \<match_order >, è necessario specificare anche \<distanza_massima >.  
  
 \<match_order > accetta uno dei valori seguenti:  
  
 **TRUE**  
 Applica l'ordine specificato all'interno dei termini. Ad esempio, `NEAR(A,B)` corrisponderebbe solo a `A … B`.  
  
 **FALSE**  
 Ignora l'ordine specificato. Ad esempio, `NEAR(A,B)` corrisponderebbe sia a `A … B` sia a `B … A`.  
  
 Impostazione predefinita.  
  
 Ad esempio, il termine vicino seguente cerca le parole "`Monday`", "`Tuesday`" e "`Wednesday`" nell'ordine specificato indipendentemente dalla distanza esistente tra di essi:  
  
```  
CONTAINS(column_name, 'NEAR ((Monday, Tuesday, Wednesday), MAX, TRUE)')  
```  
  
 Per ulteriori informazioni sull'uso di termini di prossimità personalizzato, vedere [cercare parole vicine a un'altra parola con NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).  
  
 \<weighted_term>  
 Specifica che le righe restituite dalla query corrispondono a un elenco di parole e di frasi, a ognuna delle quali può essere associato un valore di ponderazione facoltativo.  
  
 ISABOUT  
 Specifica il  *\<weighted_term >* (parola chiave).  
  
 Peso (*weight_value*)  
 Specifica un valore di ponderazione compreso tra 0.0 e 1.0. Ogni componente di  *\<weighted_term >* può includere un *weight_value*. *weight_value* è un modo per modificare una delle varie parti di una query influiscono sul valore di pertinenza assegnato a ogni riga corrispondente alla query. PESO non influenzare i risultati della query CONTAINS, ma di priorità influisce sul peso in [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) query.  
  
> [!NOTE]  
>  Il separatore decimale è sempre un punto, indipendentemente dalle impostazioni locali del sistema operativo.  
  
 { AND | & } | { AND NOT | &! } | { OR | | }   
 Specifica un'operazione logica tra due condizioni di ricerca del predicato CONTAINS.  
  
 { AND | & }  
 Indica che devono essere soddisfatte entrambe le condizioni di ricerca del predicato CONTAINS. Per rappresentare l'operatore AND, è possibile utilizzare il carattere e commerciale (&) anziché la parola chiave AND.  
  
 {E NON | &! }  
 Indica che la seconda condizione di ricerca non deve essere soddisfatta. Per rappresentare l'operatore AND NOT, è possibile utilizzare il carattere e commerciale seguito dal punto esclamativo (&!) anziché la parola chiave AND NOT.  
  
 { OR | | }  
 Indica che deve essere soddisfatta una delle due condizioni di ricerca del predicato CONTAINS. Per rappresentare l'operatore OR, è possibile utilizzare il carattere barra (|) anziché la parola chiave OR.  
  
 Quando  *\<contains_search_condition >* include gruppi tra parentesi, queste tra parentesi gruppi vengono valutati per primi. In seguito alla valutazione dei gruppi tra parentesi, gli operatori logici che includono condizioni di ricerca vengono valutati in base alle regole seguenti:  
  
-   L'operatore NOT viene applicato prima dell'operatore AND.  
  
-   L'operatore NOT può essere utilizzato solo dopo l'operatore AND, ad esempio in AND NOT. L'operatore OR NOT non è consentito. Non è possibile specificare l'operatore NOT prima del primo termine. `CONTAINS (mycolumn, 'NOT "phrase_to_search_for" ' )`, ad esempio, non è valido:  
  
-   L'operatore AND viene applicato prima dell'operatore OR.  
  
-   Gli operatori booleani dello stesso tipo (AND, OR) sono associativi e pertanto possono essere applicati in qualsiasi ordine.  
  
 *n*  
 Segnaposto che indica la possibilità di specificare più termini e più condizioni di ricerca del predicato CONTAINS.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 I predicati e le funzioni full-text possono essere utilizzati in una singola tabella, specificata in modo implicito nel predicato FROM. Per cercare in più tabelle, utilizzare una tabella unita in join nella clausola FROM, che consente di eseguire una ricerca in un set di risultati prodotto da due o più tabelle.  
  
 I predicati full-text non sono consentiti nel [clausola OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) quando il livello di compatibilità del database è impostato su 100.  
  
## <a name="querying-remote-servers"></a>Esecuzione di query in server remoti  
 È possibile utilizzare un nome composto da quattro parti in CONTAINS o [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) predicato per eseguire una query full-text indicizzate le colonne delle tabelle di destinazione in un server collegato. Per preparare un server remoto alla ricezione di query full-text, creare un indice full-text delle tabelle di destinazione e delle colonne nel server remoto, quindi aggiungere il server remoto come server collegato.  
  
## <a name="comparison-of-like-to-full-text-search"></a>Confronto tra LIKE e la ricerca full-text  
 Contrariamente alla ricerca full-text, il predicato [LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] funziona unicamente con i modelli di caratteri. Non è inoltre possibile utilizzare il predicato LIKE per eseguire query su dati binari formattati. Inoltre, l'esecuzione di una query LIKE su una grande quantità di dati di testo non strutturati è molto più lenta dell'esecuzione di una query full-text equivalente sugli stessi dati. Una query LIKE eseguita su milioni di righe di dati di testo può richiedere diversi minuti, mentre per una query full-text sugli stessi dati possono essere necessari al massimo pochi secondi, a seconda del numero di righe restituite e delle relative dimensioni. Si tenga inoltre presente che LIKE esegue unicamente un'analisi modello semplice di un'intera tabella. Una query full-text tiene invece conto della lingua, applicando trasformazioni specifiche durante l'esecuzione della query e dell'indice, ad esempio il filtro delle parole non significative ed espansioni flessive e del thesaurus. Tali trasformazioni consentono alle query full-text di migliorare la chiamata e il rango finale dei risultati.  
  
## <a name="querying-multiple-columns-full-text-search"></a>Esecuzione di query su più colonne (ricerca full-text)  
 È possibile eseguire una query su più colonne specificando un elenco di colonne in cui eseguire ricerche. Le colonne devono appartenere alla stessa tabella.  
  
 Ad esempio, la query CONTAINS seguente cerca il termine `Red` nel `Name` e `Color` colonne di `Production.Product` tabella del [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database di esempio.  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Name, Color   
FROM Production.Product  
WHERE CONTAINS((Name, Color), 'Red');  
```  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-contains-with-simpleterm"></a>A. Utilizzo di CONTAINS con \<simple_term >  
 Nell'esempio seguente vengono trovati tutti i prodotti il cui prezzo è `$80.99` e contenenti la parola `Mountain`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain');  
GO  
```  
  
### <a name="b-using-contains-and-phrase-with-simpleterm"></a>B. Utilizzo di CONTAINS e una frase con \<simple_term >  
 Nell'esempio seguente vengono restituiti tutti i prodotti che contengono la frase `Mountain` o `Road`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' Mountain OR Road ')  
GO  
```  
  
### <a name="c-using-contains-with-prefixterm"></a>C. Utilizzo di CONTAINS con \<prefix_term >  
 Nell'esempio seguente vengono restituiti tutti i nomi di prodotto della colonna `Name` contenenti almeno una parola che inizia con il prefisso chain.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' "Chain*" ');  
GO  
```  
  
### <a name="d-using-contains-and-or-with-prefixterm"></a>D. Utilizzo di CONTAINS e OR con \<prefix_term >  
 Nell'esempio seguente vengono restituite tutte le descrizioni di categoria contenenti stringhe con il prefisso `chain` o `full`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, '"chain*" OR "full*"');  
GO  
```  
  
### <a name="e-using-contains-with-proximityterm"></a>E. Utilizzo di CONTAINS con \<proximity_term >  
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Le ricerche di esempio seguente il `Production.ProductReview` tabella per tutti i commenti che contengono la parola `bike` all'interno di 10 termini della parola "`control`" e nell'ordine specificato (ovvero dove "`bike`"precede"`control`").  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments , 'NEAR((bike,control), 10, TRUE)');  
GO  
```  
  
### <a name="f-using-contains-with-generationterm"></a>F. Utilizzo di CONTAINS con \<generation_term >  
 Nell'esempio seguente viene eseguita la ricerca di tutti i prodotti con parole derivate da `ride`, ad esempio riding, ridden e così via.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, ' FORMSOF (INFLECTIONAL, ride) ');  
GO  
```  
  
### <a name="g-using-contains-with-weightedterm"></a>G. Utilizzo di CONTAINS con \<weighted_term >  
 Nell'esempio seguente viene eseguita la ricerca di tutti i nomi di prodotto contenenti la parola `performance`, `comfortable` o `smooth`. Ogni parola viene ponderata in modo diverso.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, 'ISABOUT (performance weight (.8),   
comfortable weight (.4), smooth weight (.2) )' );  
GO  
```  
  
### <a name="h-using-contains-with-variables"></a>H. Utilizzo di CONTAINS con variabili  
 Nell'esempio seguente viene utilizzata una variabile anziché un termine di ricerca specifico.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'Performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
GO  
```  
  
### <a name="i-using-contains-with-a-logical-operator-and"></a>I. Utilizzo di CONTAINS con un operatore logico (AND)  
 Nell'esempio seguente viene utilizzata la tabella ProductDescription del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . La query viene utilizzato il predicato CONTAINS per cercare le descrizioni in cui l'ID di descrizione non è uguale a 5 e la descrizione contiene le parole `Aluminum` e la parola `spindle`. Nella condizione di ricerca viene utilizzato l'operatore booleano AND.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'Aluminum AND spindle');  
GO  
```  
  
### <a name="j-using-contains-to-verify-a-row-insertion"></a>J. Utilizzo di CONTAINS per verificare l'inserimento di una riga  
 Nell'esempio seguente viene utilizzato il predicato CONTAINS in una sottoquery SELECT. Se si utilizza il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], la query consente di ottenere il valore di commento per tutti i commenti della tabella ProductReview per un ciclo specifico. Nella condizione di ricerca viene utilizzato l'operatore booleano AND.  
  
```sql  
USE AdventureWorks2012;  
GO  
INSERT INTO Production.ProductReview   
  (ProductID, ReviewerName, EmailAddress, Rating, Comments)   
VALUES  
  (780, 'John Smith', 'john@fourthcoffee.com', 5,   
'The Mountain-200 Silver from AdventureWorks2008 Cycles meets and exceeds expectations. I enjoyed the smooth ride down the roads of Redmond');  
  
-- Given the full-text catalog for these tables is Adv_ft_ctlg,   
-- with change_tracking on so that the full-text indexes are updated automatically.  
WAITFOR DELAY '00:00:30';     
-- Wait 30 seconds to make sure that the full-text index gets updated.  
  
SELECT r.Comments, p.Name  
FROM Production.ProductReview AS r  
JOIN Production.Product AS p   
    ON r.ProductID = p.ProductID  
    AND r.ProductID = (SELECT ProductID  
FROM Production.ProductReview  
WHERE CONTAINS (Comments,   
    ' AdventureWorks2008 AND   
    Redmond AND   
    "Mountain-200 Silver" '));  
GO  
```  
  
### <a name="k-querying-on-a-document-property"></a>K. Query su una proprietà di documento  
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Tramite la query seguente viene eseguita una ricerca su una proprietà indicizzata, `Title`, nella colonna `Document` della tabella `Production.Document`. La query restituisce solo documenti la cui proprietà `Title` contiene la stringa `Maintenance` o `Repair`.  
  
> [!NOTE]  
>  Affinché una ricerca basata su proprietà restituisca righe, il filtro o i filtri che analizzano la colonna durante l'indicizzazione devono estrarre la proprietà specificata. L'indice full-text della tabella specificata deve inoltre essere stato configurato per includere la proprietà. Per altre informazioni, vedere [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Document 
FROM Production.Document  
WHERE CONTAINS(PROPERTY(Document,'Title'), 'Maintenance OR Repair');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione alla ricerca full-text](../../relational-databases/search/get-started-with-full-text-search.md)   
 [Creare e gestire i cataloghi Full-Text](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CREARE il catalogo full-text &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Creazione e gestione di indici full-text](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [Query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [Query con ricerca Full-Text](../../relational-databases/search/query-with-full-text-search.md)   
 [Ricerca full-Text](../../relational-databases/search/full-text-search.md)   
 [Creare query di ricerca full-text &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)   
 [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
