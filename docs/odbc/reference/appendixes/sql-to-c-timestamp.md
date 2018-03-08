---
title: 'SQL a c: Timestamp | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timestamp data type [ODBC]
- converting data from SQL to C types [ODBC], timestamp
- data conversions from SQL to C types [ODBC], timestamp
ms.assetid: 6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d877c369a071dfc9c28f2500dc6584fe99808cfa
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sql-to-c-timestamp"></a>SQL a c: Timestamp
L'identificatore del tipo di dati SQL ODBC timestamp è:  
  
 SQL_TYPE_TIMESTAMP  
  
 Nella tabella seguente viene illustrato come ODBC C i tipi di dati a cui è possono convertire dati di tipo timestamp SQL. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > lunghezza in byte di caratteri<br /><br /> 20 < = *BufferLength* < = lunghezza in byte di caratteri<br /><br /> *BufferLength* < 20|data<br /><br /> Dati troncati [b]<br /><br /> Non definito|Lunghezza in byte dei dati<br /><br /> Lunghezza in byte dei dati<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > lunghezza in caratteri<br /><br /> 20 < = *BufferLength* < = lunghezza in caratteri<br /><br /> *BufferLength* < 20|data<br /><br /> Dati troncati [b]<br /><br /> Non definito|Lunghezza dei dati in caratteri<br /><br /> Lunghezza dei dati in caratteri<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Lunghezza in byte dei dati < = *BufferLength*<br /><br /> Lunghezza in byte dei dati > *BufferLength*|data<br /><br /> Non definito|Lunghezza in byte dei dati<br /><br /> Non definito|n/d<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Parte relativa all'ora del timestamp è uguale a zero [a]<br /><br /> Parte relativa all'ora del timestamp è diverso da zero [a]|data<br /><br /> Dati troncati [c]|6 [f]<br /><br /> 6 [f]|n/d<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|Parte relativa ai secondi frazionari di timestamp è uguale a zero [a]<br /><br /> Parte relativa ai secondi frazionari di timestamp è diverso da zero [a]|Dati [d]<br /><br /> Dati troncati [d], [e]|6 [f]<br /><br /> 6 [f]|n/d<br /><br /> 01S07|  
_C_TYPE_TIMESTAMP|Parte relativa ai secondi frazionari di timestamp non è stato troncato [a]<br /><br /> Parte relativa ai secondi frazionari di timestamp viene troncato [a]|Dati [e]<br /><br /> Dati troncati [e]|16 [f]<br /><br /> 16 [f]|n/d<br /><br /> 01S07|  
  
 [a] il valore di *BufferLength* viene ignorata per la conversione. Il driver presuppone che le dimensioni di **TargetValuePtr* è la dimensione del tipo di dati C.  
  
 [b] i secondi frazionari del timestamp vengono troncati.  
  
 [c] la porzione dell'ora del timestamp viene troncata.  
  
 [d] la parte relativa alla data del timestamp viene ignorata.  
  
 [e] la parte frazionaria dei secondi del timestamp viene troncata.  
  
 [f] è la dimensione del tipo di dati C corrispondente.  
  
 Quando i dati SQL timestamp vengono convertiti in dati di tipo carattere C, la stringa risultante è il "*aaaa*-*mm*-*gg* *hh* :*mm*:*ss*[. *f...* ] "formato, in cui può essere utilizzato fino a nove cifre per i secondi frazionari. Questo formato non è interessato dalla configurazione dell'impostazione di paese Windows®. (Tranne il separatore decimale e i secondi frazionari, il formato intero da utilizzare, indipendentemente dalla precisione del tipo di dati timestamp SQL.)
