---
title: SQLSetPos (libreria di cursori) | Documenti Microsoft
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
- SQLSetPos function [ODBC], Cursor Library
ms.assetid: 574399c3-2bb2-4d19-829c-7c77bd82858d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b195ca1dbb138b21fcf107150832288df8317196
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLSetPos** funzione nella libreria di cursori. Per informazioni generali su **SQLSetPos**, vedere [funzione SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 La libreria di cursori supporta l'operazione SQL_POSITION solo per il *operazione* argomento **SQLSetPos**. Supporta il valore SQL_LOCK_NO_CHANGE solo per il *LockType* argomento.  
  
 Se il driver non supporta operazioni bulk, la libreria di cursori restituisce SQLSTATE HYC00 (Driver non valido) quando **SQLSetPos** viene chiamato con *RowNumber* uguale a 0. Questo comportamento del driver non è consigliato.  
  
 La libreria di cursori non supporta le operazioni di SQL_UPDATE e SQL_DELETE in una chiamata a **SQLSetPos**. L'oggetto implementa libreria cursore un posizionato, aggiornare o eliminare l'istruzione SQL tramite la creazione di una ricerca istruzioni update o delete con una clausola WHERE che enumera i valori memorizzati nella cache per ogni colonna associata. Per ulteriori informazioni, vedere [istruzioni di eliminazione e l'elaborazione di aggiornamento posizionato](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md).  
  
 Se il driver non supporta i cursori statici, è necessario chiamare un'applicazione che utilizza la libreria di cursori **SQLSetPos** solo su un set di righe recuperate dalle **SQLExtendedFetch** o **SQLFetchScroll **, non da **SQLFetch**. La libreria di cursori implementa **SQLExtendedFetch** e **SQLFetchScroll** eseguendo chiamate ripetute di **SQLFetch** (con un set di righe pari a 1) nel driver. La libreria di cursori passa le chiamate a **SQLFetch**, su altro canto, tramite il driver. Se **SQLSetPos** viene chiamato su un set di righe di più righe recuperate dalle **SQLFetch** quando il driver non supporta i cursori statici, la chiamata avrà esito negativo perché **SQLSetPos** non funziona con cursori forward-only. Ciò si verifica anche se un'applicazione è stato chiamato **SQLSetStmtAttr** su cui impostare SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, che la libreria di cursori supporta anche se il driver non supporta i cursori statici.

