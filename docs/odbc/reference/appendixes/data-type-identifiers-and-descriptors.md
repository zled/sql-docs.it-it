---
title: Gli identificatori e descrittori del tipo di dati | Documenti Microsoft
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
- data types [ODBC], identifiers
- identifiers [ODBC], data types
- descriptors [ODBC], data types
- verbose data types [ODBC]
- data types [ODBC], descriptors
- concise data types [ODBC]
ms.assetid: f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9d36c0308ae7afb12541a0f33f4d2b417dfb15e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="data-type-identifiers-and-descriptors"></a>Gli identificatori di tipo di dati e i descrittori
I tipi di dati elencati nella [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) e [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) sezioni in questa appendice sono tipi di dati "concise": ogni identificatore fa riferimento a un singolo tipo di dati. È una corrispondenza tra l'identificatore e il tipo di dati. Descrittori, tuttavia, eseguire non in tutti i casi usare un singolo valore per identificare i tipi di dati. In alcuni casi, vengono utilizzati un tipo di dati "verbose" e un codice secondario di tipo. Per tutti i tipi di dati tranne i tipi di dati datetime e interval, l'identificatore di tipo dettagliato è lo stesso come l'identificatore del tipo conciso e il valore in SQL_DESC_DATETIME_INTERVAL_CODE è uguale a 0. Per i tipi di dati datetime e interval, tuttavia, un tipo verbose (SQL_DATETIME o SQL_INTERVAL) è archiviato in SQL_DESC_TYPE, un tipo conciso è archiviato in SQL_DESC_CONCISE_TYPE e un codice secondario per ogni tipo conciso viene archiviato in SQL_DESC_DATETIME_INTERVAL_CODE. L'impostazione di uno di questi campi interessa gli altri. Per ulteriori informazioni su questi campi, vedere il [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) descrizione della funzione.  
  
 Quando il campo SQL_DESC_TYPE o SQL_DESC_CONCISE_TYPE è impostato per alcuni tipi di dati, i campi SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION e SQL_DESC_SCALE vengono impostati automaticamente sui valori predefiniti, come applicabile per i dati tipo. Per ulteriori informazioni, vedere la descrizione del campo SQL_DESC_TYPE [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Se non è uno dei set di valori predefiniti appropriati, l'applicazione deve impostare in modo esplicito il campo di descrizione tramite una chiamata a **SQLSetDescField**.  
  
 Nella tabella seguente mostra l'identificatore di tipo conciso, identificatore di tipo dettagliato e codice secondario di tipo per ogni datetime e interval SQL e l'identificatore di tipo C. Come indicato nella tabella, per i tipi di dati datetime e interval, i campi SQL_DESC_TYPE e SQL_DESC_DATETIME_INTERVAL_CODE sono le costanti manifesto stesso sia per i tipi di dati SQL (nei descrittori di implementazione) sia per i tipi di dati C (nell'applicazione descrittori).  
  
|Tipo SQL conciso|Tipo C conciso|Tipo dettagliato|DATETIME_INTERVAL_CODE|  
|----------------------|--------------------|------------------|------------------------------|  
|SQL_TYPE_DATE|SQL_C_TYPE_DATE|SQL_DATETIME|SQL_CODE_DATE|  
|SQL_TYPE_TIME|SQL_C_TYPE_TIME|SQL_DATETIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_DATETIME|SQL_CODE_TIMESTAMP|  
|SQL_INTERVAL_MONTH|SQL_C_INTERVAL_MONTH|SQL_INTERVAL|SQL_CODE_MONTH|  
|SQL_INTERVAL_YEAR|SQL_C_INTERVAL_YEAR|SQL_INTERVAL|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_INTERVAL|SQL_CODE_YEAR_TO_MONTH|  
QL_INTERVAL_DAY|SQL_C_INTERVAL_DAY|SQL_INTERVAL|SQL_CODE_DAY|  
|SQL_INTERVAL_HOUR|SQL_C_INTERVAL_HOUR|SQL_INTERVAL|SQL_CODE_HOUR|  
|SQL_INTERVAL_MINUTE|SQL_C_INTERVAL_MINUTE|SQL_INTERVAL|SQL_CODE_MINUTE|  
|SQL_INTERVAL_SECOND|SQL_C_INTERVAL_SECOND|SQL_INTERVAL|SQL_CODE_SECOND|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_C_INTERVAL_DAY_TO_HOUR|SQL_INTERVAL|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE|SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_INTERVAL|SQL_CODE_DAY_TO_MINUTE|  
QL_INTERVAL_DAY_TO_SECOND|SQL_C_INTERVAL_DAY_TO_SECOND|SQL_INTERVAL|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR_TO_MINUTE|SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_INTERVAL|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND|SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_INTERVAL|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE_TO_SECOND|SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_INTERVAL|SQL_CODE_MINUTE_TO_SECOND|
