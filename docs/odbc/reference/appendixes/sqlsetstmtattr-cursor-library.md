---
title: SQLSetStmtAttr (libreria di cursori) | Documenti Microsoft
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
- SQLSetStmtAttr function [ODBC], Cursor Library
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb02eae512230d039cd87eafabfeffaf0af13b6e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910186"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLSetStmtAttr** funzione nella libreria di cursori. Per informazioni generali su **SQLSetStmtAttr**, vedere [funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 La libreria di cursori supporta i seguenti attributi di istruzione con **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 La libreria di cursori supporta solo i valori dell'attributo di istruzione SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY e SQL_CURSOR_STATIC.  
  
 Per i cursori forward-only, la libreria di cursori supporta il valore SQL_CONCUR_READ_ONLY dell'attributo di istruzione SQL_ATTR_CONCURRENCY. Per i cursori statici, la libreria di cursori supporta i valori SQL_CONCUR_READ_ONLY e SQL_CONCUR_VALUES dell'attributo di istruzione SQL_ATTR_CONCURRENCY.  
  
 La libreria di cursori supporta solo il valore SQL_SC_NON_UNIQUE dell'attributo di istruzione SQL_ATTR_SIMULATE_CURSOR.  
  
 Anche se la specifica ODBC supporta le chiamate a **SQLSetStmtAttr** con gli attributi SQL_ATTR_PARAM_BIND_TYPE o SQL_ATTR_ROW_BIND_TYPE dopo **SQLFetch** o **SQLFetchScroll**  è stato chiamato, il cursore non di libreria. Prima di è possibile modificare il tipo di associazione nella libreria di cursori, l'applicazione deve chiudere il cursore. La libreria di cursori supporta la modifica di SQL_ATTR_ROW_BIND_OFFSET_PTR SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR e gli attributi di istruzione SQL_ATTR_PARAMS_PROCESSED_PTR quando un cursore è aperto.  
  
 Un'applicazione può chiamare **SQLSetStmtAttr** con un **attributo** di SQL_ATTR_ROW_ARRAY_SIZE per modificare le dimensioni del set di righe mentre è aperto un cursore. Le nuove dimensioni del set di righe saranno effettive la volta successiva che **SQLFetchScroll** o **SQLFetch** viene chiamato.  
  
 La libreria di cursori supporta l'impostazione dell'attributo di istruzione SQL_ATTR_PARAM_BIND_OFFSET_PTR o SQL_ATTR_ROW_BIND_OFFSET_PTR per abilitare gli offset di associazione. L'offset di associazione non essere utilizzato per le chiamate a **SQLFetch** quando la libreria di cursori viene utilizzata con un ODBC 2. *x* driver.  
  
 La libreria di cursori supporta l'impostazione dell'attributo di istruzione SQL_ATTR_USE_BOOKMARKS su SQL_UB_VARIABLE.
