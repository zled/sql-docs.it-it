---
title: "Rimuovere le parentesi quadre dall&#39;output JSON con l&#39;opzione WITHOUT_ARRAY_WRAPPER (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WITHOUT_ARRAY_WRAPPER"
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Rimuovere le parentesi quadre dall&#39;output JSON con l&#39;opzione WITHOUT_ARRAY_WRAPPER (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Per rimuovere le parentesi quadre che racchiudono l'output JSON della clausola **FOR JSON** per impostazione predefinita, specificare l'opzione **WITHOUT_ARRAY_WRAPPER**. Usare questa opzione per generare un singolo oggetto JSON come output.  
  
 Se non si specifica questa opzione, l'output JSON è racchiuso tra parentesi quadre.  
  
## Esempi  
 L'esempio seguente mostra l'output della clausola **FOR JSON** con e senza l'opzione **WITHOUT_ARRAY_WRAPPER**.  
  
 **Query**  
  
```tsql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Risultato** con l'opzione **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{ "year":2015, "month":12, "day":15 }  
```  
  
 **Risultato** senza l'opzione **WITHOUT_ARRAY_WRAPPER**  
  
```json  
[ { "year":2015, "month":12, "day":15 } ]  
```  
  
 Ecco un altro esempio di clausola **FOR JSON** con l'opzione **WITHOUT_ARRAY_WRAPPER**.  
  
 **Query**  
  
```tsql  
SELECT TOP 1 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Risultato** con l'opzione **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{  
    "SalesOrderNumber":"SO43660",  
    "OrderDate":"2011-05-31T00:00:00",  
    "Status":5  
}  
```  
  
 **Risultato** senza l'opzione **WITHOUT_ARRAY_WRAPPER**  
  
```json  
[  
    {  
        "SalesOrderNumber":"SO43660",  
        "OrderDate":"2011-05-31T00:00:00",  
        "Status":5  
    }  
]  
```  
  
## Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  