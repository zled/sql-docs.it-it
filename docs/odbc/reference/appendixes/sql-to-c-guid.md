---
title: 'SQL per c: GUID | Documenti Microsoft'
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
ms.topic: article
helpviewer_keywords:
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a0e4d11048f532f91cc4fc06f85f6c1e355d1d4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sql-to-c-guid"></a>SQL per c: GUID
L'identificatore per il tipo di dati SQL ODBC GUID è:  
  
 SQL_GUID  
  
 Nella tabella seguente viene illustrato come ODBC C i tipi di dati a cui possono essere convertiti i dati di SQL GUID. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > lunghezza in byte di caratteri|data|36|n/d|  
||*BufferLength* < 37|Non definito|Non definito|22003|  
|SQL_C_WCHAR|*BufferLength* > lunghezza in caratteri|data|36|n/d|  
||*BufferLength* < 37|Non definito|Non definito|22003|  
|SQL_C_BINARY|Lunghezza in byte dei dati \< =  *BufferLength*|data|Lunghezza in byte dei dati|n/d|  
||Lunghezza in byte dei dati > *BufferLength*|Non definito|Non definito|22003|  
|SQL_C_GUID|Nessuno, [a]|data|16 [b]|n/d|  
  
 [a] il valore di *BufferLength* viene ignorata per la conversione. Il driver presuppone che le dimensioni di **TargetValuePtr* è la dimensione del tipo di dati C.  
  
 [b] è la dimensione del tipo di dati C corrispondente.
