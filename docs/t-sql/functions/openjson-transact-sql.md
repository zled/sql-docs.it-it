---
title: OPENJSON (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENJSON
- OPENJSON_TSQL
helpviewer_keywords:
- OPENJSON rowset function
- JSON, importing
- JSON, converting from
ms.assetid: 233d0877-046b-4dcc-b5da-adeb22f78531
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 29b296b2ae7e04871e81a9c236cb990bdd19562b
ms.openlocfilehash: 27eeb54d6493bb200e56caada1238d6fafb5b339
ms.contentlocale: it-it
ms.lasthandoff: 10/11/2017

---
# <a name="openjson-transact-sql"></a>OPENJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

**OPENJSON** è una funzione con valori di tabella che analizza il testo JSON e restituisce gli oggetti e le proprietà dell'input JSON in righe e colonne. In altre parole, **OPENJSON** fornisce una visualizzazione di set di righe in un documento JSON. In modo esplicito, è possibile specificare le colonne nel set di righe e i percorsi delle proprietà JSON usati per popolare le colonne. Poiché **OPENJSON** restituisce un set di righe, è possibile usare **OPENJSON** nel `FROM` clausola di un [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione nello stesso modo in cui è possibile utilizzare qualsiasi altra tabella, vista o funzione con valori di tabella.  
  
Utilizzare **OPENJSON** per importare i dati JSON in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], o per convertire dati JSON in formato relazionale per un'applicazione o servizio che non utilizza direttamente JSON.  
  
> [!NOTE]  
>  Il **OPENJSON** funzione è disponibile solo con livello di compatibilità 130 o versione successiva. Se il livello di compatibilità del database è inferiore a 130, SQL Server non riesce a trovare e a eseguire la funzione **OPENJSON**. Altre funzioni JSON sono disponibili in tutti i livelli di compatibilità.
> 
> È possibile controllare il livello di compatibilità nella vista `sys.databases` o nelle proprietà del database. È possibile modificare il livello di compatibilità di un database con il comando seguente:  
> 
> `ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130`
>   
> Livello di compatibilità 120 potrebbe essere il valore predefinito anche in un nuovo Database SQL di Azure.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento")[convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
OPENJSON( jsonExpression [ , path ] )  [ <with_clause> ]

<with_clause> ::= WITH ( { colName type [ column_path ] [ AS JSON ] } [ ,...n ] )
```  

Il **OPENJSON** funzione con valori di tabella per analizzare il *jsonExpression* fornito come primo argomento e restituisce uno o più righe contenenti dati dagli oggetti JSON nell'espressione. *jsonExpression* può contenere oggetti secondari nidificati. Se si desidera analizzare un oggetto secondario dall'interno *jsonExpression*, è possibile specificare un **percorso** parametro per l'oggetto secondario JSON.

### <a name="openjson"></a>openjson

![Sintassi per TVF OPENJSON](../../relational-databases/json/media/openjson-syntax.png "sintassi OPENJSON")  

Per impostazione predefinita, il **OPENJSON** funzione con valori di tabella restituisce tre colonne, che contengono il nome della chiave, il valore, e il tipo di ogni coppia di {chiave-valore} trovato *jsonExpression*. In alternativa, è possibile specificare in modo esplicito lo schema del risultato set **OPENJSON** restituisce fornendo *with_clause*.
  
### <a name="withclause"></a>with_clause
  
![Sintassi per la clausola OPENJSON TVF](../../relational-databases/json/media/openjson-shema-syntax.png "OPENJSON con sintassi")

*with_clause* contiene un elenco di colonne con i relativi tipi per **OPENJSON** da restituire. Per impostazione predefinita, **OPENJSON** corrisponde chiavi *jsonExpression* con i nomi delle colonne *with_clause* (in questo caso, le chiavi di corrispondenze implica che sia tra maiuscole e minuscole). Se un nome di colonna non corrisponde a un nome di chiave, è possibile fornire un parametro facoltativo *column_path*, ovvero un [espressione di percorso JSON](../../relational-databases/json/json-path-expressions-sql-server.md) che fa riferimento una chiave all'interno di *jsonExpression*. 

## <a name="arguments"></a>Argomenti  
### <a name="jsonexpression"></a>*jsonExpression*  
È un'espressione di caratteri Unicode contenente testo JSON.  
  
OPENJSON scorre gli elementi della matrice o le proprietà dell'oggetto nell'espressione di JSON e restituisce una riga per ogni elemento o proprietà. L'esempio seguente restituisce ogni proprietà dell'oggetto fornito come *jsonExpression*:  
  
```sql  
DECLARE @json NVARCHAR(4000) = N'{  
   "StringValue":"John",  
   "IntValue":45,  
   "TrueValue":true,  
   "FalseValue":false,  
   "NullValue":null,  
   "ArrayValue":["a","r","r","a","y"],  
   "ObjectValue":{"obj":"ect"}  
}'

SELECT *
FROM OPENJSON(@json)
```  
  
**Risultati**  
  
|Key|Valore|tipo|  
|---------|-----------|----------|  
|StringValue|John|1|  
|IntValue|45|2|  
|trueValue|true|3|  
|falseValue|false|3|  
|nullValue|NULL|0|  
|ArrayValue|["a", "r", "r", "y",""]|4|  
|ObjectValue|{"obj": "ect"}|5|  

### <a name="path"></a>*percorso*  
È un'espressione di percorso JSON facoltativa che fa riferimento a un oggetto o una matrice all'interno di *jsonExpression*. **OPENJSON** Cerca nel testo JSON in corrispondenza della posizione specificata e viene analizzato il frammento di cui si fa riferimento. Per altre informazioni, vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).

In [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] e [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], è possibile specificare una variabile come valore di *percorso*.
  
L'esempio seguente restituisce un oggetto nidificato, specificando il *percorso*:  

```sql  
DECLARE @json NVARCHAR(4000) = N'{  
      "path": {  
            "to":{  
                 "sub-object":["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]  
                 }  
              }  
 }';

SELECT [key], value
FROM OPENJSON(@json,'$.path.to."sub-object"')
```  
  
 **Risultati**  
  
|Key|Valore|  
|---------|-----------|  
|0|en-GB|  
|1|en-UK|  
|2|de-AT|  
|3|es-AR|  
|4|sr-Cyrl|  
 
Quando **OPENJSON** analizza una matrice JSON, la funzione restituisce gli indici degli elementi nel testo JSON come chiavi.

Il confronto utilizzato per identificare i passaggi di percorso con le proprietà dell'espressione JSON è consapevole di regole di confronto con distinzione tra maiuscole e minuscole (vale a dire un confronto BIN2). 

### <a name="withclause"></a>*with_clause*
Definisce in modo esplicito lo schema di output per il **OPENJSON** restituzione della funzione. Facoltativo *with_clause* può contenere i seguenti elementi:

*colName* è il nome per la colonna di output.  
  
Per impostazione predefinita, **OPENJSON** utilizza il nome della colonna per corrispondere a una proprietà in testo JSON. Ad esempio, se si specifica la colonna *nome* nello schema, OPENJSON tenta di popolare la colonna con la proprietà "name" nel testo JSON. È possibile eseguire l'override di questo mapping predefinito utilizzando il *column_path* argomento.  
  
*type*  
È il tipo di dati per la colonna di output.  

> [!NOTE]
> Se si utilizza anche il **AS JSON** opzione, la colonna *tipo* deve essere `NVARCHAR(MAX)`.
  
*column_path*  
È il percorso JSON che specifica la proprietà da restituire nella colonna specificata. Per altre informazioni, vedere la descrizione del *percorso* parametro in precedenza in questo argomento.  
  
Utilizzare *column_path* eseguire l'override delle regole di mapping predefinito quando il nome di una colonna di output non corrisponde al nome della proprietà.  
  
Il confronto utilizzato per identificare i passaggi di percorso con le proprietà dell'espressione JSON è consapevole di regole di confronto con distinzione tra maiuscole e minuscole (vale a dire un confronto BIN2).  
  
Per ulteriori informazioni sui percorsi, vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
*COME JSON*  
Utilizzare il **AS JSON** opzione in una definizione di colonna per specificare che la proprietà di riferimento contiene un oggetto JSON interno o una matrice. Se si specifica il **AS JSON** opzione, il tipo della colonna deve essere nvarchar (max).

-   Se non si specifica **AS JSON** per una colonna, la funzione restituisce un valore scalare (ad esempio int, string, true, false) della proprietà JSON specificato nel percorso specificato. Se il percorso rappresenta un oggetto o una matrice e la proprietà non può trovarsi nel percorso specificato, la funzione restituisce null in modalità lax o restituisce un errore in modalità strict. Questo comportamento è simile al comportamento del **JSON_VALUE** (funzione).  
  
-   Se si specifica **AS JSON** per una colonna, la funzione restituisce un frammento JSON della proprietà JSON specificato nel percorso specificato. Se il percorso rappresenta un valore scalare, e la proprietà non viene trovata nel percorso specificato, la funzione restituisce null in modalità lax o restituisce un errore in modalità strict. Questo comportamento è simile al comportamento del **JSON_QUERY** (funzione).  
  
> [!NOTE]  
> Se si desidera restituire un frammento JSON nidificato da una proprietà JSON, è necessario fornire il **AS JSON** flag. Senza questa opzione, se la proprietà non viene trovata, OPENJSON restituisce un valore NULL anziché il riferimento di oggetto JSON o una matrice o restituisce un errore di run-time in modalità strict.  
  
Ad esempio, la query seguente restituisce e formatta gli elementi di matrice:  
  
```sql  
DECLARE @json NVARCHAR(MAX) = N'[  
  {  
    "Order": {  
      "Number":"SO43659",  
      "Date":"2011-05-31T00:00:00"  
    },  
    "AccountNumber":"AW29825",  
    "Item": {  
      "Price":2024.9940,  
      "Quantity":1  
    }  
  },  
  {  
    "Order": {  
      "Number":"SO43661",  
      "Date":"2011-06-01T00:00:00"  
    },  
    "AccountNumber":"AW73565",  
    "Item": {  
      "Price":2024.9940,  
      "Quantity":3  
    }  
  }
]'  
   
SELECT *
FROM OPENJSON ( @json )  
WITH (   
              Number   varchar(200)   '$.Order.Number',  
              Date     datetime       '$.Order.Date',  
              Customer varchar(200)   '$.AccountNumber',  
              Quantity int            '$.Item.Quantity',  
              [Order]  nvarchar(MAX)  AS JSON  
 )
```  
  
**Risultati**  
  
|Number|Data|Customer|Quantity|JSON|  
|------------|----------|--------------|--------------|-----------|  
|SO43659|2011-05-31T00:00:00|AW29825|1|{"Number": "SO43659", "Date": "2011-05-31T00:00:00"}|  
|SO43661|2011-06-01T00:00:00|AW73565|3|{"Number": "SO43661", "Date": "2011-06-01T00:00:00"}|  
  

## <a name="return-value"></a>Valore restituito  
Le colonne che restituisce la funzione OPENJSON dipendono dall'opzione WITH.  
  
1. Quando si chiama OPENJSON con lo schema predefinito, ovvero, se non si specifica uno schema esplicito nella clausola WITH - la funzione restituisce una tabella con le colonne seguenti:  
    1.  **Chiave**. Un valore nvarchar (4000) che contiene il nome della proprietà specificata o l'indice dell'elemento nella matrice specificata. La colonna chiave con regole di confronto BIN2.  
    2.  **Valore**. Un valore nvarchar (max) che contiene il valore della proprietà. La colonna valore eredita le regole di confronto da *jsonExpression*.
    3.  **Tipo**. Un valore int che contiene il tipo del valore. Il **tipo** colonna viene restituita solo quando si utilizza OPENJSON con lo schema predefinito. La colonna di tipo è uno dei valori seguenti:  
  
        |Valore della colonna di tipo|Tipo di dati JSON|  
        |------------------------------|--------------------|  
        |0|null|  
        |1|string|  
        |2|int|  
        |3|true o false|  
        |4|array|  
        |5|oggetto|  
  
     Solo le proprietà di primo livello vengono restituite. L'istruzione ha esito negativo se il testo JSON non è formattato correttamente.  

2. Quando si chiama OPENJSON e si specifica uno schema esplicito nella clausola WITH, la funzione restituisce una tabella con lo schema definito nella clausola WITH.  

## <a name="remarks"></a>Osservazioni  

*json_path* usato nel secondo argomento di **OPENJSON** o in *with_clause* può iniziare con il **lax** o **strict** parola chiave.

-   In **lax** modalità **OPENJSON** non genera un errore se non viene trovato l'oggetto o un valore nel percorso specificato. Se non è possibile trovare il percorso, **OPENJSON** restituisce un set di risultati vuoto o un valore NULL.
-   In **strict**, modalità **OPENJSON** restituisce un errore se non è possibile trovare il percorso.

Alcuni degli esempi in questa pagina specificare in modo esplicito la modalità path, lax o strict. La modalità path è facoltativa. Se si specifica esplicitamente una modalità path, lax è la modalità predefinita. Per ulteriori informazioni sulle modalità path ed espressioni di percorso, vedere [espressioni di percorso JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).    

I nomi di colonna in *with_clause* verranno associate alle chiavi nel testo JSON. Se si specifica il nome della colonna `[Address.Country]`, viene confrontato con la chiave `Address.Country`. Se si desidera fare riferimento a una chiave nidificata `Country` all'interno dell'oggetto `Address`, è necessario specificare il percorso `$.Address.Country` nel percorso di colonna.

*json_path* può contenere chiavi con caratteri alfanumerici. Il nome della chiave in escape *json_path* tra virgolette doppie se le chiavi sono presenti caratteri speciali. Ad esempio, `$."my key $1".regularKey."key with . dot"` corrispondenze valore 1 nel testo JSON seguente:

```json
{
  "my key $1": {
    "regularKey":{
      "key with . dot": 1
    }
  }
}
```  

## <a name="examples"></a>Esempi  
  
### <a name="example-1---convert-a-json-array-to-a-temporary-table"></a>Esempio 1: convertire una matrice JSON in una tabella temporanea  
Nell'esempio seguente fornisce un elenco di identificatori come una matrice JSON dei numeri. La query converte la matrice JSON in una tabella di identificatori e i filtri di tutti i prodotti con gli ID specificati.  
  
```sql  
DECLARE @pSearchOptions NVARCHAR(4000) = N'[1,2,3,4]'

SELECT *
FROM products
INNER JOIN OPENJSON(@pSearchOptions) AS productTypes
 ON product.productTypeID = productTypes.value
```  
  
Questa query è equivalente all'esempio seguente. Tuttavia, nell'esempio seguente, è necessario incorporare i numeri nella query anziché essere passate come parametri.  
  
```sql  
SELECT *
FROM products
WHERE product.productTypeID IN (1,2,3,4)
```  
  
### <a name="example-2---merge-properties-from-two-json-objects"></a>Esempio 2: proprietà di tipo Merge da due oggetti JSON  
L'esempio seguente seleziona un'unione di tutte le proprietà di due oggetti JSON. I due oggetti hanno un duplicato *nome* proprietà. L'esempio Usa il valore della chiave per escludere le righe duplicate dai risultati.  
  
```sql  
DECLARE @json1 NVARCHAR(MAX),@json2 NVARCHAR(MAX)

SET @json1=N'{"name": "John", "surname":"Doe"}'

SET @json2=N'{"name": "John", "age":45}'

SELECT *
FROM OPENJSON(@json1)
UNION ALL
SELECT *
FROM OPENJSON(@json2)
WHERE [key] NOT IN (SELECT [key] FROM OPENJSON(@json1))
```  
  
### <a name="example-3---join-rows-with-json-data-stored-in-table-cells-using-cross-apply"></a>Esempio 3: Join le righe con i dati JSON memorizzati nelle celle di tabella utilizzando CROSS APPLY  
Nell'esempio seguente, il `SalesOrderHeader` tabella include un `SalesReason` colonna di testo che contiene una matrice di `SalesOrderReasons` in formato JSON. Il `SalesOrderReasons` oggetti contengono proprietà come *qualità* e *produttore*. Nell'esempio viene creato un report che unisce ogni riga dell'ordine di vendita ai motivi di vendita correlati. L'operatore OPENJSON si espande la matrice JSON dei motivi di vendita come se fossero archiviati i motivi in una tabella figlio separata. Quindi l'operatore CROSS APPLY unisce ogni riga dell'ordine di vendita alle righe restituite dalla funzione con valori di tabella OPENJSON.  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
> [!TIP] 
> Quando è necessario espandere le matrici JSON archiviato in singoli campi e unirli con le relative righe padre, in genere si usa il [!INCLUDE[tsql](../../includes/tsql-md.md)] operatore CROSS APPLY. Per ulteriori informazioni su CROSS APPLY, vedere [FROM &#40; Transact-SQL &#41; ](../../t-sql/queries/from-transact-sql.md).  
  
La stessa query può essere riscritto utilizzando `OPENJSON` con uno schema definito in modo esplicito di righe da restituire:  
  
```sql  
SELECT SalesOrderID, OrderDate, value AS Reason  
FROM Sales.SalesOrderHeader  
     CROSS APPLY OPENJSON (SalesReasons) WITH (value nvarchar(100) '$')
```  
  
In questo esempio, il `$` percorso fa riferimento a ogni elemento nella matrice. Se si desidera eseguire in modo esplicito il cast del valore restituito, è possibile utilizzare questo tipo di query.  
  
### <a name="example-4---combine-relational-rows-and-json-elements-with-cross-apply"></a>Esempio 4 - combinare righe relazionale e gli elementi JSON con CROSS APPLY  
La query seguente combina righe relazionale e gli elementi JSON nei risultati mostrati nella tabella riportata di seguito.  
  
```sql  
SELECT store.title, location.street, location.lat, location.long  
FROM store  
CROSS APPLY OPENJSON(store.jsonCol, 'lax $.location')   
     WITH (street varchar(500) ,  postcode  varchar(500) '$.postcode' ,  
     lon int '$.geo.longitude', lat int '$.geo.latitude')  
     AS location
```  
  
**Risultati**  
  
|title|street|codice postale|LON|LAT|  
|-----------|------------|--------------|---------|---------|  
|Intero alimenti mercati|Il modo di Redmond 17991|WA 98052|47.666124|-122.10155|  
|SEARS|NE Ave 148th|WA 98052|47.63024|-122.141246,17|  
  
### <a name="example-5---import-json-data-into-sql-server"></a>Esempio 5 - importare i dati JSON in SQL Server  
Nell'esempio seguente viene caricato un intero oggetto JSON in una tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```sql  
DECLARE @json NVARCHAR(max)  = N'{  
  "id" : 2,  
  "firstName": "John",  
  "lastName": "Smith",  
  "isAlive": true,  
  "age": 25,  
  "dateOfBirth": "2015-03-25T12:00:00",  
  "spouse": null  
  }';  
   
  INSERT INTO Person  
  SELECT *   
  FROM OPENJSON(@json)  
  WITH (id int,  
        firstName nvarchar(50), lastName nvarchar(50),   
        isAlive bit, age int,  
        dateOfBirth datetime2, spouse nvarchar(50)
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni di percorso JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Convertire dati JSON in righe e colonne con la funzione OPENJSON &#40; SQL Server &#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)   
 [Usare OPENJSON con lo Schema predefinito &#40; SQL Server &#41;](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md)   
 [Usare OPENJSON con uno Schema esplicito &#40; SQL Server &#41;](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md)  
  
  

