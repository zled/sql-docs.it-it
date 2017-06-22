---
title: Aggiungere un nodo radice all'output JSON con l'opzione ROOT (SQL Server) | Microsoft Docs
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
- ROOT (FOR JSON)
ms.assetid: b9afa74a-f59f-483e-a178-42be2e9882c9
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: e7b316ab5b6f809b348fa882a42a89431590c40b
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="add-a-root-node-to-json-output-with-the-root-option-sql-server"></a>Aggiungere un nodo radice all'output JSON con l'opzione ROOT (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Per aggiungere un unico elemento di primo livello all'output JSON della clausola **FOR JSON** , specificare l'opzione **ROOT** .  
  
 Se non si specifica l'opzione **ROOT** , l'output JSON non includerà alcun elemento radice.  
  
## <a name="examples"></a>Esempi  
 La tabella seguente mostra l'output della clausola **FOR JSON** con e senza l'opzione **ROOT** .  
  
 Gli esempi nella tabella seguente presuppongono che l'argomento facoltativo *RootName* sia vuoto. Se si specifica un nome per l'elemento radice, questo valore sostituirà il valore **root** negli esempi.  
  
 Senza l'opzione **ROOT**  
  
```json  
{  
   <<json properties>>  
}  
```  
  
```json  
[  
   <<json array elements>>  
]  
```  
  
 Con l'opzione **ROOT**  
  
```json  
{   
  "root": {  
   <<json properties>>  
 }  
}  
```  
  
```json  
{   
  "root": [  
   << json array elements >>  
  ]  
}  
```  
  
 Ecco un altro esempio di clausola **FOR JSON** con l'opzione **ROOT** . Questo esempio specifica un valore per l'argomento facoltativo *RootName* .  
  
 **Query**  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON PATH, ROOT('info')
```  
  
 **Risultato**  
  
```json  
{
    "info": [{
        "Id": 1,
        "FirstName": "Ken",
        "LastName": "Sánchez",
        "Info": {
            "MiddleName": "J"
        }
    }, {
        "Id": 2,
        "FirstName": "Terri",
        "LastName": "Duffy",
        "Info": {
            "MiddleName": "Lee"
        }
    }, {
        "Id": 3,
        "FirstName": "Roberto",
        "LastName": "Tamburello"
    }, {
        "Id": 4,
        "FirstName": "Rob",
        "LastName": "Walters"
    }, {
        "Id": 5,
        "FirstName": "Gail",
        "LastName": "Erickson",
        "Info": {
            "Title": "Ms.",
            "MiddleName": "A"
        }
    }]
}
```  
  
 **Risultato (senza radice)**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sánchez",
    "Info": {
        "MiddleName": "J"
    }
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info": {
        "MiddleName": "Lee"
    }
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info": {
        "Title": "Ms.",
        "MiddleName": "A"
    }
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Acquisire familiarità con il supporto JSON integrato in SQL Server  
Per un numero elevato di soluzioni specifiche, casi di utilizzo e indicazioni, vedere il [post di blog sul supporto JSON predefinito](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e Database SQL di Azure per Microsoft Program Manager Jovan Popovic.
 
## <a name="see-also"></a>Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

