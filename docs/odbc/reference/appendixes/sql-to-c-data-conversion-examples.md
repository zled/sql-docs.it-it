---
title: SQL agli esempi di conversione di dati C | Documenti Microsoft
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
- data conversions from SQL to C types [ODBC], examples
- converting data from SQL to C types [ODBC], examples
ms.assetid: 0190c76c-7f9b-42f4-be9d-cef7284840fd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7dd7b514ce4788a035e6f230f3d0a87a94440f2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sql-to-c-data-conversion-examples"></a>SQL agli esempi di conversione di dati C
Gli esempi illustrati nella tabella seguente viene illustrato come il driver converte i dati SQL ai dati C:  
  
|Tipo SQL<br /><br /> identificatore|SQL data<br /><br /> Valore|Tipo C<br /><br /> identificatore|Buffer<br /><br /> length|**TargetValuePtr*|SQLSTATE|  
|-----------------------------|------------------------|---------------------------|-----------------------|------------------------|--------------|  
|SQL_CHAR|abcdef|SQL_C_CHAR|7|abcdef\0 [a]|n/d|  
|SQL_CHAR|abcdef|SQL_C_CHAR|6|abcde\0 [a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|8|1234.56\0 [a]|n/d|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|5|1234\0 [a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|4|----|22003|  
|SQL_DECIMAL|1234.56|SQL_C_FLOAT|Ignorato|1234.56|n/d|  
|SQL_DECIMAL|1234.56|SQL_C_SSHORT|Ignorato|1234|01S07|  
|SQL_DECIMAL|1234.56|SQL_C_STINYINT|Ignorato|----|22003|  
SQL_DOUBLE|1.2345678|SQL_C_DOUBLE|Ignorato|1.2345678|n/d|  
|SQL_DOUBLE|1.2345678|SQL_C_FLOAT|Ignorato|1.234567|n/d|  
|SQL_DOUBLE|1.2345678|SQL_C_STINYINT|Ignorato|1|n/d|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|11|1992-12-31\0 [a]|n/d|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|10|-----|22003|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_TIMESTAMP|Ignorato|1992,12,31, 0,0,0,0 [b]|n/d|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|23|1992-12-31 23:45:55.12\0 [a]|n/d|  
SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|22|1992-12-31 23:45:55.1\0 [a]|01004|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|18|----|22003|  
  
 [a] "\0" rappresenta un byte di terminazione null. Il driver sempre null termina i dati SQL_C_CHAR.  
  
 [b] i numeri in questo elenco sono i numeri memorizzati nei campi della struttura di TIMESTAMP_STRUCT.
