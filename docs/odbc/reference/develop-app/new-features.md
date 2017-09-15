---
title: "Nuove funzionalità | Documenti Microsoft"
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
- backward compatibility [ODBC], new features in release
- ODBC drivers [ODBC], backward compatibility
- new features [ODBC]
- compatibility [ODBC], new features in release
- ODBC [ODBC], new features
ms.assetid: a8fcdd00-6cb3-4871-9489-6018b3d0d65f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e2b48097b6c398772e14d2594a583d89e6825e0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="new-features"></a>Nuove funzionalità
Le seguenti nuove funzionalità sono stata introdotta in ODBC 3. *x*. Un database ODBC 3. *x* applicazione che utilizza un ODBC 2*x* driver non sarà in grado di utilizzare questa funzionalità. ODBC 3. *x* gestione Driver non eseguire il mapping di queste funzionalità quando si lavora con un ODBC 2*x* driver.  
  
-   Funzioni che accettano un descrittore di gestiscono come argomento: **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**, e **SQLCopyDesc**.  
  
-   Le funzioni **SQLSetEnvAttr** e **SQLGetEnvAttr**.  
  
-   L'utilizzo di **SQLAllocHandle** per allocare un handle descrittore. (L'uso di **SQLAllocHandle** per allocare gli handle di ambiente, connessione e l'istruzione è una funzionalità duplicate, non è nuova,.)  
  
-   L'utilizzo di **SQLGetConnectAttr** per ottenere gli attributi di connessione SQL_ATTR_AUTO_IPD. (L'uso di **SQLSetConnectAttr** per impostare, e **SQLGetConnectAttr** per ottenere, altri attributi di connessione è una funzionalità duplicate, non è nuova,.)  
  
-   L'utilizzo di **SQLSetStmtAttr** per impostare, e **SQLGetStmtAttr** per ottenere i seguenti attributi di istruzione. (L'uso di **SQLSetStmtAttr** per impostare, e **SQLGetStmtAttr** per ottenere, altri attributi di istruzione è una funzionalità duplicate, non è nuova,.)  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_ENABLE_AUTO_IPD  
  
     SQL_ATTR_FETCH_BOOKMARK_PTR  
  
     SQL_ATTR_BIND_OFFSET  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     SQL_DESC_PARAM_STATUS_PTR  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR  
  
     SQL_ATTR_PARAMSET_SIZE  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_ROW_ARRAY_SIZE  
  
-   L'utilizzo di **SQLGetStmtAttr** per ottenere i seguenti attributi di istruzione. (L'uso di **SQLGetStmtAttr** per ottenere un'altra istruzione attributi è una funzionalità duplicate, non nuove funzionalità.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Utilizzo del tipo di dati di intervallo C, i tipi di dati di intervallo SQL, i tipi di dati BIGINT C e la struttura dei dati SQL_C_NUMERIC.  
  
-   L'associazione di parametri.  
  
-   Recupera basato su offset segnalibro, ad esempio la chiamata **SQLFetchScroll** con un *FetchOrientation* argomento di SQL_FETCH_BOOKMARK e specificando un offset diverso da 0.  
  
-   **SQLFetch** che restituisce la matrice di stato di riga, numero di righe recuperate, il recupero di più righe, combinare le chiamate con **SQLFetchScroll**e combinare le chiamate con **SQLBulkOperations** o **SQLSetPos**. Per ulteriori informazioni, vedere la sezione successiva, [cursori a blocchi, i cursori scorrevoli e la compatibilità con le applicazioni ODBC 3. x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Parametri denominati.  
  
-   Qualsiasi valore ODBC 3. *x*– specifico **SQLGetInfo** opzioni. (Se ODBC 3. *x* applicazione che utilizza un ODBC 2.* x* driver chiama i tipi di informazioni SQL_XXX_CURSOR_ATTRIBUTES1 che sono sostituiti diversi ODBC 2.* x* tipi di informazioni, alcune delle informazioni potrebbero essere affidabile, ma alcune potrebbero essere inaffidabili. Per ulteriori informazioni, vedere [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Associare gli offset.  
  
-   L'aggiornamento, aggiornamento ed eliminazione dai segnalibri (tramite una chiamata a **SQLBulkOperations**).  
  
-   La chiamata **SQLBulkOperations** o **SQLSetPos** nello stato S5.  
  
-   I campi ROW_NUMBER e col nel record di diagnostica (che devono essere recuperati tramite le funzioni di sostituzione **SQLGetDiagField** o **SQLGetDiagRec**).  
  
-   Conteggi di righe approssimativa.  
  
-   Le informazioni sull'avviso (SQL_ROW_SUCCESS_WITH_INFO da **SQLFetchScroll**).  
  
-   Segnalibri a lunghezza variabile.  
  
-   Informazioni dettagliate sull'errore per le matrici di parametri.  
  
-   Tutte le nuove colonne nei set di risultati restituiti dalle funzioni di catalogo.  
  
-   Utilizzo di **SQLDescribeCol** e **SQLColAttribute** nella colonna 0.  
  
-   Utilizzo di qualsiasi ODBC 3. *x*: gli attributi di colonna specifica in una chiamata a **SQLColAttribute**.  
  
-   Utilizzo di più handle di ambiente.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Cursori a blocchi, i cursori scorrevoli e la compatibilità con le applicazioni ODBC 3. x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)
