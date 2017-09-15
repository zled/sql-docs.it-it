---
title: Dimensioni del set di righe | Documenti Microsoft
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
- rowset size [ODBC]
- cursors [ODBC], block
- result sets [ODBC], rowset size
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 60366ae8-175c-456a-ae5e-bdd860786911
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b7d3abee6c42fe95205bbb74edc671d8dc02bf87
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="rowset-size"></a>Dimensioni del set di righe
La dimensione del set di righe da utilizzare dipende dall'applicazione. Applicazioni basate su schermo comunemente seguono una delle due strategie. Il primo consiste nell'impostare le dimensioni del set di righe per il numero di righe visualizzate sullo schermo. Se l'utente ridimensiona la schermata, l'applicazione cambierà di conseguenza le dimensioni del set di righe. Il secondo consiste nell'impostare le dimensioni del set di righe su un numero maggiore, ad esempio 100, che consente di ridurre il numero di chiamate all'origine dati. L'applicazione lo scorrimento in locale all'interno del set di righe quando possibile e recupera le nuove righe solo quando scorre all'esterno del set di righe.  
  
 Altre applicazioni, ad esempio report, tendono a impostare le dimensioni del set di righe per il numero massimo di righe, l'applicazione è in grado di gestire, con un set di righe maggiore, la rete overhead per ogni riga viene talvolta ridotto. Esattamente come grandi un set di righe può essere dipende dalle dimensioni di ogni riga e la quantità di memoria disponibile.  
  
 Dimensioni del set di righe sono impostata da una chiamata a **SQLSetStmtAttr** con un *attributo* argomento di SQL_ATTR_ROW_ARRAY_SIZE. L'applicazione può modificare le dimensioni del set di righe, associare i nuovi set di righe buffer (chiamando **SQLBindCol** o specificando un offset di associazione) anche dopo le righe recuperate, o entrambi. Le implicazioni della modifica delle dimensioni del set di righe dipendono dalla funzione:  
  
-   **SQLFetch** e **SQLFetchScroll** utilizzare le dimensioni del set di righe al momento della chiamata per determinare il numero di righe da recuperare. Tuttavia, **SQLFetchScroll** con un *FetchOrientation* di incrementi SQL_FETCH_NEXT il cursore basato su set di righe del recupero precedente e quindi recupera un set di righe in base alla dimensione del set di righe corrente.  
  
-   **SQLSetPos** utilizza le dimensioni del set di righe che sono attiva a partire dalla chiamata precedente a **SQLFetch** o **SQLFetchScroll**perché **SQLSetPos** opera su un set di righe che è già stata impostata. **SQLSetPos** anche selezionerà la nuova dimensione del set di righe se **SQLBulkOperations** è stato chiamato dopo che è stata modificata la dimensione del set di righe.  
  
-   **SQLBulkOperations** viene utilizzata la dimensione del set di righe attive al momento della chiamata, perché consente di eseguire operazioni su una tabella indipendente da qualsiasi set di righe recuperate.
