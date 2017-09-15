---
title: "Descrittore campo conformità | Documenti Microsoft"
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
- descriptor field conformance levels [ODBC]
- conformance levels [ODBC], descriptor field
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 6c29d93b-696c-4960-bff3-4d6bc41bc513
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 049208450144fdd1c1d3b902093517627486ccf9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="descriptor-field-conformance"></a>Descrittore campo conformità
Nella tabella seguente indica il livello di conformità di ogni campo di intestazione ODBC descrittore, in cui questo è ben definito.  
  
|Funzione|Livello di conformità|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Core|  
|SQL_DESC_ARRAY_SIZE|Core|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (per APD IPR e IRD); Livello 1 (per ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|Core|  
|SQL_DESC_BIND_TYPE|Core|  
|SQL_DESC_COUNT|Core|  
|SQL_DESC_ROWS_PROCESSED_PTR|Core|  
  
 Nella tabella seguente indica il livello di conformità di ogni campo di record del descrittore ODBC, in cui questo è ben definito.  
  
|Funzione|Livello di conformità|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Livello 2|  
|SQL_DESC_BASE_COLUMN_NAME|Core|  
|SQL_DESC_BASE_TABLE_NAME|Livello 1|  
|SQL_DESC_CASE_SENSITIVE|Core|  
|SQL_DESC_CATALOG_NAME|Livello 2|  
|SQL_DESC_CONCISE_TYPE|Core|  
|SQL_DESC_DATA_PTR|Core|  
|CODICE SQL_DESC_DATETIME_INTERVAL_|Componenti di base [1]|  
|PRECISIONE SQL_DESC_DATETIME_INTERVAL_|Componenti di base [1]|  
|SQL_DESC_DISPLAY_SIZE|Core|  
|SQL_DESC_FIXED_PREC_SCALE|Core|  
|SQL_DESC_INDICATOR_PTR|Core|  
|SQL_DESC_LABEL|Livello 2|  
|SQL_DESC_LENGTH|Core|  
|SQL_DESC_LITERAL_PREFIX|Core|  
|SQL_DESC_LITERAL_SUFFIX|Core|  
|SQL_DESC_LOCAL_TYPE_NAME|Core|  
|SQL_DESC_NAME|Core|  
|SQL_DESC_NULLABLE|Core|  
|SQL_DESC_OCTET_LENGTH|Core|  
|SQL_DESC_OCTET_LENGTH_PTR|Core|  
|SQL_DESC_PARAMETER_TYPE|Componenti di base o del livello 2 di [2]|  
|SQL_DESC_PRECISION|Core|  
|SQL_DESC_ROWVER|Livello 1|  
|SQL_DESC_SCALE|Core|  
|SQL_DESC_SCHEMA_NAME|Livello 1|  
|SQL_DESC_SEARCHABLE|Core|  
|SQL_DESC_TABLE_NAME|Livello 1|  
|SQL_DESC_TYPE|Core|  
|SQL_DESC_TYPE_NAME|Core|  
|SQL_DESC_UNNAMED|Core|  
|SQL_DESC_UNSIGNED|Core|  
|SQL_DESC_UPDATABLE|Core|  
  
 [1] supporto per questi campi di record è obbligatorio solo se il driver supporta i tipi di dati applicabili.  
  
 [2] per la conformità a livello di base, il driver deve supportare SQL_PARAM_INPUT. La conformità di interfaccia di livello 2, il driver deve supportare anche SQL_PARAM_INPUT_OUTPUT e SQL_PARAM_OUTPUT.
