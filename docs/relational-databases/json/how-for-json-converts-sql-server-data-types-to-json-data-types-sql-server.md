---
title: "Modalità di conversione di FOR JSON dei tipi di dati SQL Server in tipi di dati JSON (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 07/07/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5c5f0145e3a5f2809acc4d68decc206d5799b35
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>Modalità di conversione di FOR JSON dei tipi di dati SQL Server in tipi di dati JSON (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  La clausola **FOR JSON** usa le regole seguenti per convertire i tipi di dati SQL Server in tipi JSON nell'output JSON.  
  
|Category|Tipo di dati di SQL Server|Tipo di dati JSON|  
|--------------|--------------|---------------|  
|Tipi stringa e carattere|char, nchar, varchar, nvarchar|string|  
|Tipi numerici|int, bigint, float, decimal, numeric|number|  
|Tipo bit|bit|Booleano (true o false)|  
|Tipi data e ora|date, datetime, datetime2, time, datetimeoffset|string|  
|Tipi binari|varbinary, binary, image, timestamp, rowversion|Stringa con codifica BASE64|  
|Tipi CLR|geometry, geography, altri tipi CLR|Non supportato. Questi tipi restituiscono un errore.<br /><br /> Nell'istruzione SELECT usare CAST o CONVERT, oppure una proprietà o un metodo CLR, per convertire i dati di origine in un tipo di dati SQL Server convertibile correttamente in un tipo JSON. Usare ad esempio **STAsText()** per il tipo geometry o **ToString()** per qualsiasi tipo CLR. Il tipo del valore di output JSON è quindi derivato dal tipo restituito della conversione che si usa nell'istruzione SELECT.|  
|Altri tipi|uniqueidentifier, money|string|  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Altre informazioni sul supporto JSON integrato in SQL Server  
Per soluzioni specifiche, casi d'uso e indicazioni, vedere i [post del blog sul supporto JSON integrato](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e nel database SQL di Azure redatti da Jovan Popovic, Microsoft Program Manager.
  
## <a name="see-also"></a>Vedere anche  
 [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  
