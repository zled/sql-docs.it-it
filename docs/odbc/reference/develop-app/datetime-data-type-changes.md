---
title: Modifica tipo di dati DateTime | Documenti Microsoft
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
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a2033cd5931278c9a05c62d907d7da73473902e8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="datetime-data-type-changes"></a>Modifiche ai tipi di dati DateTime
In ODBC 3. *x*, gli identificatori per data, ora e tipi di dati timestamp SQL sono stati modificati da SQL_DATE, SQL_TIME e SQL_TIMESTAMP (con istanze di **#define** nel file di intestazione di 9, 10 e 11) per tipo SQL_TYPE_DATE, SQL_TYPE_TIME e SQL_TYPE_TIMESTAMP (con istanze di **#define** nel file di intestazione di 91 92 e 93), rispettivamente. Gli identificatori di tipo C corrispondenti sono stati modificati da SQL_C_DATE SQL_C_TIME e SQL_C_TIMESTAMP SQL_C_TYPE_DATE, SQL_C_TYPE_TIME e SQL_C_TYPE_TIMESTAMP, rispettivamente.  
  
 Le dimensioni e cifre decimali restituiti per i tipi di dati datetime SQL in ODBC 3. *x* sono e la precisione e scala restituito relativa in ODBC 2. *x*. Questi valori sono diversi dai valori in campi di descrizione SQL_DESC_PRECISION e SQL_DESC_SCALE. (Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).)  
  
 Queste modifiche influiscono sui **SQLDescribeCol**, **SQLDescribeParam**, e **SQLColAttribute**; **SQLBindCol**, **SQLBindParameter**, e **SQLGetData**; e **SQLColumns**, **SQLGetTypeInfo** , **SQLProcedureColumns**, **SQLStatistics**, e **SQLSpecialColumns**.  
  
 La tabella seguente mostra come ODBC 3*x* Driver Manager esegue i mapping dei tipi di dati C date, time e timestamp immesso nel *TargetType* gli argomenti di **SQLBindCol**e **SQLGetData** oppure il *ValueType* argomento di **SQLBindParameter**.  
  
|Tipo di dati<br /><br /> codice inserito|2.*x* dell'app<br /><br /> 2.*x* driver|2.*x* dell'app<br /><br /> 3.*x* driver|3.*x* dell'app<br /><br /> 2.*x* driver|3.*x* dell'app<br /><br /> 3.*x* driver|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|Nessun mapping|SQL_C_TYPE_DATE (91)|Nessun mapping [1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|Errore (DM)|Errore (DM)|SQL_C_DATE (9)|Nessun mapping [2]|  
|SQL_C_TIME (10)|Nessun mapping|SQL_C_TYPE_TIME (92)|Nessun mapping [1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|Errore (DM)|Errore (DM)|SQL_C_TIME (10)|Nessun mapping [2]|  
|SQL_C_TIMESTAMP (11)|Nessun mapping|SQL_C_TYPE_TIMESTAMP (93)|Nessun mapping [1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|Errore (DM)|Errore (DM)|SQL_C_TIMESTAMP (11)|Nessun mapping [2]|  
  
 [1] in seguito a questa, un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2. *x* driver può utilizzare i codici di data, ora o timestamp restituiti nei set di risultati restituiti dalle funzioni di catalogo.  
  
 [2] in seguito a questa, un'applicazione ODBC 3. *x* applicazione che utilizza un'applicazione ODBC 3. *x* driver può utilizzare i codici di data, ora o timestamp restituiti nei set di risultati restituiti dalle funzioni di catalogo.  
  
 La tabella seguente mostra come ODBC 3*x* Driver Manager esegue i mapping dei tipi di dati SQL date, time e timestamp immesso nel *ParameterType* argomento di **SQLBindParameter**  oppure il *DataType* argomento di **SQLGetTypeInfo**.  
  
|Tipo di dati<br /><br /> codice inserito|2.*x* dell'app<br /><br /> 2.*x* driver|2.*x* dell'app<br /><br /> 3.*x* driver|3.*x* dell'app<br /><br /> 2.*x* driver|3.*x* dell'app<br /><br /> 3.*x* driver|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|Nessun mapping|SQL_TYPE_DATE (91)|Nessun mapping [1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|Errore (DM)|Errore (DM)|SQL_DATE (9)|Nessun mapping [2]|  
|SQL_TIME (10)|Nessun mapping|SQL_TYPE_TIME (92)|Nessun mapping [1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|Errore (DM)|Errore (DM)|SQL_TIME (10)|Nessun mapping [2]|  
|SQL_TIMESTAMP (11)|Nessun mapping|SQL_TYPE_TIMESTAMP (93)|Nessun mapping [1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|Errore (DM)|Errore (DM)|SQL_TIMESTAMP (11)|Nessun mapping [2]|  
  
 [1] in seguito a questa, un'applicazione ODBC 3. *x* applicazione che utilizza un ODBC 2. *x* driver può utilizzare i codici di data, ora o timestamp restituiti nei set di risultati restituiti dalle funzioni di catalogo.  
  
 [2] in seguito a questa, un'applicazione ODBC 3. *x* applicazione che utilizza un'applicazione ODBC 3. *x* driver può utilizzare i codici di data, ora o timestamp restituiti nei set di risultati restituiti dalle funzioni di catalogo.
