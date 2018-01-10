---
title: Usare OPENJSON con lo Schema predefinito (SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: OPENJSON, with default schema
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3da875380580bcf7151db13c0b14280a9790d5dc
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="use-openjson-with-the-default-schema-sql-server"></a>Usare OPENJSON con lo Schema predefinito (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  L'uso della funzione **OPENJSON** con lo schema predefinito restituisce una tabella con una riga per ogni proprietà dell'oggetto o per ogni elemento nella matrice.  
  
 Di seguito sono riportati alcuni esempi che usano **OPENJSON** con lo schema predefinito. Per altre informazioni ed esempi, vedere [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="example---return-each-property-of-an-object"></a>Esempio: restituire ogni proprietà di un oggetto  
 **Query**  
  
```sql  
SELECT *
FROM OPENJSON('{"name":"John","surname":"Doe","age":45}') 
```  
  
 **Risultati**  
  
|Key|valore|  
|---------|-----------|  
|NAME|John|  
|surname|Doe|  
|age|45|  
  
## <a name="example---return-each-element-of-an-array"></a>Esempio: restituire ogni elemento di una matrice  
 **Query**  
  
```sql  
SELECT [key],value
FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]') 
```  
  
 **Risultati**  
  
|Key|valore|  
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
  
|Key|valore|Tipo|  
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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Altre informazioni sul supporto JSON integrato in SQL Server  
Per soluzioni specifiche, casi d'uso e indicazioni, vedere i [post del blog sul supporto JSON integrato](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e nel database SQL di Azure redatti da Jovan Popovic, Microsoft Program Manager.
  
## <a name="see-also"></a>Vedere anche  
 [OPENJSON &#40; Transact-SQL &#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  
