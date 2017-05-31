---
title: Convertire dati JSON in righe e colonne con la funzione OPENJSON (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OPENJSON
- JSON, importing
- importing JSON
ms.assetid: 0c139901-01e2-49ef-9d62-57e08e32c68e
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ea85d2dff3afe1b5e5b56117255576f8d0ae2180
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="convert-json-data-to-rows-and-columns-with-openjson-sql-server"></a>Convertire dati JSON in righe e colonne con la funzione OPENJSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

La funzione dei set di righe **OPENJSON** consente di convertire testo JSON in un set di righe e colonne. Usare **OPENJSON** per eseguire query SQL sulle raccolte JSON o importare testo JSON all'interno di tabelle di SQL Server.  
  
 La funzione **OPENJSON** accetta un singolo oggetto JSON o una raccolta di oggetti JSON e li trasforma in una o più righe. Per impostazione predefinita, la funzione **OPENJSON** restituisce le informazioni seguenti.
-   Da un oggetto JSON, tutte le coppie chiave:valore trovate al primo livello.
-   Da una matrice JSON, tutti gli elementi della matrice con i rispettivi indici.  
  
Facoltativamente, aggiungere una clausola **WITH** per specificare lo schema delle righe restituite dalla funzione **OPENJSON**. Questo schema esplicito definisce la struttura dell'output.  
  
## <a name="use-openjson-without-an-explicit-schema-for-the-output"></a>Usare OPENJSON senza uno schema esplicito per l'output
Quando si usa la funzione **OPENJSON** senza specificare uno schema esplicito per i risultati, vale a dire senza una clausola **WITH** dopo OPENJSON, la funzione restituisce una tabella con le tre colonne seguenti.
1.  Il nome della proprietà nell'oggetto di input (o l'indice dell'elemento nella matrice di input).
2.  Il valore della proprietà o l'elemento della matrice.
3.  Il tipo (ad esempio, stringa, numero, valore booleano, matrice o oggetto).

Ogni proprietà dell'oggetto JSON o ogni elemento della matrice viene restituito come riga separata.  

Questo semplice esempio usa la funzione **OPENJSON** con lo schema predefinito e restituisce una riga per ogni proprietà dell'oggetto JSON.  
 
**Esempio**
```tsql  
DECLARE @json NVARCHAR(MAX)

SET @json='{"name":"John","surname":"Doe","age":45,"skills":["SQL","C#","MVC"]}';

SELECT *
FROM OPENJSON(@json);
```  
  
**Risultati**  
  
|Key|Valore|tipo|  
|---------|-----------|----------|  
|name|John|1|  
|surname|Doe|1|  
|age|45|2|  
|skills|["SQL","C#","MVC"]|4|

### <a name="more-info"></a>Altre informazioni

Per altre info e altri esempi, vedere [Use OPENJSON with the Default Schema &#40;SQL Server&#41;](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md) (Usare OPENJSON con lo schema predefinito (SQL Server)).

Per la sintassi e l'utilizzo, vedere [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md). 

    
## <a name="use-openjson-with-an-explicit-schema-for-the-output"></a>Usare OPENJSON con uno schema esplicito per l'output
Quando si specifica uno schema per i risultati tramite la clausola **WITH** della funzione **OPENJSON**, la funzione restituisce una tabella che include solo le colonne definite nella clausola **WITH**. Nella clausola **WITH** è necessario specificare le colonne di output, i relativi tipi e i percorsi delle proprietà di origine JSON per ogni valore di output. **OPENJSON** esegue l'iterazione della matrice di oggetti JSON, legge il valore nel percorso specificato per ogni colonna e converte il valore nel tipo specificato.  

Ecco un rapido esempio che usa **OPENJSON** con uno schema per i risultati specificato in modo esplicito.  
  
**Esempio**
  
```tsql  
DECLARE @json NVARCHAR(MAX)
SET @json =   
  N'[  
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
   
SELECT * FROM  
 OPENJSON ( @json )  
WITH (   
              Number   varchar(200) '$.Order.Number' ,  
              Date     datetime     '$.Order.Date',  
              Customer varchar(200) '$.AccountNumber',  
              Quantity int          '$.Item.Quantity'  
 ) 
```  
  
**Risultati**  
  
|Number|Data|Customer|Quantity|  
|------------|----------|--------------|--------------|  
|SO43659|2011-05-31T00:00:00|AW29825|1|  
|SO43661|2011-06-01T00:00:00|AW73565|3|  
  
 Questa funzione restituisce e formatta gli elementi di una matrice JSON.  
  
-   Per ogni elemento nella matrice JSON la funzione **OPENJSON** genera una nuova riga nella tabella di output. I due elementi nella matrice JSON vengono convertiti in due righe nella tabella restituita.  
  
-   Per ogni colonna specificata tramite la sintassi `colName type json_path` la funzione **OPENJSON** converte il valore trovato in ogni elemento della matrice nel percorso specificato nel tipo specificato e popola una cella della tabella di output. In questo esempio i valori per la colonna `Date` vengono ricavati da ciascun oggetto nel percorso `$.Order.Date` e convertiti in valori datetime.  
  
Dopo aver trasformato la raccolta JSON in un set di righe con **OPENJSON**, è possibile eseguire qualsiasi query SQL sui dati restituiti o inserirli in una tabella.  

### <a name="more-info"></a>Altre informazioni
Per altre info e altri esempi, vedere [Usare OPENJSON con uno schema esplicito &#40;SQL Server&#41;](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md).

Per la sintassi e l'utilizzo, vedere [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md).

## <a name="openjson-requires-compatibility-level-130"></a>OPENJSON richiede il livello di compatibilità 130
La funzione **OPENJSON** è disponibile per il **livello di compatibilità 130**. Se il livello di compatibilità del database è inferiore a 130, SQL Server non riuscirà a trovare e a eseguire la funzione **OPENJSON** . Altre funzioni JSON predefinite sono disponibili in tutti i livelli di compatibilità. È possibile controllare il livello di compatibilità nella vista sys.databases o nelle proprietà del database.

È possibile modificare il livello di compatibilità del database tramite il comando seguente:   
`ALTER DATABASE <DatabaseName> SET COMPATIBILITY_LEVEL = 130`  

## <a name="learn-more-about-openjson-and-built-in-json-support-in-sql-server"></a>Altre informazioni sulla funzione OPENJSON e sul supporto JSON predefinito in SQL Server  
 [Post di blog di Jovan Popovic, Microsoft Program Manager](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## <a name="see-also"></a>Vedere anche  
 [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  

