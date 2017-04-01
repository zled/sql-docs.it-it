---
title: "Modalit&#224; di uso di FOR JSON delle sequenze di escape per i caratteri speciali e di controllo (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON, caratteri speciali"
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Modalit&#224; di uso di FOR JSON delle sequenze di escape per i caratteri speciali e di controllo (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Questo argomento descrive il modo in cui la clausola **FOR JSON** usa sequenze di escape per i caratteri speciali e rappresenta i caratteri di controllo nell'output JSON.  
  
## Escape di caratteri speciali  
 La clausola **FOR JSON** usa sequenze di escape per i caratteri speciali nell'output JSON con `\`, come illustrato nella tabella seguente. I caratteri di escape vengono usati sia nei nomi delle proprietà che nei relativi valori.  
  
|**Carattere speciale**|**Sequenza codificata**|  
|---------------------------|--------------------------|  
|Virgoletta (")|\\"|  
|Barra rovesciata (\\)|\\\|  
|Barra (/)|\\/|  
|Backspace|\b|  
|Avanzamento carta|\f|  
|Nuova riga|\n|  
|Ritorno a capo|\r|  
|Tabulazione orizzontale|\t|  
  
## Caratteri di controllo  
 La clausola **FOR JSON** rappresenta i caratteri di controllo nell'output JSON nel formato `\u<code>`, come illustrato nella tabella seguente.  
  
|**Carattere di controllo**|**Sequenza codificata**|  
|---------------------------|--------------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|…|…|  
|CHAR(31)|\u001f|  
  
## Esempio  
 Di seguito è riportato un esempio di una clausola **FOR JSON** che include caratteri di escape e di controllo.  
  
 Query:  
  
```tsql  
SELECT  
  'VALUE\    /  
  "' as [KEY\/"],  
  CHAR(0) as '0',  
  CHAR(1) as '1',  
  CHAR(31) as '31'  
FOR JSON PATH  
```  
  
 Risultato:  
  
```json  
{  
   "KEY\\\t\/\"":"VALUE\\\t\/\r\n\"",  
   "0":"\u0000",  
   "1":"\u0001",  
  "31":"\u001f“  
}  
```  
  
## Vedere anche  
 [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  