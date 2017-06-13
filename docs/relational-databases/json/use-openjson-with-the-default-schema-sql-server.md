---
title: Usare OPENJSON con lo Schema predefinito (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OPENJSON, with default schema
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 2aa30c8c5e0257a819d58688c90b24782d3fd153
ms.contentlocale: it-it
ms.lasthandoff: 06/09/2017

---
# <a name="use-openjson-with-the-default-schema-sql-server"></a>Usare OPENJSON con lo Schema predefinito (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  L'uso della funzione **OPENJSON** con lo schema predefinito restituisce una tabella con una riga per ogni proprietà dell'oggetto o per ogni elemento nella matrice.  
  
 Di seguito sono riportati alcuni esempi che usano **OPENJSON** con lo schema predefinito. Per altre informazioni ed esempi, vedere [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="example---return-each-property-of-an-object"></a>Esempio: restituire ogni proprietà di un oggetto  
 **Query**  
  
```sql  
SELECT *
FROM OPENJSON('{"name":"John","surname":"Doe","age":45}') 
```  
  
 **Risultati**  
  
|Key|Valore|  
|---------|-----------|  
|name|John|  
|surname|Doe|  
|age|45|  
  
## <a name="example---return-each-element-of-an-array"></a>Esempio: restituire ogni elemento di una matrice  
 **Query**  
  
```sql  
SELECT [key],value
FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]') 
```  
  
 **Risultati**  
  
|Key|Valore|  
|---------|-----------|  
|0|en-GB|  
|1|en-UK|  
|2|de-AT|  
|3|es-AR|  
|4|sr-Cyrl|  
  
## <a name="example---convert-json-to-a-temporary-table"></a>Esempio: convertire JSON in una tabella temporanea  
 La query seguente restituisce tutte le proprietà dell'oggetto **info** .  
  
```sql  
DECLARE @json NVARCHAR(MAX)

SET @json=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }'

SELECT *
FROM OPENJSON(@json,N'lax $.info')
```  
  
 **Risultati**  
  
|Key|Valore|Tipo|  
|---------|-----------|----------|  
|Tipo|1|0|  
|address|{ "town":"Bristol", "county":"Avon", "country":"England" }|5|  
|tags|[ "Sport", "Water polo" ]|4|  
  
## <a name="example---combine-relational-data-and-json-data"></a>Esempio: combinare dati relazionali e dati JSON  
 Nell'esempio seguente, la tabella SalesOrderHeader include una colonna di testo SalesReason che contiene una matrice di SalesOrderReasons in formato JSON. Gli oggetti SalesOrderReasons contengono proprietà come "Produttore" e "Qualità". Nell'esempio viene creato un report che unisce ogni riga dell'ordine di vendita ai motivi di vendita correlati espandendo la matrice JSON dei motivi di vendita come se questi fossero archiviati in una tabella figlio separata.  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
 In questo esempio, OPENJSON restituisce una tabella dei motivi di vendita in cui questi vengono visualizzati come colonna valore. L'operatore CROSS APPLY unisce ogni riga dell'ordine di vendita alle righe restituite dalla funzione con valori di tabella OPENJSON.  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Acquisire familiarità con il supporto JSON integrato in SQL Server  
Per un numero elevato di soluzioni specifiche, casi di utilizzo e indicazioni, vedere il [post di blog sul supporto JSON predefinito](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e Database SQL di Azure per Microsoft Program Manager Jovan Popovic.
  
## <a name="see-also"></a>Vedere anche  
 [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  

