---
title: CAST e CONVERT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CAST_TSQL
- CONVERT_TSQL
- CAST
- CONVERT
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- automatic data type conversion
- varbinary data type
- CONVERT function
- data types [SQL Server], converting
- large value data types
- implicit data type conversions
- image data type, converting
- explicit data type conversions [SQL Server]
- binary [SQL Server], converting
- text data type, converting
- date and time [SQL Server], cast and convert
- truncating conversions
- converting data types [SQL Server], conversion functions
- time zones [SQL Server]
- roundtrip conversions
ms.assetid: a87d0850-c670-4720-9ad5-6f5a22343ea8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 56326d7862c004ac056e329e6cc05f7bbe056aea
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="cast-and-convert-transact-sql"></a>CAST e CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Converte un'espressione da un tipo di dati a un altro.  
Ad esempio, gli esempi seguenti modificano il tipo di dati dell'input in due altri tipi di dati con livelli di precisione diversi.
```sql  
SELECT 9.5 AS Original, CAST(9.5 AS int) AS int, 
    CAST(9.5 AS decimal(6,4)) AS decimal;
SELECT 9.5 AS Original, CONVERT(int, 9.5) AS int, 
    CONVERT(decimal(6,4), 9.5) AS decimal;
```  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
|Originale   |INT    |Decimal |  
|----|----|----|  
|9.5 |9 |9.5000 |  

> [!TIP]
> Numerosi [esempi](#BKMK_examples) sono disponibili più avanti in questo argomento.  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for CAST:  
CAST ( expression AS data_type [ ( length ) ] )  
  
-- Syntax for CONVERT:  
CONVERT ( data_type [ ( length ) ] , expression [ , style ] )  
```  
  
## <a name="arguments"></a>Argomenti  
*expression*  
Qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) valida.
  
*data_type*  
Tipo di dati di destinazione. Include **xml**, **bigint** e **sql_variant**. Non è possibile usare i tipi di dati alias.
  
*length*  
Numero intero facoltativo che specifica la lunghezza del tipo di dati di destinazione. Il valore predefinito è 30.
  
*style*  
Espressione integer che specifica il modo in cui la funzione CONVERT viene usata per convertire *expression*. Se il valore di style è NULL, viene restituito NULL. L'intervallo è determinato da *data_type*. 
  
## <a name="return-types"></a>Tipi restituiti
Restituisce *expression* convertito in *data_type*.

## <a name="date-and-time-styles"></a>Stili date e time  
Quando il tipo di dati di *expression* è date o time, *style* può assumere uno dei valori indicati nella tabella seguente. Gli altri valori vengono elaborati come 0. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], gli unici stili supportati nella conversione di tipi date e time in **datetimeoffset** sono 0 o 1. Tutti gli altri stili di conversione restituiscono l'errore 9809.
  
>  [!NOTE]  
>  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è supportato il formato di data in stile arabo tramite l'algoritmo kuwaitiano.
  
|Senza il secolo (aa) (<sup>1</sup>)|Con il secolo (aaaa)|Standard|Input/Output (<sup>3</sup>)|  
|---|---|--|---|
|-|**0** o **100** (<sup>1,</sup><sup>2</sup>)|Predefinito per datetime e smalldatetime|mes gg aaaa hh:miAM (o PM)|  
|**1**|**101**|U.S.|1 = mm/gg/aa<br /> 101 = mm/gg/aaaa|  
|**2**|**102**|ANSI|2 = aa.mm.gg<br /> 102 = aaaa.mm.gg|  
|**3**|**103**|Inglese Regno Unito/Francese|3 = gg/mm/aa<br /> 103 = gg/mm/aaaa|  
|**4**|**104**|Tedesco|4 = gg.mm.aa<br /> 104 = gg.mm.aaaa|  
|**5**|**105**|Italiano|5 = gg-mm-aa<br /> 105 = gg-mm-aaaa|  
|**6**|**106** <sup>(1)</sup>|-|6 = gg mes aa<br /> 106 = gg mes aaaa|  
|**7**|**107** <sup>(1)</sup>|-|7 = Mes gg, aa<br /> 107 = Mes gg, aaaa|  
|**8**|**108**|-|hh:mi:ss|  
|-|**9** o **109** (<sup>1,</sup><sup>2</sup>)|Valore predefinito + millisecondi|mes gg aaaa hh:mi:ss:mmmAM (o PM)|  
|**10**|**110**|USA|10 = mm-gg-aa<br /> 110 = mm-gg-aaaa|  
|**11**|**111**|Giappone|11 = aa/mm/gg<br /> 111 = aaaa/mm/gg|  
|**12**|**112**|ISO|12 = aammgg<br /> 112 = aaaammgg|  
|-|**13** o **113** (<sup>1,</sup><sup>2</sup>)|Valore predefinito Europa + millisecondi|gg mes aaaa hh:mi:ss:mmm(24h)|  
|**14**|**114**|-|hh:mi:ss:mmm(24h)|  
|-|**20** o **120** (<sup>2</sup>)|ODBC canonico|aaaa-mm-gg hh:mi:ss(24h)|  
|-|**21** o **121** (<sup>2</sup>)|ODBC canonico (con millisecondi) predefinito per time, date, datetime2 e datetimeoffset|aaaa-mm-gg hh:mi:ss.mmm(24h)|  
|-|**126** (<sup>4</sup>)|ISO8601|aaaa-mm-ggThh:mi:ss.mmm (senza spazi)<br /> Nota: quando il valore dei millisecondi (mmm) è 0, il relativo valore non viene visualizzato. Ad esempio, il valore "2012-11-07T18:26:20.000" verrà visualizzato come "2012-11-07T18:26:20".|  
|-|**127**(<sup>6, 7</sup>)|ISO8601 con fuso orario Z.|aaaa-mm-ggThh:mi:ss.mmmZ (senza spazi)<br /> Nota: quando il valore dei millisecondi (mmm) è 0, il relativo valore non viene visualizzato. Ad esempio, il valore "2012-11-07T18:26:20.000" verrà visualizzato come "2012-11-07T18:26:20".|  
|-|**130** (<sup>1,</sup><sup>2</sup>)|Hijri (<sup>5</sup>)|gg mes aaaa hh:mi:ss:mmmAM<br /> In questo stile, mes è una rappresentazione unicode multi token Hijri del nome completo del mese. Questo valore non è reso correttamente in un'installazione US predefinita di SSMS.|  
|-|**131** (<sup>2</sup>)|Hijri (<sup>5</sup>)|gg/mm/aaaa hh:mi:ss:mmmAM|  
  
<sup>1</sup> Questi valori di stile restituiscono risultati non deterministici. Include tutti gli stili (aa) (senza secolo) e un subset di stili (aaaa) (con il secolo).
  
<sup>2</sup> I valori predefiniti (*style** *0** o **100**, **9** o **109**, **13** o **113**, **20** o **120** e **21** o **121**) restituiscono sempre il secolo (aaaa).
  
<sup>3</sup> Input quando viene eseguita la conversione nel tipo di dati **datetime**, output quando viene eseguita la conversione in dati di tipo carattere.
  
<sup>4</sup> Progettato per l'uso in XML. Per le conversioni di dati di tipo **datetime** o **smalldatetime** in dati di tipo carattere, il formato di output corrisponde a quello indicato nella tabella precedente.
  
<sup>5</sup> Hijri è un sistema di calendario con diverse variazioni. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene usato l'algoritmo kuwaitiano.
  
> [!IMPORTANT]  
>  Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpreta anni a due cifre in base a un anno di cambio data pari a 2049, ovvero l'anno a due cifre 49 è interpretato come 2049 mentre l'anno a due cifre 50 è interpretato come 1950. Numerose applicazioni client, ad esempio quelle basate su oggetti di automazione, utilizzano il 2030 come anno di cambio data. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è disponibile l'opzione di configurazione two digit year cutoff che modifica l'anno di cambio data usato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per una gestione coerente delle date. È consigliabile specificare l'anno nel formato a quattro cifre.  
  
<sup>6</sup> Supportato solo per il cast di dati dal tipo carattere al tipo di dati **datetime** o **smalldatetime**. In caso di cast dei dati di tipo carattere che rappresentano solo componenti di data o di ora al tipo di dati **datetime** o **smalldatetime**, il componente di ora non specificato viene impostato su 00:00:00.000 e il componente di data non specificato viene impostato su 01-01-1900.
  
<sup>7</sup> L'indicatore di fuso orario facoltativo Z viene usato per semplificare il mapping tra i valori **datetime** XML con informazioni sul fuso orario e i valori **datetime** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza fuso orario. Z è l'indicatore per il fuso orario UTC-0. Gli altri fusi orari sono indicati con il valore di offset HH:MM nella direzione + o -. Ad esempio: `2006-12-12T23:45:12-08:00`.
  
Quando si convertono dati di tipo **smalldatetime** in dati di tipo carattere, gli stili che includono secondi o millisecondi visualizzano una serie di zeri. Quando si esegue la conversione di valori **datetime** o **smalldatetime**, è possibile troncare le parti della data non desiderate specificando la lunghezza appropriata per il tipo di dati **char** o **varchar**.
  
Quando si esegue la conversione in **datetimeoffset** da dati di tipo carattere con uno stile che include un'ora, al risultato viene aggiunta una differenza di fuso orario.
  
## <a name="float-and-real-styles"></a>Stili float e real
Quando il tipo di dati di *expression* è **float** o **real**, *style* può assumere uno dei valori indicati nella tabella seguente. Gli altri valori vengono elaborati come 0.
  
|valore|Output|  
|---|---|
|**0** (predefinito)|Al massimo 6 cifre. Usare questo valore nella notazione scientifica, quando è appropriato.|  
|**1**|Sempre 8 cifre. Usare questo valore nella notazione scientifica.|  
|**2**|Sempre 16 cifre. Usare questo valore nella notazione scientifica.|  
|**3**|Sempre 17 cifre. Usare per la conversione senza perdita di dati. Con questo stile, è garantita la conversione di ogni float Distinct in una stringa di caratteri Distinct.<br /> **Si applica a:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] e a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].|  
|**126, 128, 129**|Incluso per motivi di compatibilità con le versioni precedenti. Potrebbe diventare deprecato in una versione futura.|  
  
## <a name="money-and-smallmoney-styles"></a>Stili money e smallmoney
Quando il tipo di dati di *expression* è **money** o **smallmoney**, *style* può assumere uno dei valori indicati nella tabella seguente. Gli altri valori vengono elaborati come 0.
  
|valore|Output|  
|---|---|
|**0** (predefinito)|Nessun separatore delle migliaia a sinistra del separatore decimale e due cifre a destra del separatore decimale, ad esempio 4235,98.|  
|**1**|Separatore delle migliaia ogni tre cifre a sinistra del separatore decimale e due cifre a destra del separatore decimale, ad esempio 3.510,92.|  
|**2**|Nessun separatore delle migliaia a sinistra del separatore decimale e quattro cifre a destra del separatore decimale, ad esempio 4235,9819.|  
|**126**|Equivalente allo stile 2 in caso di conversione in char(n) o varchar(n)|  
  
## <a name="xml-styles"></a>Stili xml
Quando il tipo di dati di *expression* è **xml***, style* può assumere uno dei valori indicati nella tabella seguente. Gli altri valori vengono elaborati come 0.
  
|valore|Output|  
|---|---|
|**0** (predefinito)|Viene usato il comportamento di analisi predefinito, ovvero vengono eliminati gli spazi vuoti non significativi e non vengono consentiti subset DTD interni.<br /> **Nota:** quando si esegue la conversione nel tipo di dati **xml**, gli spazi vuoti non significativi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono gestiti diversamente rispetto a XML 1.0. Per altre informazioni, vedere [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md).|  
|**1**|Mantiene gli spazi vuoti non significativi. Con questa impostazione, il comportamento predefinito di **xml:space** è equivalente a **xml:space="preserve"**.|  
|**2**|Abilita l'elaborazione limitata di subset DTD interni.<br /><br /> Se abilitata, il server può usare le informazioni seguenti disponibili in un subset DTD intero per eseguire operazioni di analisi senza convalida.<br /> - Vengono applicati i valori predefiniti per gli attributi.<br /> - I riferimenti alle entità interne vengono risolti ed espansi.<br /> - Viene controllata la correttezza della sintassi del modello di contenuti DTD.<br /> Il parser ignora i subset DTD esterni. Non valuta, inoltre, la dichiarazione XML per verificare se l'attributo **standalone** è impostato su **yes** o **no**, ma analizza l'istanza XML come se fosse un documento autonomo.|  
|**3**|Mantiene gli spazi vuoti non significativi e consente l'elaborazione limitata di subset DTD interni.|  
  
## <a name="binary-styles"></a>Stili binary
Quando il tipo di dati di *expression* è **binary(n)**, **varbinary(n)**, **char(n)** o **varchar(n)**, *style* può assumere uno dei valori indicati nella tabella seguente. I valori dello stile non elencati nella tabella restituiscono un errore.
  
|valore|Output|  
|---|---|
|**0** (predefinito)|Converte caratteri ASCII in byte binari e viceversa. Ogni carattere o byte viene convertito in base allo schema 1:1.<br /> Se *data_type* è un tipo binario, a sinistra del risultato vengono aggiunti i caratteri 0x.|  
|**1**, **2**|Se *data_type* è un tipo binario, l'espressione deve essere un'espressione di caratteri. *expression* deve includere un numero pari di cifre esadecimali (0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F, a, b, c, d, e, f). Se *style* è impostato su 1, i caratteri 0x devono essere i primi due caratteri dell'espressione. Se l'espressione contiene un numero di caratteri dispari o se un carattere qualsiasi non è valido, viene generato un errore.<br /> Se la lunghezza dell'espressione convertita è maggiore della lunghezza di *data_type*, il risultato viene troncato a destra.<br /> A *data_types* a lunghezza fissa maggiori del risultato convertito vengono aggiunti zero a destra del risultato stesso.<br /> Se data_type è un tipo di carattere, l'espressione deve essere binaria. Ogni carattere binario viene convertito in due caratteri esadecimali. Se la lunghezza dell'espressione convertita è maggiore di quella di *data_type*, verrà troncata a destra.<br /> Se *data_type* è un tipo di carattere di dimensioni fisse e la lunghezza del risultato convertito è minore di quella di *data_type*, a destra dell'espressione convertita vengono aggiunti spazi per mantenere un numero pari di cifre esadecimali.<br /> Se *style* è uguale a 1, a sinistra del risultato convertito verranno aggiunti i caratteri 0x.|  
  
## <a name="implicit-conversions"></a>Conversioni implicite
Le conversioni implicite sono conversioni eseguite senza specificare la funzione CAST o CONVERT. Le conversioni esplicite sono conversioni per cui è necessario specificare la funzione CAST o CONVERT. Nella figura seguente vengono illustrate le conversioni di tipi di dati esplicite e implicite consentite per i tipi di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questi includono **xml**, **bigint** e **sql_variant**. Non è possibile eseguire una conversione implicita in un'assegnazione dal tipo di dati **sql_variant**, ma è possibile eseguire una conversione implicita verso il tipo di dati **sql_variant**.
  
> [!TIP]  
>  Questo grafico è disponibile come file PDF scaricabile dall'[Area download Microsoft](http://www.microsoft.com/download/details.aspx?id=35834).  
  
![Tabella di conversione dei tipi di dati](../../t-sql/data-types/media/lrdatahd.png "Tabella di conversione dei tipi di dati")
  
Quando si esegue la conversione tra **datetimeoffset** e i tipi di dati carattere **char**, **varchar**, **nchar** e **nvarchar**, la parte relativa alla differenza di fuso orario convertita deve essere sempre costituita da cifre doppie sia per HH che per MM, ad esempio -08:00.
  
> [!NOTE]  
>  Poiché i dati Unicode usano sempre un numero pari di byte, prestare attenzione nella conversione tra dati di tipo **binary** o **varbinary** e tipi di dati supportati da Unicode. La conversione seguente, ad esempio, non restituisce il valore esadecimale 41, bensì 4100: `SELECT CAST(CAST(0x41 AS nvarchar) AS varbinary)`.  
  
## <a name="large-value-data-types"></a>Tipi di dati per valori di grandi dimensioni
Per quanto riguarda le conversioni implicite ed esplicite, i tipi di dati per valori di grandi dimensioni si comportano come i tipi di dati per valori di dimensioni minori, nello specifico i tipi di dati **varchar**, **nvarchar** e **varbinary**. Considerare, tuttavia, le linee guida seguenti:
-   La conversione di **image** in **varbinary(max)** e viceversa è una conversione implicita, come le conversioni tra **text** e **varchar(max)** e **ntext** e **nvarchar(max)**.  
-   La conversione di tipi di dati per valori di grandi dimensioni, ad esempio **varchar(max)**, in tipi di dati per valori di dimensioni minori, ad esempio **varchar**, è una conversione implicita, ma si verifica un troncamento se le dimensioni del valore di grandi dimensioni sono eccessive rispetto alla lunghezza specificata per il tipo di dati di dimensioni minori.  
-   La conversione di **varchar**, **nvarchar** o **varbinary** nei corrispondenti tipi di dati per valori di grandi dimensioni viene eseguita in modo implicito.  
-   La conversione del tipo di dati **sql_variant** in tipi di dati per valori di grandi dimensioni è una conversione esplicita.  
-   Non è possibile convertire i tipi di dati per valori di grandi dimensioni nel tipo di dati **sql_variant**.  
  
Per altre informazioni sulla conversione del tipo di dati **xml**, vedere [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md).
  
## <a name="xml-data-type"></a>Tipo di dati XML.
Quando si esegue il cast esplicito o implicito del tipo di dati **xml** a un tipo string o binary, il contenuto del tipo di dati **xml** viene serializzato in base a un set di regole. Per informazioni su queste regole, vedere [Definire la serializzazione di dati XML](../../relational-databases/xml/define-the-serialization-of-xml-data.md). Per altre informazioni sulla conversione di altri tipi di dati nel tipo di dati **xml**, vedere [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md).
  
## <a name="text-and-image-data-types"></a>Tipi di dati text e image
La conversione automatica del tipo di dati non è supportata per i tipi di dati **text** e **image**. È possibile convertire in modo esplicito dati di tipo **text** in dati di tipo carattere e dati di tipo **image** in dati di tipo **binary** o **varbinary**, ma la lunghezza massima è di 8000 byte. Se si tenta di eseguire una conversione non corretta, ad esempio se si tenta di convertire un'espressione di tipo carattere contenente lettere in un tipo **int**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un messaggio di errore.
  
## <a name="output-collation"></a>Regole di confronto per l'output  
Quando sia l'output che l'input di CAST o CONVERT sono stringhe di caratteri, le regole di confronto e la relativa etichetta dell'output corrispondono alle regole di confronto e alla relativa etichetta dell'input. Se l'input non è una stringa di caratteri, all'output sono associate le regole di confronto predefinite del database e un'etichetta delle regole di confronto a cui possono essere assegnati valori predefiniti. Per altre informazioni, vedere [Precedenza delle regole di confronto &#40;Transact-SQL&#41;](../../t-sql/statements/collation-precedence-transact-sql.md).
  
Per assegnare all'output regole di confronto diverse, applicare la clausola COLLATE all'espressione risultante della funzione CAST o CONVERT. Ad esempio
  
`SELECT CAST('abc' AS varchar(5)) COLLATE French_CS_AS`
  
## <a name="truncating-and-rounding-results"></a>Troncamento e arrotondamento dei risultati
Quando si esegue la conversione di espressioni di tipo carattere o binarie (**char**, **nchar**, **nvarchar**, **varchar**, **binary** o **varbinary**) in un'espressione con un tipo di dati diverso, i dati possono venire troncati o visualizzati solo parzialmente oppure viene restituito un errore per segnalare che il risultato è troppo breve per essere visualizzato. I risultati delle conversioni in dati di tipo **char**, **varchar**, **nchar**, **nvarchar**, **binary** e **varbinary** vengono troncati, ad eccezione delle conversioni riportate nella tabella seguente.
  
|Tipo di dati di origine|Tipo di dati di destinazione|Risultato|  
|---|---|---|
|**int**, **smallint** o **tinyint**|**char**|*|  
||**varchar**|*|  
||**nchar**|E|  
||**nvarchar**|E|  
|**money**, **smallmoney**, **numeric**, **decimal**, **float** o **real**|**char**|E|  
||**varchar**|E|  
||**nchar**|E|  
||**nvarchar**|E|  
  
\* = Risultato di lunghezza insufficiente per essere visualizzato. E = Viene restituito un errore perché la lunghezza del risultato è insufficiente per la visualizzazione.
  
Nelle operazioni di conversione viene garantita la restituzione di valori uguali in versioni diverse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] solo quando un tipo di dati viene convertito in un altro tipo di dati e quindi riconvertito nel tipo di dati iniziale. Nell'esempio seguente viene illustrata una conversione di questo tipo:
  
```sql
DECLARE @myval decimal (5, 2);  
SET @myval = 193.57;  
SELECT CAST(CAST(@myval AS varbinary(20)) AS decimal(10,5));  
-- Or, using CONVERT  
SELECT CONVERT(decimal(10,5), CONVERT(varbinary(20), @myval));  
```  
  
> [!NOTE]  
>  Evitare di costruire valori di tipo **binary** e di convertirli in un tipo di dati della categoria dei tipi numerici. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non garantisce che il risultato della conversione di un tipo di dati **decimal** o **numeric** nel tipo **binary** sia uguale in versioni diverse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Nell'esempio seguente viene illustrata un'espressione troppo breve per essere visualizzata.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName, SUBSTRING(p.Title, 1, 25) AS Title,
    CAST(e.SickLeaveHours AS char(1)) AS [Sick Leave]  
FROM HumanResources.Employee e JOIN Person.Person p 
    ON e.BusinessEntityID = p.BusinessEntityID  
WHERE NOT e.BusinessEntityID >5;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```   
FirstName   LastName      Title   Sick Leave
---------   ------------- ------- --------`
Ken         Sanchez       NULL   *
Terri       Duffy         NULL   *
Roberto     Tamburello    NULL   *
Rob         Walters       NULL   *
Gail        Erickson      Ms.    *
(5 row(s) affected)  
```
  
Quando si convertono tipi di dati con un numero di cifre decimali diverso, in alcuni casi il valore risultante viene troncato e in altri viene arrotondato. Nella tabella seguente viene illustrato questo comportamento.
  
|From|Per|Comportamento|  
|---|---|---|
|**numeric**|**numeric**|Arrotondamento|  
|**numeric**|**int**|Troncamento|  
|**numeric**|**money**|Arrotondamento|  
|**money**|**int**|Arrotondamento|  
|**money**|**numeric**|Arrotondamento|  
|**float**|**int**|Troncamento|  
|**float**|**numeric**|Arrotondamento<br /><br /> La conversione dei valori **float** che usano come notazione scientifica **decimal** o **numeric** è limitata ai soli valori con precisione a 17 cifre. Tutti i valori con precisione maggiore di 17 vengono arrotondati a zero.|  
|**float**|**datetime**|Arrotondamento|  
|**datetime**|**int**|Arrotondamento|  
  
Ad esempio, i valori 10.6496 e -10.6496 potrebbero essere troncati o arrotondati durante la conversione nei tipi **int** o **numeric**:
  
```sql
SELECT  CAST(10.6496 AS int) as trunc1,
         CAST(-10.6496 AS int) as trunc2,
         CAST(10.6496 AS numeric) as round1,
         CAST(-10.6496 AS numeric) as round2;
 ```
I risultati della query sono riportati nella tabella seguente:
 
|trunc1|trunc2|round1|round2|
|---|---|---|---|
|10|-10|11|-11|
 
Se si esegue una conversione di tipi di dati in cui il tipo di destinazione prevede un numero di decimali minore rispetto al tipo di origine, il valore viene arrotondato. Il risultato, ad esempio, della conversione seguente è `$10.3497`:
  
`SELECT CAST(10.3496847 AS money);`
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un messaggio di errore quando dati **char**, **nchar**, **varchar** o **nvarchar** non numerici vengono convertiti in **int**, **float**, **numeric** o **decimal**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un errore anche quando una stringa vuota (" ") viene convertita in **numeric** o **decimal**.
  
## <a name="certain-datetime-conversions-are-nondeterministic"></a>Alcune conversioni di data/ora sono non deterministiche
Nella tabella seguente vengono elencati gli stili per i quali la conversione da stringa al tipo datetime è di tipo non deterministico.
  
|||  
|-|-|  
|Tutti gli stili inferiori a 100<sup>1</sup>|106|  
|107|109|  
|113|130|  
  
<sup>1</sup> Ad eccezione degli stili 20 e 21
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)
A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], se si usano le regole di confronto per caratteri supplementari (SC), un'operazione CAST da **nchar** o **nvarchar** a un tipo **nchar** o **nvarchar** di lunghezza minore non verrà troncato in una coppia di surrogati, ma verrà troncato prima del carattere supplementare. Ad esempio, nel frammento di codice seguente `@x` mantiene solo `'ab'`. Lo spazio non è sufficiente per mantenere il carattere supplementare.
  
```sql
DECLARE @x NVARCHAR(10) = 'ab' + NCHAR(0x10000);  
SELECT CAST (@x AS NVARCHAR(3));  
```  
  
Quando si utilizzano le regole di confronto SC, il comportamento di `CONVERT` è analogo a quello di `CAST`.
  
## <a name="compatibility-support"></a>Informazioni sulla compatibilità
Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lo stile predefinito per le operazioni CAST e CONVERT nei tipi di dati **time** e **datetime2** è 121, tranne quando uno dei due tipi viene usato in un'espressione di colonna calcolata. Per le colonne calcolate, lo stile predefinito è 0. Questo comportamento influisce sulle colonne calcolate quando vengono create o usate nelle query con parametrizzazione automatica o nelle definizioni dei vincoli.
  
Con il livello di compatibilità 110 e superiore, lo stile predefinito per le operazioni CAST e CONVERT nei tipi di dati **time** e **datetime2** è sempre 121. Se la query si basa sul comportamento obsoleto, usare un livello di compatibilità inferiore a 110 oppure specificare in modo esplicito lo stile 0 nella query interessata.
  
L'aggiornamento del database al livello di compatibilità 110 e superiore non comporta la modifica dei dati utente archiviati su disco. È necessario correggere manualmente questi dati nel modo opportuno. Se ad esempio si usa SELECT INTO per creare una tabella da un'origine che contiene un'espressione di colonna calcolata descritta in precedenza, vengono archiviati i dati (con stile 0), non la definizione della colonna calcolata. Sarà necessario aggiornare manualmente questi dati in base allo stile 121.
  
## <a name="BKMK_examples"></a> Esempi  
  
### <a name="a-using-both-cast-and-convert"></a>A. Utilizzo delle funzioni CAST e CONVERT  
In ogni esempio vengono recuperati i nomi dei prodotti il cui prezzo contiene un `3` come prima cifra e i relativi valori di `ListPrice` vengono convertiti nel tipo `int`.
  
```sql
-- Use CAST  
USE AdventureWorks2012;  
GO  
SELECT SUBSTRING(Name, 1, 30) AS ProductName, ListPrice  
FROM Production.Product  
WHERE CAST(ListPrice AS int) LIKE '3%';  
GO  
  
-- Use CONVERT.  
USE AdventureWorks2012;  
GO  
SELECT SUBSTRING(Name, 1, 30) AS ProductName, ListPrice  
FROM Production.Product  
WHERE CONVERT(int, ListPrice) LIKE '3%';  
GO  
```  
  
### <a name="b-using-cast-with-arithmetic-operators"></a>B. Utilizzo della funzione CAST con operatori aritmetici  
Nell'esempio seguente viene eseguito il calcolo di una sola colonna (`Computed`) dividendo il totale delle vendite dell'anno in corso (`SalesYTD`) per la percentuale di commissione (`CommissionPCT`). Il risultato viene convertito in un tipo di dati `int` dopo l'arrotondamento al numero intero più prossimo.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT CAST(ROUND(SalesYTD/CommissionPCT, 0) AS int) AS Computed  
FROM Sales.SalesPerson   
WHERE CommissionPCT != 0;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
```  
Computed
------
379753754
346698349
257144242
176493899
281101272
0  
301872549
212623750
298948202
250784119
239246890
101664220
124511336
97688107
(14 row(s) affected)  
```  
  
### <a name="c-using-cast-to-concatenate"></a>C. Utilizzo della funzione CAST per la concatenazione  
Nell'esempio seguente vengono concatenate espressioni non di tipo carattere mediante CAST. Usa AdventureWorksDW.
  
```sql
SELECT 'The list price is ' + CAST(ListPrice AS varchar(12)) AS ListPrice  
FROM dbo.DimProduct  
WHERE ListPrice BETWEEN 350.00 AND 400.00;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
ListPrice
------------------------
The list price is 357.06
The list price is 364.09
The list price is 364.09
The list price is 364.09
The list price is 364.09  
```  
  
### <a name="d-using-cast-to-produce-more-readable-text"></a>D. Utilizzo di CAST per migliorare la leggibilità del testo  
L'esempio seguente usa CAST nell'elenco SELECT per convertire la colonna `Name` in una colonna **char(10)**. Usa AdventureWorksDW.
  
```sql
SELECT DISTINCT CAST(EnglishProductName AS char(10)) AS Name, ListPrice  
FROM dbo.DimProduct  
WHERE EnglishProductName LIKE 'Long-Sleeve Logo Jersey, M';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Name        UnitPrice
----------  ---------
Long-Sleev  31.2437
Long-Sleev  32.4935
Long-Sleev  49.99  
```  
  
### <a name="e-using-cast-with-the-like-clause"></a>E. Utilizzo di CAST con la clausola LIKE  
Nell'esempio seguente viene convertita la colonna `money` di tipo `SalesYTD` in una colonna di tipo `int` e quindi in una colonna di tipo `char(20)`, utilizzabile con la clausola `LIKE`.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName, s.SalesYTD, s.BusinessEntityID  
FROM Person.Person AS p   
JOIN Sales.SalesPerson AS s   
    ON p.BusinessEntityID = s.BusinessEntityID  
WHERE CAST(CAST(s.SalesYTD AS int) AS char(20)) LIKE '2%';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
FirstName        LastName            SalesYTD         SalesPersonID
---------------- ------------------- ---------------- -------------
Tsvi             Reiter              2811012.7151      279
Syed             Abbas               219088.8836       288
Rachel           Valdez              2241204.0424      289
(3 row(s) affected)  
```
  
### <a name="f-using-convert-or-cast-with-typed-xml"></a>F. Utilizzo di CONVERT o CAST con XML tipizzato  
Gli esempi seguenti illustrano l'utilizzo di CONVERT per eseguire conversioni in XML tipizzato tramite [Colonne e tipo di dati XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-type-and-columns-sql-server.md).
  
In questo esempio una stringa con spazi vuoti, testo e markup viene convertita in XML tipizzato e vengono rimossi tutti gli spazi vuoti non significativi (spazi vuoti limite tra i nodi):
  
```sql
CONVERT(XML, '<root><child/></root>')  
```  
  
In questo esempio una stringa simile con spazi vuoti, testo e markup viene convertita in XML tipizzato e vengono mantenuti gli spazi vuoti non significativi (spazi vuoti limite tra i nodi):
  
```sql
CONVERT(XML, '<root>          <child/>         </root>', 1)  
```  
  
In questo esempio viene eseguito il cast di una stringa con spazi vuoti, testo e markup in XML tipizzato:
  
```sql
CAST('<Name><FName>Carol</FName><LName>Elliot</LName></Name>'  AS XML)  
```  
  
Per altri esempi, vedere [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md).
  
### <a name="g-using-cast-and-convert-with-datetime-data"></a>G. Utilizzo di CAST e CONVERT con dati datetime  
Nell'esempio seguente vengono visualizzate la data e l'ora correnti, viene usato `CAST` per modificarle in un tipo di dati character e quindi viene usato `CONVERT` per visualizzarle nel formato `ISO 8901`.
  
```sql
SELECT   
   GETDATE() AS UnconvertedDateTime,  
   CAST(GETDATE() AS nvarchar(30)) AS UsingCast,  
   CONVERT(nvarchar(30), GETDATE(), 126) AS UsingConvertTo_ISO8601  ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedDateTime     UsingCast              UsingConvertTo_ISO8601
----------------------- ---------------------- ------------------------------
2006-04-18 09:58:04.570 Apr 18 2006  9:58AM    2006-04-18T09:58:04.570
(1 row(s) affected)  
```
  
L'esempio seguente rappresenta all'incirca l'opposto dell'esempio precedente. Nell'esempio vengono visualizzate una data e un'ora come dati di tipo carattere, viene usato `CAST` per modificare i dati di tipo carattere nel tipo di dati `datetime` e quindi viene usato `CONVERT` per modificare i dati nel tipo di dati `datetime`.
  
```sql
SELECT   
   '2006-04-25T15:50:59.997' AS UnconvertedText,  
   CAST('2006-04-25T15:50:59.997' AS datetime) AS UsingCast,  
   CONVERT(datetime, '2006-04-25T15:50:59.997', 126) AS UsingConvertFrom_ISO8601 ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedText         UsingCast               UsingConvertFrom_ISO8601
----------------------- ----------------------- ------------------------
2006-04-25T15:50:59.997 2006-04-25 15:50:59.997 2006-04-25 15:50:59.997
(1 row(s) affected)  
```
  
### <a name="h-using-convert-with-binary-and-character-data"></a>H. Utilizzo di CONVERT con dati binari e di tipo carattere  
Negli esempi seguenti vengono illustrati i risultati della conversione di dati binari e di tipo carattere utilizzando stili diversi.
  
```sql
--Convert the binary value 0x4E616d65 to a character value.  
SELECT CONVERT(char(8), 0x4E616d65, 0) AS [Style 0, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 0, binary to character
----------------------------
Name  
(1 row(s) affected)  
```
 
L'esempio seguente illustra come Style 1 può forzare il troncamento del risultato. Il troncamento è causato dall'inserimento dei caratteri 0x nel risultato.  
```sql  
SELECT CONVERT(char(8), 0x4E616d65, 1) AS [Style 1, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 1, binary to character
------------------------------
0x4E616D
(1 row(s) affected)  
```  
 
L'esempio seguente mostra che Style 2 non tronca il risultato perché i caratteri 0x non sono inclusi nel risultato.  
```sql  
SELECT CONVERT(char(8), 0x4E616d65, 2) AS [Style 2, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 2, binary to character
------------------------------
4E616D65
(1 row(s) affected)  
```
  
Convertire il valore di carattere 'Name' in valore binario.  
```sql
SELECT CONVERT(binary(8), 'Name', 0) AS [Style 0, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 0, character to binary
----------------------------
0x4E616D6500000000
(1 row(s) affected)  
```
  
```sql
SELECT CONVERT(binary(4), '0x4E616D65', 1) AS [Style 1, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 1, character to binary
---------------------------- 
0x4E616D65
(1 row(s) affected)  
```  

```sql
SELECT CONVERT(binary(4), '4E616D65', 2) AS [Style 2, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 2, character to binary  
----------------------------------  
0x4E616D65
(1 row(s) affected)  
```  
  
### <a name="i-converting-date-and-time-data-types"></a>I. Conversione dei tipi di dati date e time  
Il seguente esempio illustra la conversione dei tipi di dati date, time e datetime.
  
```sql
DECLARE @d1 date, @t1 time, @dt1 datetime;  
SET @d1 = GETDATE();  
SET @t1 = GETDATE();  
SET @dt1 = GETDATE();  
SET @d1 = GETDATE();  
-- When converting date to datetime the minutes portion becomes zero.  
SELECT @d1 AS [date], CAST (@d1 AS datetime) AS [date as datetime];  
-- When converting time to datetime the date portion becomes zero   
-- which converts to January 1, 1900.  
SELECT @t1 AS [time], CAST (@t1 AS datetime) AS [time as datetime];  
-- When converting datetime to date or time non-applicable portion is dropped.  
SELECT @dt1 AS [datetime], CAST (@dt1 AS date) AS [datetime as date], 
   CAST (@dt1 AS time) AS [datetime as time];  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="j-using-cast-and-convert"></a>J. Uso di CAST e CONVERT  
Questo esempio recupera il nome dei prodotti il cui prezzo contiene un `3` come prima cifra e converte i relativi valori di `ListPrice` nel tipo **int**. Usa AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS ProductName, ListPrice  
FROM dbo.DimProduct  
WHERE CAST(ListPrice AS int) LIKE '3%';  
```  
  
Questo esempio illustra la stessa query in cui viene usato CONVERT anziché CAST. Usa AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS ProductName, ListPrice  
FROM dbo.DimProduct  
WHERE CONVERT(int, ListPrice) LIKE '3%';  
```  
  
### <a name="k-using-cast-with-arithmetic-operators"></a>K. Utilizzo della funzione CAST con operatori aritmetici  
L'esempio seguente calcola una sola colonna dividendo il prezzo unitario del prodotto (`UnitPrice`) per la percentuale di sconto (`UnitPriceDiscountPct`). Il risultato viene convertito in un tipo di dati `int` dopo l'arrotondamento al numero intero più prossimo. Usa AdventureWorksDW.
  
```sql
SELECT ProductKey, UnitPrice,UnitPriceDiscountPct,  
       CAST(ROUND (UnitPrice*UnitPriceDiscountPct,0) AS int) AS DiscountPrice  
FROM dbo.FactResellerSales  
WHERE SalesOrderNumber = 'SO47355'   
      AND UnitPriceDiscountPct > .02;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
ProductKey  UnitPrice  UnitPriceDiscountPct  DiscountPrice
----------  ---------  --------------------  -------------
323         430.6445   0.05                  22
213         18.5043    0.05                  1
456         37.4950    0.10                  4
456         37.4950    0.10                  4
216         18.5043    0.05                  1  
```  
  
### <a name="l-using-cast-with-the-like-clause"></a>L. Utilizzo di CAST con la clausola LIKE  
L'esempio seguente converte la colonna **money** di tipo `ListPrice` in una colonna di tipo **int** e quindi in una colonna di tipo **char(20)** utilizzabile con la clausola LIKE. Usa AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS Name, ListPrice  
FROM dbo.DimProduct  
WHERE CAST(CAST(ListPrice AS int) AS char(20)) LIKE '2%';  
```  
  
### <a name="m-using-cast-and-convert-with-datetime-data"></a>M. Utilizzo di CAST e CONVERT con dati datetime  
L'esempio seguente visualizza la data e l'ora correnti, usa CAST per modificarle in dati di tipo carattere e quindi usa CONVERT per visualizzarle nel formato ISO 8601. Usa AdventureWorksDW.
  
```sql
SELECT TOP(1)  
   SYSDATETIME() AS UnconvertedDateTime,  
   CAST(SYSDATETIME() AS nvarchar(30)) AS UsingCast,  
   CONVERT(nvarchar(30), SYSDATETIME(), 126) AS UsingConvertTo_ISO8601  
FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedDateTime     UsingCast                     UsingConvertTo_ISO8601  
---------------------   ---------------------------   ---------------------------  
07/20/2010 1:44:31 PM   2010-07-20 13:44:31.5879025   2010-07-20T13:44:31.5879025  
```  
  
L'esempio seguente rappresenta all'incirca l'opposto dell'esempio precedente. L'esempio visualizza una data e un'ora come dati di tipo carattere, usa CAST per modificare i dati di tipo carattere nel tipo di dati **datetime** e quindi usa CONVERT per modificare i dati di tipo carattere nel tipo di dati **datetime**. Usa AdventureWorksDW.
  
```sql
SELECT TOP(1)   
   '2010-07-25T13:50:38.544' AS UnconvertedText,  
CAST('2010-07-25T13:50:38.544' AS datetime) AS UsingCast,  
   CONVERT(datetime, '2010-07-25T13:50:38.544', 126) AS UsingConvertFrom_ISO8601  
FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedText         UsingCast               UsingConvertFrom_ISO8601
----------------------- ----------------------- ------------------------
2010-07-25T13:50:38.544 07/25/2010 1:50:38 PM   07/25/2010 1:50:38 PM  
```  
  
## <a name="see-also"></a>Vedere anche
 [Conversione del tipo di dati &#40;motore di database&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
 [FORMAT &#40;Transact-SQL&#41;](../../t-sql/functions/format-transact-sql.md)  
 [STR &#40;Transact-SQL&#41;](../../t-sql/functions/str-transact-sql.md)  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
 [Scrittura di istruzioni Transact-SQL internazionali](../../relational-databases/collations/write-international-transact-sql-statements.md)
  
