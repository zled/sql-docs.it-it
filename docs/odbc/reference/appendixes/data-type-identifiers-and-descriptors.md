---
title: Identificatori e descrittori del tipo di dati | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
- descriptors [ODBC], data types
- verbose data types [ODBC]
- data types [ODBC], descriptors
- concise data types [ODBC]
ms.assetid: f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6594c2b47ed5f57f6814ac704b9d36073e0a8304
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792999"
---
# <a name="data-type-identifiers-and-descriptors"></a>Identificatori e descrittori del tipo di dati
I tipi di dati elencati nella [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) e [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) sezioni più indietro in questa appendice sono tipi di dati "conciso": ogni identificatore fa riferimento a un singolo tipo di dati. È disponibile una corrispondenza uno a uno tra l'identificatore e il tipo di dati. I descrittori, farlo, tuttavia, non in tutti i casi usano un singolo valore per identificare i tipi di dati. In alcuni casi, usano un tipo di dati "verbose" e un codice secondario di tipo. Per tutti i tipi di dati tranne i tipi di dati Data/ora e intervallo, l'identificatore di tipo dettagliato è quello utilizzato per l'identificatore del tipo conciso e il valore in SQL_DESC_DATETIME_INTERVAL_CODE è uguale a 0. Per tipi di dati Data/ora e intervallo, tuttavia, un tipo verbose (SQL_DATETIME o SQL_INTERVAL) è archiviato in SQL_DESC_TYPE in SQL_DESC_CONCISE_TYPE viene archiviato un tipo conciso e un codice secondario per ogni tipo conciso viene archiviato in SQL_DESC_DATETIME_INTERVAL_CODE. L'impostazione di uno di questi campi influenza gli altri. Per altre informazioni su questi campi, vedere la [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) descrizione della funzione.  
  
 Quando il campo SQL_DESC_TYPE o SQL_DESC_CONCISE_TYPE è impostato per alcuni tipi di dati, i campi SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION e SQL_DESC_SCALE vengono automaticamente impostati sui valori predefiniti, come applicabile per i dati tipo. Per altre informazioni, vedere la descrizione del campo SQL_DESC_TYPE [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Se il set di valori predefinito non è appropriato, l'applicazione deve impostare in modo esplicito il campo di descrizione tramite una chiamata a **SQLSetDescField**.  
  
 La tabella seguente illustra l'identificatore di tipo conciso, identificatore di tipo dettagliato e codice secondario di tipo per ogni data/ora e intervallo SQL e l'identificatore di tipo C. Come indicato in questa tabella, per i tipi di dati Data/ora e intervallo, i campi SQL_DESC_TYPE e SQL_DESC_DATETIME_INTERVAL_CODE hanno le costanti manifeste stesso sia per i tipi di dati SQL (nei descrittori di implementazione) per tipi di dati C (nell'applicazione descrittori).  
  
|Tipo conciso di SQL|Tipo conciso di C|Tipo dettagliato|DATETIME_INTERVAL_CODE|  
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
