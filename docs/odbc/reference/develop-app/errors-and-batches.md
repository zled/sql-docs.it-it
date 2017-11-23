---
title: Errori e batch | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4f00a70ec411824da13d37666c7b22f92248a236
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="errors-and-batches"></a>Errori e batch
Quando si verifica un errore durante l'esecuzione di un batch di istruzioni SQL, uno dei seguenti quattro risultati sono possibili. (Ogni risultato possibili è specifici dell'origine dati e può dipendere anche le istruzioni incluse nel batch).  
  
-   Viene eseguita alcuna istruzione nel batch.  
  
-   Viene eseguita alcuna istruzione nel batch e viene eseguito il rollback della transazione.  
  
-   Vengono eseguite tutte le istruzioni prima dell'istruzione di errore.  
  
-   Vengono eseguite tutte le istruzioni, ad eccezione dell'istruzione di errore.  
  
 Nei primi due casi, **SQLExecute** e **SQLExecDirect** restituirà SQL_ERROR. Negli ultimi due casi, possono restituire SQL_SUCCESS_WITH_INFO o SQL_SUCCESS, a seconda dell'implementazione. In tutti i casi, ulteriori informazioni sull'errore possono essere recuperati con **SQLGetDiagField**, **SQLGetDiagRec**, o **SQLError**. Tuttavia, la natura e la profondità di queste informazioni è specifici dell'origine dati. Queste informazioni sono inoltre improbabile identificare esattamente l'istruzione in errore.
