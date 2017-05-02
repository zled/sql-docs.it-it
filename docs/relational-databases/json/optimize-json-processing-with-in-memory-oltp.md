---
title: Ottimizzare l&quot;elaborazione JSON con OLTP in memoria | Microsoft Docs
ms.custom: 
ms.date: 02/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9c5adb1-3209-4186-bc10-8e41a26f5e57
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4e0331c288665fd9f69444d0d14366dfa69a668f
ms.lasthandoff: 04/11/2017

---
# <a name="optimize-json-processing-with-in-memory-oltp"></a>Ottimizzare l'elaborazione JSON con OLTP in memoria
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

SQL Server e il database SQL di Azure consentono di usare il testo formattato come JSON. Per migliorare le prestazioni delle query OLTP che elaborano dati JSON, è possibile archiviare i documenti JSON in tabelle con ottimizzazione per la memoria mediante colonne di tipo stringa standard (di tipo NVARCHAR).

## <a name="store-json-in-memory-optimized-tables"></a>Archiviare dati JSON in tabelle con ottimizzazione per la memoria
Nell'esempio seguente è illustrata una tabella `Product` con ottimizzazione per la memoria contenente due colonne JSON, `Tags` e `Data`.

```tsql
CREATE SCHEMA xtp;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED, --standard column
    Name nvarchar(400) NOT NULL, --standard column
    Price float, --standard column

    Tags nvarchar(400),--json stored in string column
    Data nvarchar(4000) --json stored in string column

) WITH (MEMORY_OPTIMIZED=ON);
```
L'archiviazione dei dati JSON in tabelle con ottimizzazione per la memoria aumenta le prestazioni delle query mediante l'accesso ai dati in memoria senza blocco.

## <a name="optimize-json-with-additional-in-memory-features"></a>Ottimizzare l'elaborazione JSON con funzionalità aggiuntive in memoria
Le nuove funzionalità disponibili in SQL Server e nel database SQL di Azure consentono di integrare le funzionalità JSON con le tecnologie OLTP in memoria esistenti. Ad esempio, è possibile eseguire le operazioni seguenti:
 - Convalidare la struttura dei documenti JSON archiviati in tabelle con ottimizzazione per la memoria tramite vincoli CHECK compilati in modo nativo.
 - Esporre e tipizzare i valori archiviati nei documenti JSON tramite le colonne calcolate.
 - Indicizzare i valori nei documenti JSON tramite gli indici con ottimizzazione per la memoria.
 - Compilare in modo nativo le query SQL che usano valori di documenti JSON o formattano i risultati come testo JSON.

## <a name="validate-json-columns"></a>Convalidare le colonne JSON
SQL Server e il database SQL di Azure consentono di aggiungere vincoli CHECK compilati in modo nativo per la convalida del contenuto dei documenti JSON archiviati in una colonna di tipo stringa, come illustrato nell'esempio seguente.

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Tags nvarchar(400)
            CONSTRAINT [Tags should be formatted as JSON]
                CHECK (ISJSON(Tags)=1),
    Data nvarchar(4000)

) WITH (MEMORY_OPTIMIZED=ON);
```

È possibile aggiungere il vincolo CHECK compilato in modo nativo nelle tabelle esistenti che contengono colonne JSON:

```tsql
ALTER TABLE xtp.Product
    ADD CONSTRAINT [Data should be JSON]
        CHECK (ISJSON(Data)=1)
```

I vincoli JSON CHECK compilati in modo nativo garantiscono la corretta formattazione del testo JSON archiviato nelle tabelle con ottimizzazione per la memoria.

## <a name="expose-json-values-using-computed-columns"></a>Esporre i valori JSON tramite le colonne calcolate
Le colonne calcolate consentono di esporre i valori del testo JSON e accedere a tali valori senza ripetere la valutazione delle espressioni che recuperano un valore dal testo JSON e senza dover rieseguire l'analisi della struttura JSON. I valori esposti sono fortemente tipizzati e fisicamente salvati in modo permanente nelle colonne calcolate. L'accesso ai valori JSON tramite le colonne calcolate persistenti è più veloce rispetto all'accesso ai valori nel documento JSON.

Nell'esempio seguente viene illustrato come esporre i due valori seguenti dalla colonna JSON `Data`:
-   paese di produzione del prodotto;
-   costo di produzione del prodotto.

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float)

) WITH (MEMORY_OPTIMIZED=ON);
```

Le colonne calcolate `MadeIn` e `Cost` vengono aggiornate a ogni modifica del documento JSON archiviato nella colonna `Data`.

## <a name="index-values-in-json-columns"></a>Indicizzare i valori nelle colonne JSON
SQL Server e il database SQL di Azure consentono di indicizzare i valori nelle colonne JSON tramite indici con ottimizzazione per la memoria. I valori JSON indicizzati devono essere esposti e fortemente tipizzati tramite le colonne calcolate, come illustrato nell'esempio seguente.

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float) PERSISTED,

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)

) WITH (MEMORY_OPTIMIZED=ON)

ALTER TABLE Product
    ADD INDEX [idx_Product_Cost] NONCLUSTERED HASH(Cost)
        WITH (BUCKET_COUNT=20000)
```
I valori nelle colonne JSON possono essere indicizzati usando sia gli indici NONCLUSTERED sia gli indici HASH standard.
-   Gli indici NONCLUSTERED ottimizzano le query che eseguono la selezione di intervalli di righe in base a un valore JSON oppure l'ordinamento dei risultati in base ai valori JSON.
-   Gli indici HASH garantiscono prestazioni ottimali quando una singola riga o alcune righe vengono recuperate tramite l'immissione del valore esatto da trovare.

## <a name="native-compilation-of-json-queries"></a>Compilazione nativa di query JSON
La compilazione nativa di procedure, funzioni e trigger Transact-SQL contenenti query con funzioni JSON aumenta infine le prestazioni delle query e riduce i cicli di CPU richiesti per eseguire le procedure. Nell'esempio seguente viene illustrata una procedura compilata in modo nativo che usa numerose funzioni JSON, ovvero JSON_VALUE, OPENJSON e JSON_MODIFY.

```tsql
CREATE PROCEDURE xtp.ProductList(@ProductIds nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    SELECT ProductID,Name,Price,Data,Tags, JSON_VALUE(data,'$.MadeIn') AS MadeIn
    FROM xtp.Product
        JOIN OPENJSON(@ProductIds)
            ON ProductID = value

END;

CREATE PROCEDURE xtp.UpdateProductData(@ProductId int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE xtp.Product
    SET Data = JSON_MODIFY(Data, @Property, @Value)
    WHERE ProductID = @ProductId;

END
```

## <a name="next-steps"></a>Passaggi successivi
I dati JSON nei moduli nativi OLTP in memoria assicurano un miglioramento a livello di prestazioni per la funzionalità JSON predefinita disponibile in SQL Server e nel database SQL di Azure.

Per altre informazioni sugli scenari principali per l'uso di JSON, vedere le risorse riportate di seguito:

-   [Blog di TechNet](https://blogs.technet.microsoft.com/dataplatforminsider/2016/01/05/json-in-sql-server-2016-part-1-of-4/)
-   [Documentazione MSDN](https://msdn.microsoft.com/library/dn921897.aspx)
-   [Video di Channel 9](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

Per altre informazioni sui vari scenari per l'integrazione di JSON nell'applicazione, vedere le risorse seguenti:
-   Visualizzare le demo in questo [video di Channel 9](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds).
-   Trovare uno scenario corrispondente al caso d'uso specifico nel [post di blog JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/).
-   Trovare esempi nel [repository GitHub](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/json/).


