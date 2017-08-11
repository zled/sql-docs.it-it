---
title: Convalidare, eseguire query e modificare i dati JSON con funzioni predefinite (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: d8c99e842ceaa2351c98583238cbba28e2a152c7
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>Convalidare, eseguire query e modificare i dati JSON con funzioni predefinite (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Il supporto integrato per JSON include le funzioni predefinite seguenti descritte brevemente in questo argomento.  
  
-   [ISJSON](#ISJSON) verifica se una stringa include contenuto JSON valido.  
  
-   [JSON_VALUE](#VALUE) estrae un valore scalare da una stringa JSON.  
  
-   [JSON_QUERY](#QUERY) estrae un oggetto o una matrice da una stringa JSON.  
  
-   [JSON_MODIFY](#MODIFY) aggiorna il valore di una proprietà in una stringa JSON e restituisce la stringa JSON aggiornata.  
 
## <a name="json-text-for-the-examples-on-this-page"></a>Testo JSON per gli esempi in questa pagina
Gli esempi in questa pagina usano il testo JSON seguente, che contiene un elemento complesso.

```sql 
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
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
``` 

##  <a name="ISJSON"></a> Convalidare il testo JSON tramite la funzione ISJSON  
 La funzione **ISJSON** verifica se una stringa include contenuto JSON valido.  
  
L'esempio seguente restituisce le righe in cui la colonna `json_col` include contenuto JSON valido.  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  

Per altre informazioni, vedere [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md).  
  
##  <a name="VALUE"></a> Estrarre un valore dal testo JSON tramite la funzione JSON_VALUE  
La funzione **JSON_VALUE** estrae un valore scalare da una stringa JSON.  
  
Nell'esempio seguente viene estratto il valore della proprietà JSON annidata `town` in una variabile locale.  
  
```sql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
Per altre informazioni, vedere [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md).  
  
##  <a name="QUERY"></a> Estrarre un oggetto o una matrice dal testo JSON tramite la funzione JSON_QUERY  
La funzione **JSON_QUERY** estrae un oggetto o una matrice da una stringa JSON.  
 
Nell'esempio seguente viene illustrato come restituire un frammento JSON nei risultati della query.  
  
```sql  
SELECT FirstName, LastName, JSON_QUERY(jsonInfo,'$.info.address') AS Address
FROM Person.Person
ORDER BY LastName
```  
  
Per altre informazioni, vedere [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  
  
##  <a name="JSONCompare"></a> Confronto tra JSON_VALUE e JSON_QUERY  
La differenza principale tra **JSON_VALUE** e **JSON_QUERY** consiste nel fatto che **JSON_VALUE** restituisce un valore scalare, mentre **JSON_QUERY** restituisce un oggetto o una matrice.  
  
Si consideri il testo JSON di esempio seguente.  
  
```json  
{
    "a": "[1,2]",
    "b": [1, 2],
    "c": "hi"
}  
```  
  
In questo testo JSON di esempio i membri dati "a" e "c" sono valori stringa, mentre il membro dati "b" è una matrice. **JSON_VALUE** e **JSON_QUERY** restituiscono i risultati seguenti:  
  
|Percorso|**JSON_VALUE** restituisce|**JSON_QUERY** restituisce|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL o errore|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL o errore|  
|**$.b**|NULL o errore|[1,2]|  
|**$.b[0]**|1|NULL o errore|  
|**$.c**|hi|NULL o errore|  
  
## <a name="test-jsonvalue-and-jsonquery-with-the-adventureworks-sample-database"></a>Test di JSON_VALUE e JSON_QUERY con il database di esempio AdventureWorks  
Testare le funzioni predefinite descritte in questo argomento tramite l'esecuzione degli esempi seguenti con il database di esempio AdventureWorks, contenente i dati JSON. Per ottenere il database di esempio AdventureWorks, [fare clic qui](http://www.microsoft.com/en-us/download/details.aspx?id=49502).  
  
Negli esempi seguenti la colonna `Info` nella tabella `SalesOrder_json` contiene testo JSON.  
  
### <a name="example-1---return-both-standard-columns-and-json-data"></a>Esempio 1: restituire colonne standard e dati JSON  
La query seguente restituisce valori sia dalle colonne relazionali standard sia da una colonna JSON.  
  
```sql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,
 JSON_QUERY(Info,'$.ShippingInfo') ShippingInfo,
 JSON_QUERY(Info,'$.BillingInfo') BillingInfo,
 JSON_VALUE(Info,'$.SalesPerson.Name') SalesPerson,
 JSON_VALUE(Info,'$.ShippingInfo.City') City,
 JSON_VALUE(Info,'$.Customer.Name') Customer,
 JSON_QUERY(OrderItems,'$') OrderItems
FROM Sales.SalesOrder_json
WHERE ISJSON(Info) > 0
```  
  
### <a name="example-2--aggregate-and-filter-json-values"></a>Esempio 2: aggregare e filtrare valori JSON  
La query seguente aggrega i subtotali in base al nome del cliente (archiviato in JSON) e in base allo stato (archiviato in una colonna normale), quindi filtra i risultati in base alla città (archiviata in JSON) e in base al valore OrderDate (archiviato in una colonna normale).  
  
```sql  
DECLARE @territoryid INT;
DECLARE @city NVARCHAR(32);

SET @territoryid=3;

SET @city=N'Seattle';

SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total
FROM Sales.SalesOrder_json
WHERE TerritoryID=@territoryid
 AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city
 AND OrderDate > '1/1/2015'
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status
HAVING SUM(SubTotal)>1000
```  
  
##  <a name="MODIFY"></a> Aggiornare i valori delle proprietà in testo JSON tramite la funzione JSON_MODIFY  
La funzione **JSON_MODIFY** aggiorna il valore di una proprietà in una stringa JSON e restituisce la stringa JSON aggiornata.  
  
Nell'esempio seguente viene aggiornato il valore di una proprietà JSON in una variabile che include contenuto JSON.  
  
```sql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')    
```  
  
 Per altre informazioni, vedere [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  
  
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Altre informazioni sul supporto JSON integrato in SQL Server  
Per soluzioni specifiche, casi d'uso e indicazioni, vedere i [post del blog sul supporto JSON integrato](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e nel database SQL di Azure redatti da Jovan Popovic, Microsoft Program Manager.
  
## <a name="see-also"></a>Vedere anche  
 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)   
 [JSON Path Expressions (Espressioni di percorso JSON) &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  

