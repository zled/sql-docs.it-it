---
title: Mapping SQLSetParam | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd23345c0e403e6f4f16419e539c2b5ae277c9d4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetparam-mapping"></a>Mapping di SQLSetParam
**SQLSetParam** continua a essere eseguito il mapping in cima **SQLBindParameter** come ODBC 2. *x*. Anche se è concettualmente simile a **SQLBindParam**, gestione Driver non esegue il mapping **SQLSetParam** a **SQLBindParam**. Determinati esistente ODBC 2. *x* driver viene utilizzato il valore speciale di *BufferLength* (SQL_SETPARAM_VALUE_MAX) che genera l'errore di gestione Driver quando viene eseguito il mapping **SQLSetParam** in cima  **SQLBindParameter** per determinare quando viene chiamato da un 1. *x* applicazione ODBC.  
  
 Una chiamata a  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 restituirà le operazioni seguenti:  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```

