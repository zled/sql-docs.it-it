---
title: Utilizzando la libreria di cursori ODBC | Documenti Microsoft
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
- ODBC cursor library [ODBC], using cursor library
- cursor library [ODBC], using cursor library
ms.assetid: 9653f2f8-ccfc-4220-99ef-601dc0fa641c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: db98c1cee3b31615ee515fd197427724a39c9433
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-the-odbc-cursor-library"></a>Utilizzando la libreria di cursori ODBC
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 Per utilizzare la libreria di cursori ODBC, un'applicazione:  
  
1.  Chiamate **SQLSetConnectAttr** con un *attributo* di SQL_ATTR_ODBC_CURSORS per specificare come la libreria di cursori deve essere utilizzata con una determinata connessione. La libreria di cursori possa essere sempre utilizzato (SQL_CUR_USE_ODBC), utilizzata solo se il driver non supporta i cursori scorrevoli (SQL_CUR_USE_IF_NEEDED) o mai (SQL_CUR_USE_DRIVER).  
  
2.  Chiamate **SQLConnect**, **SQLDriverConnect**, o **SQLBrowseConnect** per la connessione all'origine dati.  
  
3.  Chiamate **SQLSetStmtAttr** per specificare il tipo di cursore (SQL_ATTR_CURSOR_TYPE), concorrenza (SQL_ATTR_CONCURRENCY) e dimensioni del set di righe (SQL_ATTR_ROW_ARRAY_SIZE). La libreria di cursori supporta i cursori forward-only e statici. I cursori forward-only devono essere di sola lettura, mentre i cursori statici possono essere di sola lettura oppure utilizzano il controllo della concorrenza ottimistica il confronto di valori.  
  
4.  Alloca uno o più set di righe buffer e chiama **SQLBindCol** una o più volte per associare questi buffer come risultato un set di colonne.  
  
5.  Genera un set di risultati, l'esecuzione di un **selezionare** istruzione o una stored procedure o chiamando una funzione di catalogo. Se l'applicazione verrà eseguite le istruzioni di aggiornamento posizionato, è necessario eseguire un **selezionare per aggiornare** istruzione per generare il set di risultati.  
  
6.  Chiamate **SQLFetch** o **SQLFetchScroll** una o più volte per scorrere il set di risultati.  
  
 L'applicazione può modificare i valori dei dati nei buffer di set di righe. Per aggiornare i buffer di set di righe con i dati dalla cache della libreria di cursori, un'applicazione chiama **SQLFetchScroll** con il *FetchOrientation* argomento impostato su SQL_FETCH_RELATIVE e * FetchOffset* argomento impostato su 0.  
  
 Per recuperare dati da una colonna non associata, l'applicazione chiama **SQLSetPos** per posizionare il cursore sulla riga desiderata. Chiama quindi **SQLGetData** per recuperare i dati.  
  
 Per determinare il numero di righe che sono stati recuperati dall'origine dati, l'applicazione chiama **SQLRowCount**.
