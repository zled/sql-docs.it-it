---
title: Funzione CAST SQL-92 | Documenti Microsoft
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
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8389ff0812c91ca5a35007a21d70a2a1ca0baee8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sql-92-cast-function"></a>Funzione CAST SQL-92
Il **CAST** è equivalente alla funzione definita in SQL-92 il **CONVERTIRE** funzione definita in ODBC. La sintassi delle funzioni equivalente è il seguente:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 SQL-92 **CAST** funzione impone i tipi di dati possono essere convertiti in cui altri tipi di dati. (Per ulteriori informazioni, vedere la specifica di SQL-92). Il **CAST** funzione è supportata a livello di transizione FIPS.  
  
 Un'applicazione può determinare il supporto per il **CAST** funzione come segue:  
  
1.  Chiamare **SQLGetInfo** con il tipo di informazioni SQL_SQL_CONFORMANCE. Se il valore restituito per il tipo di informazioni è SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE o SQL_SC_SQL92_FULL, il **CAST** funzione è supportata.  
  
2.  Se il valore restituito del tipo di informazioni SQL_SQL_CONFORMANCE SQL_SC_ENTRY_LEVEL o 0, chiamare **SQLGetInfo** con il tipo di informazioni SQL_SQL92_VALUE_EXPRESSIONS. Se il bit SQL_SVE_CAST è impostato, il **CAST** funzione è supportata.
