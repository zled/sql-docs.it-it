---
title: 'SQL a c: Bit | Documenti Microsoft'
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
- converting data from SQL to c types [ODBC], bit
- bit data type [ODBC]
- data conversions from SQL to C types [ODBC], bit
ms.assetid: 0eeaab8b-ad82-4a36-b464-9a1211d5f72c
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6862a94cc31bcbee1b931b18c775f03a9e1e58ef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-to-c-bit"></a>SQL a Bit c:
L'identificatore per il tipo di dati SQL ODBC bit è:  
  
 SQL_BIT  
  
 Nella tabella seguente viene illustrato come ODBC C i tipi di dati a cui possono essere convertiti i dati SQL bit. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*BufferLength* > 1<br /><br /> *BufferLength* < = 1|data<br /><br /> Non definito|1<br /><br /> Non definito|n/d<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Nessuno, [a]|data|Dimensioni del tipo di dati C|n/d|  
|SQL_C_BIT|Nessuno, [a]|data|1 [b]|n/d|  
|SQL_C_BINARY|*BufferLength* > = 1<br /><br /> *BufferLength* < 1|data<br /><br /> Non definito|1<br /><br /> Non definito|n/d<br /><br /> 22003|  
  
 [a] il valore di *BufferLength* viene ignorata per la conversione. Il driver presuppone che le dimensioni di **TargetValuePtr* è la dimensione del tipo di dati C.  
  
 [b] è la dimensione del tipo di dati C corrispondente.  
  
 Quando i dati SQL bit viene convertiti in dati di tipo carattere C, i valori possibili sono "0" e "1".
