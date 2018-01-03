---
title: Cosa il Driver | Documenti Microsoft
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
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: 75dcdea6-ff6b-4ac8-aa11-a1f9edbeb8e6
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c4c1bf17e8a54f4eeb8722b1a17b9e85b930dd00
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="what-the-driver-does"></a>Cosa il Driver
Nella tabella seguente sono riepilogate le funzioni e gli attributi delle istruzioni un'applicazione ODBC 3*x* driver devono implementare per il blocco e i cursori scorrevoli.  
  
|Funzione o<br /><br /> attributo di istruzione|Commenti|  
|-----------------------------------------|--------------|  
|VENGONO IMPOSTATI SQL_ATTR_ROW_STATUS_PTR|Imposta l'indirizzo della matrice di stato di riga vengono immesse **SQLFetch** e **SQLFetchScroll**. Questa matrice viene inoltre compilata **SQLSetPos** se **SQLSetPos** viene chiamato in stato di istruzione S6. Se **SQLSetPos** viene chiamato in stato S7, questa matrice non è compilata, ma la matrice a cui punta il *RowStatusArray* argomento di **SQLExtendedFetch** viene compilato. Per ulteriori informazioni, vedere [istruzione transizioni](../../../odbc/reference/appendixes/statement-transitions.md) in tabelle di transizione dello stato di appendice b: ODBC.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Imposta l'indirizzo del buffer in cui **SQLFetch** e **SQLFetchScroll** restituire il numero di righe recuperate. Se **SQLExtendedFetch** viene chiamato, questo buffer non è compilato, ma il *RowCountPtr* argomento punta al numero di righe recuperate.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Imposta le dimensioni del set di righe utilizzate da **SQLFetch** e **SQLFetchScroll**.|  
|SQL_ROWSET_SIZE|Imposta le dimensioni del set di righe utilizzate da **SQLExtendedFetch**. ODBC 3*x* driver implementano se desiderano utilizzare ODBC 2. *x* applicazioni che chiamano **SQLExtendedFetch** o **SQLSetPos**.|  
|**SQLBulkOperations**|Se un'applicazione ODBC 3*x* driver dovrebbero funzionare con ODBC 2. *x* le applicazioni che utilizzano **SQLSetPos** con un *operazione* di SQL_ADD, il driver deve supportare **SQLSetPos** con un  *Operazione* di SQL_ADD oltre a **SQLBulkOperations** con un *operazione* di SQL_ADD.|  
|**SQLExtendedFetch.**|Restituisce il set di righe specificato. ODBC 3*x* driver implementano se desiderano utilizzare ODBC 2. *x* applicazioni che chiamano **SQLExtendedFetch** o **SQLSetPos**. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Il driver recupera le dimensioni del set di righe dal valore dell'attributo di istruzione SQL_ROWSET_SIZE.<br />-Il driver recupera l'indirizzo della matrice di stato di riga dal *RowStatusArray* argomento, non l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR. Il *RowStatusArray* argomento in una chiamata a **SQLExtendedFetch** non deve essere un puntatore null. (Si noti che in ODBC 3*x*, l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR può essere un puntatore null.)<br />-Il driver recupera l'indirizzo del buffer di righe recuperate dal *RowCountPtr* argomento, non l'attributo SQL_ATTR_ROWS_FETCHED_PTR dell'istruzione.<br />-Il driver restituisce SQLSTATE 01S01 (errore nella riga) per indicare che si è verificato un errore mentre le righe recuperate da una chiamata a **SQLExtendedFetch**. Un'applicazione ODBC 3*x* driver deve restituire 01S01 SQLSTATE (errore nella riga) solo quando **SQLExtendedFetch** viene chiamato, non quando **SQLFetch** o **SQLFetchScroll** viene chiamato. Per mantenere la compatibilità con le versioni precedenti, quando 01S01 SQLSTATE (errore nella riga) restituito da **SQLExtendedFetch**, gestione Driver non sono ordinati i record di stato nella coda degli errori in base alle regole indicato "sequenza di stato Registra"sezione di [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).|  
|**SQLFetch**|Restituisce il set di righe successivo. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Il driver recupera le dimensioni del set di righe dal valore dell'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE.<br />-Il driver recupera l'indirizzo della matrice di stato di riga dell'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.<br />-Il driver recupera l'indirizzo delle righe recuperate buffer dall'attributo SQL_ATTR_ROWS_FETCHED_PTR istruzione.<br />-L'applicazione è possibile combinare le chiamate tra **SQLFetchScroll** e **SQLFetch**.<br />-   **SQLFetch** restituisce i segnalibri, se è associata la colonna 0.<br />-   **SQLFetch** può essere chiamata per restituire più righe.<br />-Il driver non restituisce SQLSTATE 01S01 (errore nella riga) per indicare che si è verificato un errore mentre le righe recuperate da una chiamata a **SQLFetch**.|  
|**SQLFetchScroll**|Restituisce il set di righe specificato. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Il driver recupera le dimensioni del set di righe dall'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE.<br />-Il driver recupera l'indirizzo della matrice di stato di riga dell'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.<br />-Il driver recupera l'indirizzo delle righe recuperate buffer dall'attributo SQL_ATTR_ROWS_FETCHED_PTR istruzione.<br />-L'applicazione è possibile combinare le chiamate tra **SQLFetchScroll** e **SQLFetch**.<br />-Il driver non restituisce SQLSTATE 01S01 (errore nella riga) per indicare che si è verificato un errore mentre le righe recuperate da una chiamata a **SQLFetchScroll**.|  
|**SQLSetPos**|Esegue diverse operazioni posizionate. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Può essere richiamata in stati istruzione S6 o S7. Per ulteriori informazioni, vedere [istruzione transizioni](../../../odbc/reference/appendixes/statement-transitions.md) in tabelle di transizione dello stato di appendice b: ODBC.<br />-Se si tratta di istruzione o in stato S5 S6, il driver recupera le dimensioni del set di righe dall'attributo SQL_ATTR_ROWS_FETCHED_PTR dell'istruzione e l'indirizzo della matrice di stato di riga dell'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.<br />-Se si tratta in stato di istruzione S7, il driver recupera le dimensioni del set di righe dall'attributo di istruzione SQL_ROWSET_SIZE e l'indirizzo della matrice di stato di riga dal *RowStatusArray* argomento di  **SQLExtendedFetch**.<br />-Il driver restituisce SQLSTATE 01S01 (errore nella riga) solo per indicare che si è verificato un errore mentre le righe recuperate da una chiamata a **SQLSetPos** per eseguire un'operazione bulk quando la funzione viene chiamata in stato S7. Per mantenere la compatibilità con le versioni precedenti, se SQLSTATE 01S01 (errore nella riga) restituito da **SQLSetPos**, gestione Driver non sono ordinati i record di stato nella coda degli errori in base alle regole indicato "Sequenza di record di stato" sezione di [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).<br />-Se il driver dovrebbe funzionare con ODBC 2. *x* applicazioni che chiamano **SQLSetPos** con un *operazione* argomento di SQL_ADD, il driver deve supportare **SQLSetPos** con un  *Operazione* argomento di SQL_ADD.|
