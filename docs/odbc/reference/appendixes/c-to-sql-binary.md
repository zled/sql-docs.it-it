---
title: 'C a SQL: binario | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binary data type [ODBC]
- data conversions from C to SQL types [ODBC], binary
- binary data transfers [ODBC]
- converting data from c to SQL types [ODBC], binary
ms.assetid: 3e9083f3-357b-41aa-833c-2c8aac2226cd
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e85e57206c6bf963e3b97039224d37f512961f86
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-binary"></a>C a SQL: binario
L'identificatore per il tipo di dati C ODBC binario è:  
  
 SQL_C_BINARY  
  
 Nella tabella seguente viene illustrato SQL ODBC dei tipi di dati a cui possono essere convertiti i dati binari di C. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Lunghezza in byte dei dati < = lunghezza di colonna in byte<br /><br /> Lunghezza in byte dei dati > lunghezza di colonna in byte|n/d<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Lunghezza dei dati di carattere < = lunghezza in caratteri colonna<br /><br /> Lunghezza dei dati in caratteri > lunghezza in caratteri colonna|n/d<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> TIPO SQL_TYPE_DATE SQL_BIT<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|Lunghezza in byte di dati = lunghezza dei dati SQL<br /><br /> Lunghezza in byte di lunghezza dei dati SQL <> dati|n/d<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|Lunghezza dei dati < = lunghezza della colonna<br /><br /> Lunghezza dei dati > lunghezza della colonna|n/d<br /><br /> 22001|
