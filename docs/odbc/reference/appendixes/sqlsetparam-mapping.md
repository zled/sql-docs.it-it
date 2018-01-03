---
title: Mapping SQLSetParam | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: adebe26728690a6d631ca94e8ce11040ebc08a0f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
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
