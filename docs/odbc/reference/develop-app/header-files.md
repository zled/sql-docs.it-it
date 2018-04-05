---
title: File di intestazione | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- header files [ODBC]
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 197c7ef28124fb1b1c52facbec541913330c69c5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="header-files"></a>File di intestazione
Il file di intestazione SQL contiene prototipi per le funzioni e funzionalità del livello di conformità interfaccia ODBC Core. Il file di intestazione Sqlext. h contiene prototipi per le funzioni e le funzionalità del livello 1 e i livelli di conformità di API di livello 2. Il file di intestazione Sqlext contiene le definizioni di tipo e gli indicatori per i tipi di dati SQL.  
  
 I file di intestazione contengono tutti un **#define**, ODBCVER, che un'applicazione o il driver è possibile impostare per essere compilato per versioni diverse di ODBC.  
  
 Per allineare e ISO CLI aprire CLI di gruppo, i file di intestazione contengono alias per i tipi di informazioni utilizzato nelle chiamate a **SQLGetInfo**. Nella tabella seguente, la colonna "Nome ODBC" indica il nome ODBC per il tipo di informazioni in [riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md). La colonna "Alias nel file di intestazione" indica il nome che viene utilizzato la CLI ISO e CLI gruppo aperto. Il valore numerico effettivo di questi nomi manifesti è lo stesso sia in ODBC che le interfacce standard. Questi alias abilitare un'applicazione conforme agli standard o un driver per la compilazione con ODBC 3*x* file di intestazione.  
  
 Questi alias includono le espansioni di abbreviazioni nei nomi di ODBC in modo che i nomi sono più intuitive. Espanso "MAX" a "Massimo", "Lunghezza" "Lunghezza", "MULT" "Più", "GU" a "OUTER_JOIN" e "TXN" a "Transazione".  
  
|Nome ODBC|Alias nel file di intestazione|  
|---------------|--------------------------|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAXIMUM_CATALOG_NAME_LENGTH|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAXIMUM_COLUMN_NAME_LENGTH|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAXIMUM_COLUMNS_IN_GROUP_BY|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAXIMUM_COLUMNS_IN_ORDER_BY|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAXIMUM_COLUMNS_IN_SELECT|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAXIMUM_COLUMNS_IN_TABLE|  
|SQL_MAX_CONCURRENT_ACTIVITIES|SQL_MAXIMUM_CONCURRENT_ACTIVITIES|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAXIMUM_CURSOR_NAME_LENGTH|  
|SQL_MAX_DRIVER_CONNECTIONS|SQL_MAXIMUM_DRIVER_CONNECTIONS|  
|SQL_MAX_IDENTIFIER_LEN|SQL_MAXIMUM_IDENTIFIER_LENGTH|  
|SQL_MAX_SCHEMA_NAME_LEN|SQL_MAXIMUM_SCHEMA_NAME_LENGTH|  
|SQL_MAX_STATEMENT_LEN|SQL_MAXIMUM_STATEMENT_LENGTH|  
|SQL_MAX_TABLE_NAME_LEN|SQL_MAXIMUM_TABLE_NAME_LENGTH|  
|SQL_MAX_TABLES_IN_SELECT|SQL_MAXIMUM_TABLES_IN_SELECT|  
|SQL_MAX_USER_NAME_LEN|SQL_MAXIMUM_USER_NAME_LENGTH|  
|SQL_MULT_RESULT_SETS|SQL_MULTIPLE_RESULT_SETS|  
|SQL_OJ_CAPABILITIES|SQL_OUTER_JOIN_CAPABILITIES|  
|SQL_TXN_CAPABLE|SQL_TRANSACTION_CAPABLE|  
|SQL_TXN_ISOLATION_OPTION|SQL_TRANSACTION_ISOLATION_OPTION|
