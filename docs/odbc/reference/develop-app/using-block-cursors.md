---
title: Utilizzo di cursori a blocchi | Documenti Microsoft
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
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fb2662ac4dcfc6a1f0fa2362bfc71f7a173bcd9c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="using-block-cursors"></a>Utilizzo di cursori a blocchi
Supporto per cursori a blocchi viene compilato in ODBC 3. *x*. **SQLFetch** può essere utilizzata solo per operazioni di recupero su più righe quando viene chiamato in ODBC 3. *x*; se un database ODBC 2. *x* applicazione chiama **SQLFetch**, verrà aperto solo un cursore a riga singola e forward-only. Quando un'applicazione ODBC 3. *x* applicazione chiama **SQLFetch** in un'API ODBC 2. *x* driver, restituisce una singola riga, a meno che il driver supporta **SQLExtendedFetch**. Per ulteriori informazioni, vedere [cursori a blocchi, i cursori scorrevoli e compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
 Per utilizzare cursori a blocchi, l'applicazione imposta le dimensioni del set di righe, associa i buffer di set di righe (come descritto nella sezione precedente), facoltativamente imposta gli attributi di istruzione SQL_ATTR_ROWS_FETCHED_PTR e vengono impostati SQL_ATTR_ROW_STATUS_PTR e chiamate **SQLFetch**  o **SQLFetchScroll** per recuperare un blocco di righe. L'applicazione può modificare le dimensioni del set di righe e associare nuovi buffer di set di righe (chiamando **SQLBindCol** o specificando un offset di associazione) anche dopo le righe recuperate.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Dimensione del set di righe](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Numero di righe recuperate e stato](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData e cursori a blocchi; cursore di blocco](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
