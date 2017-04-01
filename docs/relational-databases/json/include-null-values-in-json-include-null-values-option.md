---
title: "Includere valori Null nell&#39;output JSON con l&#39;opzione INCLUDE_NULL_VALUES (SQL Server) | Microsoft Docs"
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
  - "INCLUDE_NULL_VALUES (FOR JSON)"
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 13
---
# Includere valori Null nell&#39;output JSON con l&#39;opzione INCLUDE_NULL_VALUES (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Per includere valori Null nell'output JSON della clausola **FOR JSON**, specificare l'opzione **INCLUDE_NULL_VALUES**.  
  
 Se non si specifica l'opzione **INCLUDE_NULL_VALUES**, l'output JSON non includerà le proprietà per i valori Null presenti nei risultati della query.  
  
## Esempi  
 L'esempio seguente illustra l'output della clausola **FOR JSON** con e senza l'opzione **INCLUDE_NULL_VALUES**  
  
|Senza l'opzione **INCLUDE_NULL_VALUES**|Con l'opzione **INCLUDE_NULL_VALUES**|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 Ecco un altro esempio di clausola **FOR JSON** con l'opzione **INCLUDE_NULL_VALUES**.  
  
 **Query**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES  
```  
  
 **Risultato**  
  
```json  
[   
   {"name": "John",  "surname": null },  
   {"name": "Jane",  "surname": "Doe"}  
]  
```  
  
## Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  