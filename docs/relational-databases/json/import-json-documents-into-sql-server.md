---
title: Importare documenti JSON in SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e908ec0-7173-4cd2-8f48-2700757b53a5
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fafe626643707982162ce03a02b9f707b6be2995
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="import-json-documents-into-sql-server"></a>Importare documenti JSON in SQL Server
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Questo argomento descrive come importare file JSON in SQL Server. Attualmente sono disponibili molti documenti JSON archiviati in file. I sensori generano informazioni archiviate in file JSON, le applicazioni registrano informazioni in file JSON e così via. È importante essere in grado di leggere i dati JSON archiviati in file, caricare i dati in SQL Server e quindi analizzarli.

## <a name="import-a-json-document-into-a-single-column"></a>Importare un documento JSON in una singola colonna
**OPENROWSET(BULK)** è una funzione con valori di tabella che consente di leggere i dati da qualsiasi file nell'unità locale o in rete, se SQL Server ha accesso in lettura a tale percorso. Restituisce una tabella con una sola colonna con il contenuto del file. Sono disponibili diverse opzioni che è possibile usare con la funzione OPENROWSET(BULK), ad esempio i separatori. Nel caso più semplice, tuttavia, è possibile limitarsi a caricare l'intero contenuto di un file come un valore di testo, per poi caricare il contenuto di tale valore in una variabile o una tabella. Questo singolo valore di grandi dimensioni è noto come singolo oggetto CLOB (Character Large Object) o SINGLE_CLOB. 

Di seguito è riportato un esempio della funzione **OPENROWSET(BULK)** che legge il contenuto di un file JSON e lo restituisce all'utente come singolo valore:

```tsql
SELECT BulkColumn
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j
 ```

OPENJSON(BULK) legge il contenuto del file e lo restituisce in `BulkColumn`.

È anche possibile caricare il contenuto del file in una variabile locale o in una tabella, come illustrato nell'esempio seguente:

```tsql
-- Load file contents into a variable
SELECT @json = BulkColumn
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j

-- Load file contents into a table 
SELECT BulkColumn
 INTO #temp 
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j
```

## <a name="import-multiple-json-documents"></a>Importare più documenti JSON
È possibile usare lo stesso approccio per caricare un set di file JSON dal file system in variabili locali. Si supponga che i file siano denominati `book<index>.json`.
  
```tsql
declare @i int = 1
declare @json AS nvarchar(MAX)

while(@i < 10)
begin
    SET @file = 'C:\JSON\Books\book' + cast(@i as varchar(5)) + '.json';
    SELECT @json = BulkColumn FROM OPENROWSET (BULK (@file), SINGLE_CLOB) as j
    SELECT * FROM OPENJSON(@json) as json
    set @i = @i + 1 ;
end
```

## <a name="import-json-documents-from-azure-file-storage"></a>Importare documenti JSON dall'archiviazione file di Azure
È possibile usare lo stesso approccio descritto in precedenza per leggere i file JSON da percorsi di file accessibili da SQL Server. L'archiviazione file di Azure, ad esempio, supporta il protocollo SMB. Di conseguenza è possibile mappare un'unità virtuale locale alla condivisione di archiviazione file di Azure tramite la procedura seguente:
1.  Creare un account di archiviazione di file (ad esempio, `mystorage`), una condivisione file (ad esempio, `sharejson`) e una cartella nell'archiviazione file di Azure tramite il portale di Azure o Azure PowerShell.
2.  Caricare alcuni file JSON nella condivisione di archiviazione di file.
3.  Creare una regola del firewall in uscita in Windows Firewall nel computer per consentire la porta 445. Si noti che il provider di servizi Internet potrebbe bloccare questa porta. Se si verifica un errore DNS (errore 53) nel passaggio seguente, significa che la porta 445 non è stata aperta o è bloccata dall'ISP.
4.  Montare la condivisione di archiviazione file di Azure come unità locale (ad esempio `T:`) con il comando seguente:

    ```
    net use [drive letter] \\[storage name].file.core.windows.net\[share name] /u:[storage account name] [storage account access key]
    ```

    Ecco un esempio:

    ```
    net use t: \\mystorage.file.core.windows.net\sharejson /u:myaccount hb5qy6eXLqIdBj0LvGMHdrTiygkjhHDvWjUZg3Gu7bubKLg==
    ```

    La chiave dell'account di archiviazione e la chiave di accesso all'account di archiviazione primario o secondario sono disponibili nella sezione Chiavi in Impostazioni nel portale di Azure.


5.  È ora possibile accedere ai file JSON usando il nome della condivisione, come illustrato nell'esempio seguente:

    ```tsql
    SELECT book.* FROM
     OPENROWSET(BULK N't:\books\books.json', SINGLE_CLOB) AS json
     CROSS APPLY OPENJSON(BulkColumn)
     WITH( id nvarchar(100), name nvarchar(100), price float,
        pages_i int, author nvarchar(100)) AS book
    ```

Per altre informazioni sull'archiviazione file di Azure, vedere [Archiviazione file](https://azure.microsoft.com/en-us/services/storage/files/).

## <a name="import-json-documents-from-azure-blob-storage"></a>Importare documenti JSON da Archiviazione BLOB di Azure

È possibile caricare i file direttamente nel database SQL di Azure da Archiviazione BLOB di Azure con il comando T-SQL BULK INSERT e la funzione OPENROWSET.

Creare innanzitutto l'origine dati esterna, come illustrato nell'esempio seguente.

```tsql
CREATE EXTERNAL DATA SOURCE MyAzureBlobStorage
 WITH ( TYPE = BLOB_STORAGE,
        LOCATION = 'https://myazureblobstorage.blob.core.windows.net',
        CREDENTIAL= MyAzureBlobStorageCredential);
```

Eseguire poi un comando BULK INSERT con l'opzione DATA_SOURCE.

```tsql
BULK INSERT Product
FROM 'data/product.dat'
WITH ( DATA_SOURCE = 'MyAzureBlobStorage');
```

Per altre informazioni e un esempio di OPENROWSET, vedere [Loading files from Azure Blob Storage into Azure SQL Database](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/02/23/loading-files-from-azure-blob-storage-into-azure-sql-database/) (Caricamento di file da Archiviazione BLOB di Azure nel database SQL di Azure).

## <a name="parse-json-documents-into-rows-and-columns"></a>Analizzare i documenti JSON come righe e colonne
Invece di leggere un file JSON intero come singolo valore, può essere utile analizzarlo e restituire i libri nel file e le relative proprietà in righe e colonne. Questo esempio usa un file JSON contenente un elenco di libri da [questo sito](https://github.com/tamingtext/book/blob/master/apache-solr/example/exampledocs/books.json).

Nell'esempio più semplice, è possibile caricare semplicemente l'intero elenco dal file. 

```tsql
SELECT value
 FROM OPENROWSET (BULK 'C:\JSON\Books\books.json', SINGLE_CLOB) as j
 CROSS APPLY OPENJSON(BulkColumn)
```

OPENROWSET legge un singolo valore di testo dal file, lo restituisce come BulkColumn e lo passa alla funzione OPENJSON. OPENJSON scorre la matrice di oggetti JSON nella matrice BulkColumn e restituisce un libro, formattato come JSON, in ogni riga:

```
{"id" : "978-0641723445″, "cat" : ["book","hardcover"], "name" : "The Lightning Thief", … 
{"id" : "978-1423103349″, "cat" : ["book","paperback"], "name" : "The Sea of Monsters", … 
{"id" : "978-1857995879″, "cat" : ["book","paperback"], "name" : "Sophie’s World : The Greek … 
{"id" : "978-1933988177″, "cat" : ["book","paperback"], "name" : "Lucene in Action, Second … 
```

La funzione OPENJSON può analizzare il contenuto JSON e trasformarlo in una tabella o un set di risultati. L'esempio seguente carica il contenuto, analizza i dati JSON caricati e restituisce i cinque campi come colonne:

```tsql
SELECT book.*
 FROM OPENROWSET (BULK 'C:\JSON\Books\books.json', SINGLE_CLOB) as j
 CROSS APPLY OPENJSON(BulkColumn)
 WITH( id nvarchar(100), name nvarchar(100), price float,
 pages_i int, author nvarchar(100)) AS book
```

In questo esempio, OPENROWSET(BULK) legge il contenuto del file e passa il contenuto alla funzione OPENJSON con uno schema definito per l'output. OPENJSON stabilisce le corrispondenze per le proprietà negli oggetti JSON usando i nomi di colonna. Ad esempio, la proprietà `price` viene restituita come una colonna `price` e convertita nel tipo di dati float. Ecco i risultati:

|ID|Nome|price|pages_i|Autore
|---|---|---|---|---|
978-0641723445|The Lightning Thief|12,5|384|Rick Riordan| 
978-1423103349|The Sea of Monsters|6,49|304|Rick Riordan| 
978-1857995879|Sophie’s World : The Greek Philosophers|3,07|64|Jostein Gaarder| 
978-1933988177|Lucene in Action, Second Edition|30,5|475|Michael McCandless| 

A questo punto è possibile restituire questa tabella all'utente o caricare i dati in un'altra tabella.

## <a name="learn-more-about-built-in-json-support-in-sql-server"></a>Altre informazioni sul supporto JSON integrato in SQL Server  
 [Post di blog di Jovan Popovic, Microsoft Program Manager](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## <a name="see-also"></a>Vedere anche
[Convertire dati JSON in righe e colonne con la funzione OPENJSON](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)


