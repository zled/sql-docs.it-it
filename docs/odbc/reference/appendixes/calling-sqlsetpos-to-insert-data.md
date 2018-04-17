---
title: La funzione SQLSetPos per inserire dati | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7912db8105a67fcd6240c107778b55b3dcacd0c4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="calling-sqlsetpos-to-insert-data"></a>La funzione SQLSetPos per inserire i dati
Quando un'applicazione ODBC 2. *x* applicazione che utilizza un'applicazione ODBC 3*x* driver chiama **SQLSetPos** con un *operazione* argomento di SQL_ADD, gestione Driver non eseguire il mapping di questa chiamata a **SQLBulkOperations**. Se un'applicazione ODBC 3*x* driver dovrebbe funzionare con un'applicazione che chiama **SQLSetPos** con SQL_ADD, il driver deve supportare l'operazione.  
  
 La principale differenza nel comportamento quando **SQLSetPos** viene chiamato con SQL_ADD si verifica quando viene chiamato in stato S6. In ODBC 2. *x*, il driver ha restituito S1010 quando **SQLSetPos** è stata chiamata con SQL_ADD nello stato S6 (dopo il cursore è stato posizionato con **SQLFetch**). In ODBC 3*x*, **SQLBulkOperations** con un *operazione* di SQL_ADD può essere chiamato in stato S6. Una differenza principale secondo comportamento è che **SQLBulkOperations** con un *operazione* di SQL_ADD può essere chiamato in stato S5, mentre **SQLSetPos** con un  **Operazione** di SQL_ADD non è possibile. Per le transizioni di istruzione che possono verificarsi per la stessa chiamata in ODBC 3*x*, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
