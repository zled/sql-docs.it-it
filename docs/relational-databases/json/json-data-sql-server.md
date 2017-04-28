---
title: Dati JSON (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- JSON
- JSON, built-in support
ms.assetid: c9a4e145-33c3-42b2-a510-79813e67806a
caps.latest.revision: 47
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3daaaa3dc2fb53344b009a5b3ab3d1cfbdd19350
ms.lasthandoff: 04/11/2017

---
# <a name="json-data-sql-server"></a>Dati JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

JSON è un popolare formato di dati testuali usato per lo scambio di dati in applicazioni per dispositivi mobili e Web moderne. JSON viene usato anche per archiviare dati non strutturati nei file di log o nei database NoSQL come Microsoft Azure DocumentDB. Molti servizi Web REST restituiscono risultati formattati come testo JSON oppure accettano dati formattati come JSON. La maggior parte dei servizi Azure, come Ricerca di Azure, Archiviazione di Azure e Azure DocumentDb, include ad esempio endpoint REST che restituiscono o usano JSON. JSON è anche il formato principale per lo scambio di dati tra le pagine Web e i server Web che usano le chiamate AJAX.  
  
 Ecco un esempio di testo JSON:  
  
```json  
[{
    "name": "John",
    "skills": ["SQL", "C#", "Azure"]
}, {
    "name": "Jane",
    "surname": "Doe"
}]
```  
  
 SQL Server fornisce funzioni e operatori predefiniti che consentono di eseguire le operazioni seguenti con testo JSON.  
  
-   Analizzare il testo JSON e leggere o modificare i valori.  
  
-   Trasformare matrici di oggetti JSON in formato tabella.  
  
-   Eseguire qualsiasi query Transact-SQL sugli oggetti JSON convertiti.  
  
-   Formattare i risultati delle query Transact-SQL in formato JSON.  
  
 ![Panoramica del supporto JSON predefinito](../../relational-databases/json/media/jsonslides1overview.png "Panoramica del supporto JSON predefinito")  
  
## <a name="key-json-capabilities-of-sql-server"></a>Principali funzionalità JSON di SQL Server 
Di seguito sono descritte le principali funzionalità offerte da SQL Server tramite il supporto JSON predefinito.

### <a name="extract-values-from-json-text-and-use-them-in-queries"></a>Estrarre valori dal testo JSON e usarli nelle query
Se un testo JSON viene archiviato nel database o in tabelle, è possibile usare le funzioni predefinite per leggere o modificare i valori in testo JSON.  
  
-   Usare la funzione **JSON_VALUE** per estrarre un valore scalare da una stringa JSON.
  
-   Usare **JSON_QUERY** per estrarre un oggetto o una matrice da una stringa JSON.
  
-   Usare la funzione **ISJSON** per verificare se una stringa contiene JSON valido.

-   Usare la funzione **JSON_MODIFY** per modificare un valore in una stringa JSON.

**Esempio**
  
 Nell'esempio seguente viene illustrata la query che usa dati relazionali e JSON (archiviati nella colonna jsonCol) da una tabella:  
  
```tsql  
SELECT Name,Surname,
 JSON_VALUE(jsonCol,'$.info.address.PostCode') AS PostCode,
 JSON_VALUE(jsonCol,'$.info.address."Address Line 1"')+' '
  +JSON_VALUE(jsonCol,'$.info.address."Address Line 2"') AS Address,
 JSON_QUERY(jsonCol,'$.info.skills') AS Skills
FROM PeopleCollection
WHERE ISJSON(jsonCol)>0
 AND JSON_VALUE(jsonCol,'$.info.address.Town')='Belgrade'
 AND Status='Active'
ORDER BY JSON_VALUE(jsonCol,'$.info.address.PostCode')
```  
  
 Strumenti e applicazioni non rilevano alcuna differenza tra i valori ricavati dalle colonne della tabella scalare e i valori ricavati dalla colonna JSON. È possibile usare i valori dal testo JSON in qualsiasi parte della query Transact-SQL (tra cui clausole WHERE, ORDER BY o GROUP BY, aggregazioni finestra e così via). Le funzioni JSON usano una sintassi di tipo JavaScript per fare riferimento ai valori all'interno del testo JSON.

Per altre informazioni, vedere [Convalidare, eseguire query e modificare i dati JSON con funzioni predefinite &#40;SQL Server&#41;](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md), [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)e [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  
  
### <a name="change-json-values"></a>Modificare valori JSON
Se è necessario modificare parti di testo JSON, è possibile usare la funzione **JSON_MODIFY** per aggiornare il valore di una proprietà in una stringa JSON e restituire la stringa JSON aggiornata. L'esempio seguente aggiorna il valore di una proprietà in una variabile che include contenuto JSON.  
  
```tsql  
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=JSON_MODIFY(@jsonInfo,'$.info.address[0].town','London') 
```  
  
### <a name="convert-json-collections-to-a-rowset"></a>Convertire raccolte JSON in un set di righe
Non è necessario un linguaggio di query personalizzato per eseguire query JSON in SQL Server. Per eseguire query sui dati JSON, si può usare il linguaggio T-SQL standard. Se è necessario creare una query o un report sui dati JSON, è possibile convertire facilmente i dati JSON in righe e colonne chiamando la funzione **OPENJSON** del set di righe. Per altre informazioni, vedere [Convertire dati JSON in righe e colonne con la funzione OPENJSON &#40;SQL Server&#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md).  
  
 Nell'esempio seguente viene chiamato **OPENJSON** che trasforma una matrice di oggetti archiviati nella variabile `@json` in un set di righe su cui è possibile eseguire una query usando l'istruzione SQL **SELECT** standard:  
  
```tsql  
DECLARE @json NVARCHAR(MAX)
SET @json =  
N'[  
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith" }, "dob": "2005-11-04T12:00:00" }  
 ]'  
   
SELECT *  
FROM OPENJSON(@json)  
  WITH (id int 'strict $.id',  
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',  
        age int, dateOfBirth datetime2 '$.dob')  
```  
  
 **Risultati**  
  
|id|firstName|lastName|age|dateOfBirth|  
|--------|---------------|--------------|---------|-----------------|  
|2|John|Smith|25||  
|5|Jane|Smith||2005-11-04T12:00:00|  
  
 **OPENJSON** trasforma la matrice di oggetti JSON in una tabella in cui ogni oggetto è rappresentato come una riga e le coppie chiave-valore vengono restituite come celle. L'output osserva le regole seguenti.
-   **OPENJSON** converte i valori JSON nei tipi specificati nella clausola **WITH**.
-   **OPENJSON** può gestire sia coppie chiave-valore flat che gli oggetti annidati organizzati gerarchicamente.
-   Non è necessario restituire tutti i campi contenuti nel testo JSON.
-   **OPENJSON** restituisce valori NULL se non esistono valori JSON.
-   È possibile specificare un percorso dopo la definizione del tipo per fare riferimento a una proprietà annidata o a una proprietà con un nome diverso.
-   Il prefisso **strict** facoltativo nel percorso specifica che i valori per le proprietà specificate devono esistere nel testo JSON.

Per altre informazioni, vedere [Convertire dati JSON in righe e colonne con la funzione OPENJSON &#40;SQL Server&#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md) e [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
### <a name="convert-sql-server-data-to-json-or-export-json"></a>Convertire dati di SQL Server in formato JSON o esportare JSON
Formattare i dati SQL Server o i risultati delle query JSON in formato JSON aggiungendo la clausola **FOR JSON** a un'istruzione **SELECT** . Usare la clausola FOR JSON per delegare la formattazione dell'output JSON dalle applicazioni client a SQL Server. Per altre informazioni, vedere [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
 L'esempio seguente usa la modalità PATH con la clausola FOR JSON.  
  
```tsql  
SELECT id, firstName AS "info.name", lastName AS "info.surname", age, dateOfBirth as dob  
FROM People  
FOR JSON PATH  
```  
  
Ogni **FOR JSON** formatta i risultati SQL come testo JSON che può essere fornito a qualsiasi app che riconosce JSON. L'opzione PATH usa alias separati da punti nella clausola SELECT per annidare oggetti nei risultati della query.  
  
 **Risultati**  
  
```json  
[{
    "id": 2,
    "info": {
        "name": "John",
        "surname": "Smith"
    },
    "age": 25
}, {
    "id": 5,
    "info": {
        "name": "Jane",
        "surname": "Smith"
    },
    "dob": "2005-11-04T12:00:00"
}] 
```  
  
 Per altre informazioni, vedere [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md) e [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="combine-relational-and-json-data"></a>Combinare dati relazionali e dati JSON
 SQL Server fornisce un modello ibrido per l'archiviazione e l'elaborazione dei dati relazionali e JSON usando il linguaggio Transact-SQL standard. È possibile organizzare le raccolte di documenti JSON in tabelle, stabilire relazioni tra di esse, combinare colonne scalari fortemente tipizzate archiviate in tabelle con coppie chiave-valore flessibili archiviate nelle colonne JSON ed eseguire query su valori scalari e JSON in una o più tabelle usando il linguaggio Transact-SQL completo.
 
Il testo JSON è in genere archiviato in colonne varchar o nvarchar e viene indicizzato come testo normale. Qualsiasi funzionalità o componente di SQL Server che supporta testo supporta anche JSON, quindi non esiste quasi nessun vincolo nell'interazione tra JSON e altre funzionalità di SQL Server. I dati JSON possono essere archiviati in tabelle in memoria o temporali, i predicati della sicurezza a livello di riga possono essere applicati al testo JSON e così via.

Se si hanno semplici carichi di lavoro JSON in cui si vuole usare un linguaggio di query personalizzato per l'elaborazione di documenti JSON, prendere in considerazione Microsoft Azure [DocumentDB](https://azure.microsoft.com/services/documentdb/).  
  
 Ecco alcuni casi d'uso che mostrano come usare il supporto JSON integrato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-data-from-a-sql-server-table-formatted-as-json"></a>Restituire dati da una tabella di SQL Server formattata come JSON  
 Se si ha un servizio Web che preleva i dati dal livello di database e li restituisce in formato JSON oppure framework o librerie JavaScript che accettano dati formattati come JSON, è possibile formattare l'output JSON direttamente in una query SQL. Anziché scrivere codice o, ad esempio includere una libreria per convertire i risultati di una query tabulare e quindi serializzare gli oggetti in formato JSON, è possibile usare FOR JSON per delegare la formattazione JSON a SQL Server.  
  
 Ad esempio, può essere necessario generare output JSON che sia conforme alla specifica OData. Il servizio Web prevede una richiesta e una risposta nel formato seguente.  
  
-   Richiesta: `/Northwind/Northwind.svc/Products(1)?$select=ProductID,ProductName`  
  
-   Risposta: `{"@odata.context":"http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity","ProductID":1,"ProductName":"Chai"}`  
  
 Questo URL OData rappresenta una richiesta per le colonne ProductID e ProductName per il prodotto con id 1. È possibile usare la clausola **FOR JSON** per formattare l'output come previsto in SQL Server.  
  
```tsql  
SELECT 'http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity'
 AS '@odata.context',   
 ProductID, Name as ProductName   
FROM Production.Product  
WHERE ProductID = 1  
FOR JSON AUTO  
```  
  
Il risultato di questa query è testo JSON interamente conforme alla specifica OData. Formattazione e sequenza di escape vengono gestite da SQL Server. SQL Server può anche formattare i risultati delle query in qualsiasi formato, ad esempio OData JSON o GeoJSON. Per altre informazioni, vedere [Returning spatial data in GeoJSON format](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/returning-spatial-data-in-geojson-format-part-1) (Restituzione di dati spaziali in formato GeoJSON).  
  
## <a name="analyze-json-data-with-sql-queries"></a>Analizzare i dati JSON con query SQL  
 Se è necessario filtrare o aggregare dati JSON per la creazione di report, è possibile usare **OPENJSON** per trasformare i dati JSON in formato relazionale. Quindi, usare le funzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] predefinite e standard per preparare i report.  
  
```tsql  
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date  
FROM   SalesOrderRecord AS Tab  
          CROSS APPLY  
     OPENJSON (Tab.json, N'$.Orders.OrdersArray')  
           WITH (  
              Number   varchar(200) N'$.Order.Number',   
              Date     datetime     N'$.Order.Date',  
              Customer varchar(200) N'$.AccountNumber',   
              Quantity int          N'$.Item.Quantity'  
           )  
  AS SalesOrderJsonData  
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'  
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified  
```  
  
 È possibile usare sia le colonne sia i valori della tabella standard dal testo JSON nella stessa query. È possibile aggiungere indici nell'espressione `JSON_VALUE(Tab.json, '$.Status')` per migliorare le prestazioni della query. Per altre informazioni, vedere [Indicizzazione dei dati JSON](../../relational-databases/json/index-json-data.md).
  
## <a name="import-json-data-into-sql-server-tables"></a>Importare i dati JSON in tabelle di SQL Server  
 Se è necessario caricare dati JSON da un servizio esterno in SQL Server, è possibile usare **OPENJSON** per importare i dati in SQL Server, anziché analizzare i dati nel livello dell'applicazione.  
  
```tsql  
DECLARE @jsonVariable NVARCHAR(MAX)

SET @jsonVariable = N'[  
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
  
INSERT INTO SalesReport  
SELECT SalesOrderJsonData.*  
FROM OPENJSON (@jsonVariable, N'$.Orders.OrdersArray')  
           WITH (  
              Number   varchar(200) N'$.Order.Number',   
              Date     datetime     N'$.Order.Date',  
              Customer varchar(200) N'$.AccountNumber',   
              Quantity int          N'$.Item.Quantity'  
           )  
  AS SalesOrderJsonData;  
```  
  
 Il contenuto della variabile JSON può essere fornito da un servizio REST esterno, inviato come parametro da un framework JavaScript sul lato client o caricato da file esterni. È possibile inserire, aggiornare o unire facilmente i risultati dal testo JSON in una tabella SQL. Per altre informazioni su questo scenario, vedere i post di blog seguenti.
-   [importare i dati JSON in SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/09/22/openjson-the-easiest-way-to-import-json-text-into-table/)
-   [eseguire l'upsert dei documenti JSON in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/03/upsert-json-documents-in-sql-server-2016)
-   [caricare i dati GeoJSON in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/).  
  
## <a name="load-json-files-into-sql-server"></a>Caricare file JSON in SQL Server  
 Le informazioni archiviate nei file possono essere formattate come JSON standard o JSON delimitato da righe. SQL Server può importare il contenuto di file JSON, analizzarlo usando le funzioni **OPENJSON** e **JSON_VALUE** e caricarlo nelle tabelle.  
  
-   Se i documenti JSON vengono archiviati in file locali, unità di rete condivise o posizioni di archiviazione file di Azure accessibili da SQL Server, è possibile usare l'importazione in blocco per caricare i dati JSON in SQL Server. Per altre informazioni su questo scenario, vedere [Importing JSON files into SQL Server using OPENROWSET (BULK)](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2015/10/07/importing-json-files-into-sql-server-using-openrowset-bulk.aspx)(Importazione di file JSON in SQL Server usando OPENROWSET (BULK)).  
  
-   Se i file JSON delimitati da righe vengono archiviati in Archiviazione BLOB Azure o nel file system di Hadoop, è possibile usare PolyBase per caricare il testo JSON, analizzarlo nel codice Transact-SQL e caricarlo nelle tabelle.  
  
## <a name="test-drive-built-in-json-support"></a>Test drive del supporto JSON integrato  
 **Test drive del supporto JSON integrato con il database di esempio AdventureWorks.** Per ottenere il database di esempio AdventureWorks, è necessario scaricare almeno il file di database e il file di script ed esempi da [qui](https://www.microsoft.com/en-us/download/details.aspx?id=49502). Dopo aver ripristinato il database di esempio in un'istanza di SQL Server 2016, decomprimere il file di esempi e aprire il file "JSON Sample Queries procedures views and indexes.sql" dalla cartella JSON. Eseguire gli script in questo file per riformattare alcuni dati esistenti come dati JSON, eseguire report e query di esempio sui dati JSON, indicizzare i dati JSON e importare ed esportare JSON.  
  
 Di seguito sono elencate le operazioni possibili con gli script inclusi nel file.  
  
1.  Denormalizzare lo schema esistente per creare colonne di dati JSON.  
  
    1.  Archiviare informazioni dalle tabelle SalesReasons SalesOrderDetails, SalesPerson, Customer e da altre tabelle che contengono informazioni relative all'ordine di vendita nelle colonne JSON della tabella SalesOrder_json.  
  
    2.  Archiviare informazioni dalle tabelle EmailAddresses/PersonPhone nella tabella Person_json come matrici di oggetti JSON.  
  
2.  Creare procedure e viste che eseguono query sui dati JSON.  
  
3.  Indicizzare i dati JSON: creare indizi sulle proprietà JSON e indici full-text.  
  
4.  Importare ed esportare JSON: creare ed eseguire procedure per esportare il contenuto delle tabelle Person e SalesOrder come risultati JSON, quindi importare e aggiornare le tabelle Person e SalesOrder usando input JSON.  
  
5.  Eseguire esempi di query: eseguire alcune query che chiamano le stored procedure e le viste create nei passaggi 2 e 4.  
  
6.  Eseguire la pulizia degli script: eseguire alcune query che chiamano le stored procedure e le viste create nei passaggi 2 e 4.  
  
## <a name="learn-more-about-built-in-json-support"></a>Altre informazioni sul supporto JSON integrato  
  
### <a name="topics-in-this-section"></a>Argomenti in questa sezione  
 [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
 Usare la clausola FOR JSON per delegare la formattazione dell'output JSON dalle applicazioni client a SQL Server.  
  
 [Convertire dati JSON in righe e colonne con la funzione OPENJSON &#40;SQL Server&#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)  
 Usare la clausola OPENJSON per importare i dati JSON in SQL Server o per convertire dati JSON in formato relazionale per un'app o un servizio che al momento non utilizza direttamente JSON, ad esempio SQL Server Integration Services.  
  
 [Convalidare, eseguire query e modificare i dati JSON con funzioni predefinite &#40;SQL Server&#41;](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)  
 Usare queste funzioni predefinite per convalidare il testo JSON e per estrarre un valore scalare, un oggetto o una matrice.  
  
 [JSON Path Expressions (Espressioni di percorso JSON) &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
 Usare un'espressione di percorso per specificare il testo JSON che si vuole usare.  
  
 [Indicizzazione dei dati JSON](../../relational-databases/json/index-json-data.md)  
 Usare colonne calcolate per creare indici con riconoscimento delle regole di confronto rispetto alle proprietà nei documenti JSON.  
  
[Risolvere i problemi comuni di JSON in SQL Server](../../relational-databases/json/solve-common-issues-with-json-in-sql-server.md)  
 Trovare le risposte ad alcune domande comuni sul supporto JSON integrato in SQL Server.  
  
### <a name="microsoft-blog-posts"></a>Post del blog Microsoft  
  
-   [Post di blog di Jovan Popovic, Microsoft Program Manager](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
### <a name="reference-topics"></a>Argomenti di riferimento  
  
-   [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md) (FOR JSON)  
  
-   [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
-   [Funzioni JSON &#40;Transact-SQL&#41;](../../t-sql/functions/json-functions-transact-sql.md)  
  
    -   [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)  
  
    -   [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)  
  
    -   [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
    -   [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)  
  
  

