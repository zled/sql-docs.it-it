---
title: Record di stato | Documenti Microsoft
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
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e748612bf8293a0c7fca29b0baa21c9278e44d15
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="status-records"></a>Record di stato
I campi di record di stato contengono informazioni su errori o avvisi restituiti dall'origine di gestione Driver, driver o dati, tra cui SQLSTATE, il numero di errore nativo, messaggio di diagnostica, numero di colonna e il numero di riga specifici. Stato record possono essere creati solo se la funzione restituisce SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA o SQL_STILL_EXECUTING. Per un elenco completo dei campi di record di stato, vedere il [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) descrizione della funzione.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Sequenza di record di stato](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Messaggi di diagnostica](../../../odbc/reference/develop-app/diagnostic-messages.md)
