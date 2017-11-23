---
title: Tipi di dati dBASE | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], data types
- data types [ODBC], DBase driver
- dbase data types [ODBC]
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b0e2405001dbffc6421cb2f1ed6c7b44a138abca
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="dbase-data-types"></a>file dBASE tipi di dati
Nella tabella seguente viene illustrato come tipi di dati dBASE vengono eseguito il mapping ai tipi di dati SQL ODBC. Si noti che non tutti i tipi di dati SQL ODBC sono supportati.  
  
|tipo di dati di file dBASE|Tipo di dati ODBC|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|FLOAT [1]|SQL_DOUBLE|  
|LOGICA|SQL_BIT|  
|MEMO|SQL_LONGVARCHAR|  
|NUMERICO (BCD)|SQL_DOUBLE|  
|OLEOBJECT [1]|SQL_LONGBINARY|  
  
 [1] valido solo per file dBASE versione 5. *x*  
  
 Precisione in file dBASE III ammette numeri con backup per gli esponenti a due cifre e numeri dBASE IV con fino a tre cifre esponenti. Poiché i numeri vengono archiviati come testo, vengono convertiti in numeri. Se il numero da convertire non rientra in un campo, si potrebbero verificare risultati sconosciuti.  
  
 DBASE consente una precisione e scala per essere specificato con un tipo di dati numerici, ma non è supportato dal driver ODBC dBASE. Il driver ODBC dBASE restituisce sempre una precisione di 15 e una scala pari a 0 per un tipo di dati numerici.  
  
 Una colonna creata con il tipo di dati numerici utilizzando le mappe di driver ODBC dBASE al tipo di dati ODBC SQL_DOUBLE. In questo modo i dati in questa colonna sono soggetti a arrotondamento. Questo comportamento non è lo stesso come che i dati numerici di tipo nel file dBASE (tipo N), che è Binary Coded Decimal (BCD).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** restituisce i tipi di dati SQL ODBC. Tutte le conversioni nell'appendice D il *riferimento per programmatori ODBC* sono supportati per i tipi di dati SQL ODBC elencati in precedenza in questo argomento.  
  
 La tabella seguente illustra le limitazioni in file dBASE tipi di dati.  
  
|Tipo di dati|Description|  
|---------------|-----------------|  
|CHAR|Creazione di una colonna CHAR pari a zero o lunghezza non specificata restituisce una colonna 254 byte.|  
|Dati crittografati|Il driver dBASE non supporta le tabelle dBASE crittografati.|  
|LOGICA|Il driver dBASE non è possibile creare un indice su una colonna LOGICA.|  
|MEMO|La lunghezza massima di una colonna di dati MEMO è 65.500 byte.|  
  
 Altre limitazioni sui tipi di dati sono reperibili [limitazioni del tipo di dati](../../odbc/microsoft/data-type-limitations.md).
