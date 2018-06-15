---
title: Diagnostica descrittore, informazioni, tipi specifici del driver, dati, | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- driver-specific diagnostic values [ODBC]
- diagnostic information [ODBC], driver-specific values
- ODBC drivers [ODBC], driver-specific diagnostic values
ms.assetid: ad4c76d3-5191-4262-b47c-5dd1d19d1154
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e7dbc0ca0584d5dd9c7e8dbfc1cfa5d23831d764
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912316"
---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Tipi di dati specifici del driver, i tipi di descrittore, tipi di informazioni, i tipi di diagnostica e attributi
I driver possono allocare valori specifici del driver per le operazioni seguenti:  
  
-   **Indicatori di tipo di dati SQL** sono usati nella *ParameterType* in **SQLBindParameter** e in *DataType* in **SQLGetTypeInfo** e restituito da **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLGetTypeInfo**,  **SQLDescribeParam**, **SQLProcedureColumns**, e **SQLSpecialColumns**.  
  
-   **I campi di descrizione** sono usati nella *FieldIdentifier* in **SQLColAttribute**, **SQLGetDescField**, e **SQLSetDescField**.  
  
-   **I campi di diagnostica** sono usati nella *DiagIdentifier* in **SQLGetDiagField** e **SQLGetDiagRec**.  
  
-   **Tipi di informazioni** sono usati nella *InfoType* in **SQLGetInfo**.  
  
-   **Connessione e gli attributi di istruzione** sono usati nella *attributo* in **SQLGetConnectAttr**, **SQLGetStmtAttr**,  **La funzione SQLSetConnectAttr**, e **SQLSetStmtAttr**.  
  
 Per ognuno di questi elementi, sono disponibili due set di valori: valori riservati per ODBC e valori riservati per i driver. Prima di implementare i valori specifici del driver, un writer di driver deve richiedere un valore per ogni tipo specifico del driver, un campo o attributo da Open Group. Per i nuovi sviluppi driver, utilizzare l'intervallo descritto nella tabella seguente. Gestione ODBC 3.8 Driver non genererà un errore se viene utilizzato un valore sconosciuto che non è compreso nell'intervallo descritto di seguito. Tuttavia, le versioni successive di gestione Driver potrebbero generare un errore se i valori sconosciuti ricevuti che non rientrano nell'intervallo.  
  
 Quando uno di questi valori viene passato a una funzione ODBC, il driver deve controllare se il valore è valido. Driver restituiscono HYC00 SQLSTATE (funzionalità facoltativa non implementata) per i valori specifici del driver che si applicano a altri driver.  
  
 A partire da ODBC 3.8, gli sviluppatori di driver possono allocare gli attributi specifici del driver all'interno di un intervallo riservato.  
  
> [!NOTE]  
>  La gestione driver ODBC 3.8 per convalida né applica questi intervalli per la compatibilità con le versioni precedenti. Una versione futura di gestione Driver potrebbe imporre, tuttavia.  
  
|Tipo di attributo|Tipo di dati ODBC|Intervallo di base specifici del driver|Limite dell'intervallo specifici del driver|Costante ODBC per l'intervallo di valori specifici del driver base|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|Gli indicatori di tipo di dati SQL|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|Campi di descrizione|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|Campi di diagnostica|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|Tipi di informazioni|SQLUSMALLINT|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|Attributi di connessione|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|Attributi di istruzione|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  Tipi di dati specifici del driver, i campi di descrizione, i campi di diagnostica, i tipi di informazioni, gli attributi di istruzione e gli attributi di connessione devono essere descritte nella documentazione del driver. Quando uno di questi valori viene passato a una funzione ODBC, il driver deve controllare se il valore è valido. Driver restituiscono HYC00 SQLSTATE (funzionalità facoltativa non implementata) per i valori specifici del driver che si applicano a altri driver.  
  
 I valori di base vengono definiti per facilitare lo sviluppo di driver. Attributi di diagnostica specifici del driver, ad esempio, possono essere definiti nel formato seguente:  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
