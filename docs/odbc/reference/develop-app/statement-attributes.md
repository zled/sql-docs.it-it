---
title: Gli attributi di istruzione | Documenti Microsoft
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
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9c5ccfeb2d7cf3ba4b0db5767ced1eeeee92c960
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="statement-attributes"></a>Attributi di istruzione
Gli attributi di istruzione sono caratteristiche dell'istruzione. Ad esempio, se per l'utilizzo dei segnalibri e quali tipi di cursore da utilizzare con il risultato dell'istruzione set sono gli attributi di istruzione.  
  
 Gli attributi di istruzione sono impostati con **SQLSetStmtAttr** e le relative impostazioni correnti recuperati con **SQLGetStmtAttr**. Non è necessario che un'applicazione impostare eventuali attributi di istruzione. tutti gli attributi di istruzione hanno impostazioni predefinite, alcune delle quali sono specifici del driver.  
  
 Quando un attributo di istruzione può essere impostato a seconda dei casi sull'attributo stesso. Prima dell'esecuzione dell'istruzione, è necessario impostare gli attributi di istruzione SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR e SQL_ATTR_USE_BOOKMARKS. Gli attributi di istruzione SQL_ATTR_ASYNC_ENABLE e SQL_ATTR_NOSCAN possono essere impostati in qualsiasi momento, ma non vengono applicati fino a quando non viene utilizzata nuovamente l'istruzione. Impostare gli attributi di istruzione SQL_ATTR_MAX_LENGTH e SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT in qualsiasi momento, ma è specifico del driver che vengono applicati prima di utilizza nuovamente l'istruzione. In qualsiasi momento, è possono impostare gli attributi di istruzione rimanenti.  
  
> [!NOTE]  
>  La possibilità di impostare gli attributi di istruzione a livello di connessione chiamando **SQLSetConnectAttr** è stato deprecato in ODBC 3. *x*. ODBC 3. *x* applicazioni non devono mai impostata gli attributi di istruzione a livello di connessione. ODBC 3. *x* driver necessitano supportano questa funzionalità solo se funzionano con ODBC 2. *x* applicazioni. Per ulteriori informazioni, vedere [SQLSetConnectOption Mapping](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
>   
>  Un'eccezione il caso gli attributi SQL_ATTR_METADATA_ID e SQL_ATTR_ASYNC_ENABLE, entrambi gli attributi di connessione e gli attributi di istruzione che possono essere impostati a livello di connessione o il livello di istruzione.  
>   
>  Nessuno degli attributi di istruzione introdotti in ODBC 3. *x* (tranne SQL_ATTR_METADATA_ID) può essere impostata a livello di connessione.  
  
 Per ulteriori informazioni, vedere il [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) descrizione della funzione.
