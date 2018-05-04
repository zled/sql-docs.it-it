---
title: Aggiornamento dei dati con SQLBulkOperations | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e354cb1bb69618a7a56a0286aeb90ea2ba24692e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data-with-sqlbulkoperations"></a>Aggiornamento dei dati con SQLBulkOperations
Le applicazioni possono eseguire operazioni update, delete, fetch o inserimento bulk nella tabella sottostante nell'origine dati con una chiamata a **SQLBulkOperations**. La chiamata **SQLBulkOperations** rappresenta un'alternativa utile alla creazione ed esecuzione di un'istruzione SQL. Consente un driver ODBC supporta gli aggiornamenti posizionati anche quando l'origine dati non supporta le istruzioni SQL posizionate. È parte del paradigma di ottenere accesso completo del database tramite le chiamate di funzione.  
  
 **SQLBulkOperations** opera su set di righe corrente e può essere usata solo dopo una chiamata a **SQLFetch** o **SQLFetchScroll**. L'applicazione specifica le righe per aggiornare, eliminare o aggiornare memorizzando nella cache i segnalibri. Il driver recupera i nuovi dati per le righe da aggiornare o i nuovi dati da inserire nella tabella sottostante, dai buffer di set di righe.  
  
 Le dimensioni del set di righe deve essere utilizzato dal **SQLBulkOperations** è impostata da una chiamata a **SQLSetStmtAttr** con un *attributo* argomento di SQL_ATTR_ROW_ARRAY_SIZE. A differenza di **SQLSetPos**, che utilizza la nuova dimensione del set di righe solo dopo una chiamata a **SQLFetch** o **SQLFetchScroll**, **SQLBulkOperations** utilizza il nuova dimensione del set di righe dopo la chiamata a **SQLSetStmtAttr**.  
  
 Poiché la maggior parte delle interazioni con i database relazionali vengono eseguite tramite SQL, **SQLBulkOperations** è ampiamente supportato. Tuttavia, un driver può facilmente emulare creazione ed esecuzione di un **aggiornamento**, **eliminare**, o **inserire** istruzione.  
  
 Per determinare quali operazioni **SQLBulkOperation** supporta, un'applicazione chiama **SQLGetInfo** con SQL_DYNAMIC_CURSOR_ATTRIBUTES1 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR _ATTRIBUTES1, o l'opzione relativa alle informazioni SQL_STATIC_CURSOR_ATTRIBUTES1 (a seconda del tipo di cursore).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Aggiornamento delle righe tramite segnalibro con SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Eliminazione di righe tramite segnalibro con SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Inserimento di righe con SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Recupero di righe con SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
