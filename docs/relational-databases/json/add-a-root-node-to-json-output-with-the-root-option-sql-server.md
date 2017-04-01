---
title: "Aggiungere un nodo radice all&#39;output JSON con l&#39;opzione ROOT (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ROOT (FOR JSON)"
ms.assetid: b9afa74a-f59f-483e-a178-42be2e9882c9
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# Aggiungere un nodo radice all&#39;output JSON con l&#39;opzione ROOT (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Per aggiungere un unico elemento di primo livello all'output JSON della clausola **FOR JSON**, specificare l'opzione **ROOT**.  
  
 Se non si specifica l'opzione **ROOT**, l'output JSON non includerà alcun elemento radice.  
  
## Esempi  
 La tabella seguente mostra l'output della clausola **FOR JSON** con e senza l'opzione **ROOT**.  
  
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
  
 Ecco un altro esempio di clausola **FOR JSON** con l'opzione **ROOT**. Questo esempio specifica un valore per l'argomento facoltativo *RootName*.  
  
 **Query**  
  
```tsql  
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
  "info": [  
    {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
    {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
    {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
    {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
    {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
  ]  
}  
  
```  
  
 **Risultato (senza radice)**  
  
```json  
[  
  {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
  {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
  {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
  {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
  {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
]  
  
```  
  
## Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  