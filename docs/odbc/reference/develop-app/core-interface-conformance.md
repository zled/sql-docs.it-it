---
title: Conformità di interfaccia di base | Documenti Microsoft
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
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- core-level interface conformance levels [ODBC]
ms.assetid: aaaa864a-6477-45ff-a50a-96d8db66a252
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c45fdfe2b01ddfd34e7db391b799b95ce696da8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913986"
---
# <a name="core-interface-conformance"></a>Conformità di interfaccia di base
Tutti i driver ODBC devono presentare almeno a livello di base della conformità di interfaccia. Poiché le funzionalità del livello di base sono quelle richieste dalle applicazioni interoperabili più generiche, con tali applicazioni possa utilizzare il driver. Le funzionalità del livello di base corrispondono anche con le funzionalità definite nella specifica ISO CLI e con le funzionalità necessari definite nella specifica Open CLI di gruppo. Un driver ODBC a livello di base conforme allo standard dell'interfaccia consente all'applicazione di eseguire tutte le operazioni seguenti:  
  
-   Alloca e libera tutti i tipi di handle, chiamando **SQLAllocHandle** e **SQLFreeHandle**.  
  
-   Tutte le forme di utilizzare il **SQLFreeStmt** (funzione).  
  
-   Associare colonne del set di risultati, chiamando **SQLBindCol**.  
  
-   Gestire i parametri dinamici, incluse le matrici di parametri, l'input solo in direzione, chiamando **SQLBindParameter** e **SQLNumParams**. (I parametri nella direzione dell'output sono funzionalità 203 in [la conformità a livello 2 interfaccia](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Specificare un offset di associazione.  
  
-   Utilizzare la finestra di dialogo data-at-execution, che includono chiamate a **SQLParamData** e **SQLPutData**.  
  
-   Gestire i cursori e nomi di cursore, chiamando **SQLCloseCursor**, **SQLGetCursorName**, e **SQLSetCursorName**.  
  
-   Accedere alla descrizione (metadati) di set di risultati, chiamando **SQLColAttribute**, **SQLDescribeCol**, **SQLNumResultCols**, e **SQLRowCount** . (Utilizzo di queste funzioni il numero di colonna 0 per recuperare i metadati di segnalibro è funzionalità 204 in [la conformità a livello 2 interfaccia](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Il dizionario dei dati, eseguire una query chiamando le funzioni di catalogo **SQLColumns**, **SQLGetTypeInfo**, **SQLStatistics**, e **SQLTables**.  
  
     Il driver non è necessario per supportare i nomi di tabelle e viste in più parti. (Per ulteriori informazioni, vedere funzionalità 101 [la conformità a livello 1 interfaccia](../../../odbc/reference/develop-app/level-1-interface-conformance.md) e funzionalità 201 in [la conformità a livello 2 interfaccia](../../../odbc/reference/develop-app/level-2-interface-conformance.md).) Tuttavia, alcune funzionalità della specifica SQL-92, ad esempio nomi di indici e di qualificazione di colonna sono sintatticamente paragonabili a denominazione multipart. Il presente elenco di funzioni ODBC non è introdurre nuove opzioni in questi aspetti di SQL-92.  
  
-   Gestire origini dati e le connessioni, chiamando **SQLConnect**, **SQLDataSources**, **SQLDisconnect**, e **SQLDriverConnect**. Ottenere informazioni sui driver, indipendentemente da quale ODBC livello che supportano, chiamando **SQLDrivers**.  
  
-   Preparare ed eseguire istruzioni SQL, chiamando **SQLExecDirect**, **SQLExecute**, e **SQLPrepare**.  
  
-   Recuperare una riga di un set di risultati o più righe, in avanti, chiamando **SQLFetch** o chiamando **SQLFetchScroll** con il *FetchOrientation* argomento Impostare su SQL_FETCH_NEXT.  
  
-   Ottenere una colonna non associata in parti, chiamando **SQLGetData**.  
  
-   Ottenere i valori correnti di tutti gli attributi, chiamando **SQLGetConnectAttr**, **SQLGetEnvAttr**, e **SQLGetStmtAttr**e impostare gli attributi di tutti i valori predefiniti e impostare valori non predefiniti determinati attributi chiamando **SQLSetConnectAttr**, **SQLSetEnvAttr**, e **SQLSetStmtAttr**.  
  
-   Modificare alcuni campi di descrittori, chiamando **SQLCopyDesc**, **SQLGetDescField**, **SQLGetDescRec**, **SQLSetDescField**, e **SQLSetDescRec**.  
  
-   Ottenere informazioni di diagnostica, chiamare **SQLGetDiagField** e **SQLGetDiagRec**.  
  
-   Rilevare le funzionalità del driver, chiamando **SQLGetFunctions** e **SQLGetInfo**. Inoltre, il risultato di qualsiasi sostituzioni di testo apportate a un'istruzione SQL prima che venga inviato all'origine dati, tramite la chiamata di rilevare **SQLNativeSql**.  
  
-   Utilizzare la sintassi di **SQLEndTran** per eseguire il commit di una transazione. Un driver a livello di base non deve supportare le transazioni true. Pertanto, l'applicazione non è possibile specificare SQL_ROLLBACK né SQL_AUTOCOMMIT_OFF per l'attributo di connessione SQL_ATTR_AUTOCOMMIT. (Per ulteriori informazioni, vedere funzionalità 109 [la conformità a livello 2 interfaccia](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Chiamare **SQLCancel** per annullare la finestra di dialogo data-at-execution e, in ambienti multithread, annullare un'esecuzione di funzione ODBC in un altro thread. Conformità di interfaccia a livello di base non implica il supporto per l'esecuzione asincrona delle funzioni, né l'uso di **SQLCancel** per annullare una funzione ODBC in esecuzione in modo asincrono. La piattaforma né il driver ODBC devono essere multithread per il driver eseguire le attività di indipendenti nello stesso momento. Tuttavia, negli ambienti multithread, il driver ODBC deve essere thread-safe. Serializzazione delle richieste dall'applicazione è una modalità conforme per implementare questa specifica, anche se potrebbe creare problemi di prestazioni gravi.  
  
-   Ottenere la colonna SQL_BEST_ROWID identificazione delle righe delle tabelle, chiamando **SQLSpecialColumns**. (Il supporto per SQL_ROWVER è funzionalità 208 in [la conformità a livello 2 interfaccia](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
    > [!IMPORTANT]  
    >  Il livello di conformità di interfaccia di base devono implementare le funzioni ODBC (driver).
