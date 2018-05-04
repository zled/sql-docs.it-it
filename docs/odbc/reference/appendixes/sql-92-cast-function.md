---
title: Funzione CAST SQL-92 | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce0ff593f8f381efb6d54ea73a8dea04f99823ce
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
