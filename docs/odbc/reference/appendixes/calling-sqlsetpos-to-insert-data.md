---
title: La funzione SQLSetPos per inserire dati | Documenti Microsoft
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
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e9d768ea5c16b199dc316726cb425b75d409bf1f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="calling-sqlsetpos-to-insert-data"></a>La funzione SQLSetPos per inserire i dati
Quando un'applicazione ODBC 2. *x* applicazione che utilizza un'applicazione ODBC 3*x* driver chiama **SQLSetPos** con un *operazione* argomento di SQL_ADD, gestione Driver non eseguire il mapping di questa chiamata a **SQLBulkOperations**. Se un'applicazione ODBC 3*x* driver dovrebbe funzionare con un'applicazione che chiama **SQLSetPos** con SQL_ADD, il driver deve supportare l'operazione.  
  
 La principale differenza nel comportamento quando **SQLSetPos** viene chiamato con SQL_ADD si verifica quando viene chiamato in stato S6. In ODBC 2. *x*, il driver ha restituito S1010 quando **SQLSetPos** è stata chiamata con SQL_ADD nello stato S6 (dopo il cursore è stato posizionato con **SQLFetch**). In ODBC 3*x*, **SQLBulkOperations** con un *operazione* di SQL_ADD può essere chiamato in stato S6. Una differenza principale secondo comportamento è che **SQLBulkOperations** con un *operazione* di SQL_ADD può essere chiamato in stato S5, mentre **SQLSetPos** con un  **Operazione** di SQL_ADD non è possibile. Per le transizioni di istruzione che possono verificarsi per la stessa chiamata in ODBC 3*x*, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).

