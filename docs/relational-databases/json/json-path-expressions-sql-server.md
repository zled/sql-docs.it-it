---
title: Espressioni di percorso JSON (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 01/23/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, path expressions
- path expressions (JSON)
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 07c873941669f7a36ff9b93651a938ecae2662b7
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="json-path-expressions-sql-server"></a>Espressioni di percorso JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Usare le espressioni di percorso JSON per fare riferimento alle proprietà degli oggetti JSON.  
  
 È necessario specificare un'espressione di percorso quando si chiamano le funzioni seguenti.  
  
-   Quando si chiama **OPENJSON** per creare una vista relazionale dei dati JSON. Per altre informazioni, vedere [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
-   Quando si chiama **JSON_VALUE** per estrarre un valore dal testo JSON. Per altre informazioni, vedere [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md).  
  
-   Quando si chiama **JSON_QUERY** per estrarre un oggetto o una matrice JSON. Per altre informazioni, vedere [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  
  
-   Quando si chiama **JSON_MODIFY** per aggiornare il valore di una proprietà in una stringa JSON. Per altre informazioni, vedere [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  

## <a name="parts-of-a-path-expression"></a>Parti di un'espressione di percorso
 Un'espressione di percorso include due componenti.  
  
1.  La [modalità percorso](#PATHMODE) facoltativa, con valore **lax** o **strict**.  
  
2.  Il [percorso](#PATH) stesso.  

##  <a name="PATHMODE"></a> Path mode  
 All'inizio dell'espressione di percorso, è possibile dichiarare la modalità percorso specificando la parola chiave **lax** o **strict**. Il valore predefinito è **lax**.  
  
-   Nella modalità **lax** la funzione restituisce valori vuoti se l'espressione di percorso contiene un errore. Se ad esempio si richiede il valore **$.name** e il testo JSON non contiene una chiave **name**, la funzione restituisce Null ma non genera un errore.  
  
-   Nella modalità **strict** la funzione genera un errore se l'espressione di percorso contiene un errore.  

La query seguente specifica in modo esplicito la modalità `lax` nell'espressione di percorso.

```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{ ... }'

SELECT * FROM OPENJSON(@json, N'lax $.info')
```  
  
##  <a name="PATH"></a> Path  
 Dopo la dichiarazione facoltativa della modalità percorso, specificare il percorso stesso.  
  
-   Il segno di dollaro (`$`) rappresenta l'elemento contesto.  
  
-   Il percorso proprietà è un insieme di passaggi di percorso. I passaggi di percorso possono contenere gli elementi e gli operatori seguenti.  
  
    -   Nomi delle chiavi. Ad esempio `$.name` e `$."first name"`. Se il nome della chiave inizia con un segno di dollaro o contiene caratteri speciali quali spazi, racchiuderlo tra virgolette.   
  
    -   Elementi matrice. Ad esempio, `$.product[3]`. Le matrici sono in base zero.  
  
    -   L'operatore punto (`.`) indica un membro di un oggetto. Ad esempio, in `$.people[1].surname` `surname` è figlio di `people`.
  
## <a name="examples"></a>Esempi  
 Gli esempi inclusi in questa sezione fanno riferimento al testo JSON seguente.  
  
```json  
{
    "people": [{
        "name": "John",
        "surname": "Doe"
    }, {
        "name": "Jane",
        "surname": null,
        "active": true
    }]
}
```  
  
 La tabella seguente illustra alcuni esempi di espressioni di percorso.  
  
|Espressione di percorso|Valore|  
|---------------------|-----------|  
|$.people[0].name|John|  
|$.people[1]|{ "name": "Jane",  "surname": null, "active": true }|  
|$.people[1].surname|null|  
|$|{ "people": [ { "name": "John",  "surname": "Doe" },<br />   { "name": "Jane",  "surname": null, "active": true } ] }|  
  
## <a name="how-built-in-functions-handle-duplicate-paths"></a>Modalità di gestione dei percorsi duplicati da parte delle funzioni predefinite  
 Se il testo JSON contiene proprietà duplicate, ad esempio due chiavi con lo stesso nome sullo stesso livello, le funzioni **JSON_VALUE** e **JSON_QUERY** restituiscono solo il primo valore corrispondente al percorso. Per analizzare un oggetto JSON che contiene chiavi duplicate e restituire tutti i valori, usare **OPENJSON**, come illustrato nell'esempio seguente.  
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{"person":{"info":{"name":"John", "name":"Jack"}}}'

SELECT value
FROM OPENJSON(@json,'$.person.info') 
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Altre informazioni sul supporto JSON integrato in SQL Server  
Per soluzioni specifiche, casi d'uso e indicazioni, vedere i [post del blog sul supporto JSON integrato](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e nel database SQL di Azure redatti da Jovan Popovic, Microsoft Program Manager.
  
## <a name="see-also"></a>Vedere anche  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
  

