---
title: "Modalit&#224; di conversione di FOR JSON dei tipi di dati SQL Server in tipi di dati JSON (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON, conversione del tipo di dati"
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Modalit&#224; di conversione di FOR JSON dei tipi di dati SQL Server in tipi di dati JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  La clausola **FOR JSON** usa le regole seguenti per convertire i tipi di dati SQL Server in tipi JSON nell'output JSON.  
  
|Category|Tipo di dati di SQL Server|Tipo di dati JSON|  
|--------------|--------------|---------------|  
|Tipi stringa e carattere|(n)(var)(char)|string|  
|Tipi numerici|int, bigint, float, decimal, numeric|number|  
|Tipo bit|bit|Booleano (true o false)|  
|Tipi data e ora|date, datetime, datetime2, time, datetimeoffset|string|  
|Tipi binari|varbinary, binary, image, timestamp, rowversion|Stringa con codifica BASE64|  
|Tipi CLR|CLR, geometry, geography|Non supportato. Questi tipi restituiscono un errore.<br /><br /> Nell'istruzione SELECT usare CAST o CONVERT, oppure usare una proprietà o un metodo CLR, per convertire i dati in un tipo convertibile in un tipo JSON. Usare ad esempio **ToString()** per qualsiasi tipo CLR o **STAsText()** per il tipo geometry. Il tipo del valore di output JSON è quindi derivato dal tipo restituito della conversione che si usa nell'istruzione SELECT.|  
|Altri tipi|uniqueidentifier, money|string|  
  
## Vedere anche  
 [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  