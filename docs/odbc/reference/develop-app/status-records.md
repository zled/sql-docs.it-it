---
title: Record di stato | Documenti Microsoft
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
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ab82d285a57c147a27cb248e1e28b1bd9c6d0241
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="status-records"></a>Record di stato
I campi di record di stato contengono informazioni su errori o avvisi restituiti dall'origine di gestione Driver, driver o dati, tra cui SQLSTATE, il numero di errore nativo, messaggio di diagnostica, numero di colonna e il numero di riga specifici. Stato record possono essere creati solo se la funzione restituisce SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA o SQL_STILL_EXECUTING. Per un elenco completo dei campi di record di stato, vedere il [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) descrizione della funzione.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Sequenza di record di stato](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Messaggi di diagnostica](../../../odbc/reference/develop-app/diagnostic-messages.md)

