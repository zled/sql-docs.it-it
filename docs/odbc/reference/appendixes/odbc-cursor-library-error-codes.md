---
title: Codici di errore libreria di cursori ODBC | Documenti Microsoft
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
- cursor library [ODBC], error codes
- error codes [ODBC], cursor library
- ODBC cursor library [ODBC], error codes
ms.assetid: 9713480e-8744-4f37-a630-20871590d4a1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 308ad8ed54aacb9ab7bc169efd9dad020e2f2b66
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-cursor-library-error-codes"></a>Codici di errore libreria di cursori ODBC
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Microsoft Data Access Components. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Utilizzare invece i cursori di driver e del server.  
  
 La libreria di cursori ODBC restituisce i seguente SQLSTATE oltre a quelli elencati [riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
> [!NOTE]  
>  La libreria di cursori non sono ordinati i record di stato. Gestione Driver e ODBC 3. *x* driver sono responsabili per l'ordinamento dei record di stato.  
  
|SQLSTATE|Description|Può essere restituito da|  
|--------------|-----------------|--------------------------|  
|01000|Cursore non è aggiornabile.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Libreria di cursori non usata. Caricamento non riuscito.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Libreria di cursori non usata. Supporto del driver insufficiente.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Libreria di cursori non usata. Versione non corrispondente con gestione Driver.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Driver restituito SQL_SUCCESS_WITH_INFO. Il messaggio di avviso è stata perso.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Errore generale: Impossibile creare il buffer di file.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Errore generale: Impossibile leggere dal buffer di file.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Errore generale: Impossibile scrivere nel buffer di file.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Errore generale: Impossibile chiudere o rimuovere il buffer di file.|**SQLFreeHandle**<br /><br /> **SQLFreeStmt**|  
|SL001|Impossibile eseguire richieste posizionate perché nessuna colonna di ricerca associata.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Richiesta di posizione non è riuscito perché il set di risultati è stato creato da una condizione di join.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Il buffer associato supera la dimensione massima del segmento.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Set di risultati non è stato generato da un **selezionare** istruzione.|**SQLGetData**|  
|SL005|**Selezionare** istruzione contiene una clausola GROUP BY.|**SQLGetData**|  
|SL006|Le matrici di parametri non sono supportate con le richieste di posizione.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData** non è consentita su un cursore forward-only (funzionalità).|**SQLGetData**|  
|SL009|Nessuna colonna associata prima di chiamare **SQLFetch** o **SQLFetchScroll**.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** restituito SQL_ERROR durante un tentativo di associare un buffer interno.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|Opzione di istruzione è valida solo dopo la chiamata **SQLFetch** o **SQLFetchScroll**.|**SQLGetStmtAttr**|  
|SL012|Associazioni di istruzione non possono essere modificate mentre è aperto un cursore.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **Funzione SQLSetStmtAttr**|  
|SL014|È stata eseguita una richiesta di posizione e non tutti i campi numero di colonna sono stati memorizzati nel buffer.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** e **SQLFetchScroll** non possono essere combinate.|**SQLExtendedFetch.**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|

