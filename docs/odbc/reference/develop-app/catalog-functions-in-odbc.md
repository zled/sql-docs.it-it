---
title: Catalogo delle funzioni di ODBC | Documenti Microsoft
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
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74b86dfd62a12938d18b4aa11a8d0502db50da13
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-functions-in-odbc"></a>Funzioni di catalogo ODBC
ODBC contiene le funzioni di catalogo seguenti:  
  
|Funzione|Description|  
|--------------|-----------------|  
|**SQLTables**|Restituisce un elenco dei cataloghi, schemi, tabelle o i tipi di tabella nell'origine dati.|  
|**SQLColumns**|Restituisce un elenco di colonne in una o più tabelle.|  
|**SQLStatistics**|Restituisce un elenco delle statistiche su una singola tabella. Restituisce inoltre un elenco di indici associate alla tabella.|  
|**SQLSpecialColumns**|Restituisce un elenco di colonne che identifica in modo univoco una riga in una singola tabella. Restituisce inoltre un elenco di colonne della tabella che vengono aggiornate automaticamente.|  
|**SQLPrimaryKeys**|Restituisce un elenco di colonne che compongono la chiave primaria di una singola tabella.|  
|**SQLForeignKeys**|Restituisce un elenco di chiavi esterne in una singola tabella o un elenco di chiavi esterne in altre tabelle che fanno riferimento a una singola tabella.|  
|**SQLTablePrivileges**|Restituisce un elenco di privilegi associati a una o più tabelle.|  
|**SQLColumnPrivileges**|Restituisce un elenco di privilegi associati a una o più colonne in un'unica tabella.|  
|**SQLProcedures**|Restituisce un elenco di procedure nell'origine dati.|  
|**SQLProcedureColumns**|Restituisce un elenco di parametri di input e outpui, il valore restituito e le colonne nel set di risultati di una sola stored procedure.|  
|**SQLGetTypeInfo**|Restituisce un elenco di tipi di dati SQL supportati dall'origine dati. Questi tipi di dati vengono in genere utilizzati **CREATE TABLE** e **ALTER TABLE** istruzioni.|  
  
 Poiché **SQLTables**, **SQLColumns**, **SQLStatistics**, e **SQLSpecialColumns** conformi alla Apri gruppo CLI e **SQLGetTypeInfo** è conforme a ISO 92 CLI, vengono implementati dalla maggior parte dei driver. Le funzioni di catalogo rimanenti sono nel livello di conformità di ODBC.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Dati restituiti dalle funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Argomenti nelle funzioni di catalogo](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Viste degli schemi](../../../odbc/reference/develop-app/schema-views.md)

