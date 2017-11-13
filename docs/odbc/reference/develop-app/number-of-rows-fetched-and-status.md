---
title: Numero di righe recuperate e stato | Documenti Microsoft
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
- row status array [ODBC]
- number of rows fetched [ODBC]
- result sets [ODBC], row status array
ms.assetid: a069b979-5108-4905-932f-8ae8e7905ff2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3e79fec9836fb7a6528bea63c78a8e6479dac8e1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="number-of-rows-fetched-and-status"></a>Numero di righe recuperate e stato
Se è stato impostato l'attributo SQL_ATTR_ROWS_FETCHED_PTR dell'istruzione, specifica un buffer che restituisce il numero di righe recuperate dalla chiamata a **SQLFetch** o **SQLFetchScroll**e le righe di errore. (Questo numero è un conteggio di tutte le righe che non contengono lo stato SQL_ROW_NO_ROWS). Dopo una chiamata a **SQLBulkOperations** o **SQLSetPos**, il buffer contiene il numero di righe interessate da un'operazione bulk eseguita dalla funzione. Se è stato impostato l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR, **SQLFetch** o **SQLFetchScroll** restituisce il *matrice di stato di riga,* che fornisce lo stato di ogni riga restituita. Entrambi i buffer a cui fa riferimento a questi campi vengono allocati dall'applicazione e popolati dal driver. Un'applicazione deve garantire che questi puntatori rimangono validi fino a quando il cursore è chiuso.  
  
 Le voci nello stato di matrice di stato di riga se ogni riga è stata recuperata correttamente, se è stata aggiornata, aggiunti o eliminati dopo l'ultimo recupero e, se si è verificato un errore durante il recupero della riga. Se **SQLFetch** o **SQLFetchScroll** rileva un errore durante il recupero di una riga di un set di righe su più righe, o se **SQLBulkOperations** con un *operazione*  argomento di SQL_FETCH_BY_BOOKMARK rileva un errore durante l'esecuzione di un'operazione di recupero di massa, imposta il valore corrispondente nella matrice di stato di riga da SQL_ROW_ERROR, continua il recupero delle righe e viene restituito SQL_SUCCESS_WITH_INFO. Per ulteriori informazioni sulla gestione degli errori e la matrice di stato di riga, vedere il [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) e [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) funzione descrizioni.

