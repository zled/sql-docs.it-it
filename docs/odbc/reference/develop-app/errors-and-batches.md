---
title: Errori e batch | Documenti Microsoft
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
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e793309d25bb81eb4b65129f65276ab9ea9091ff
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="errors-and-batches"></a>Errori e batch
Quando si verifica un errore durante l'esecuzione di un batch di istruzioni SQL, uno dei seguenti quattro risultati sono possibili. (Ogni risultato possibili è specifici dell'origine dati e può dipendere anche le istruzioni incluse nel batch).  
  
-   Viene eseguita alcuna istruzione nel batch.  
  
-   Viene eseguita alcuna istruzione nel batch e viene eseguito il rollback della transazione.  
  
-   Vengono eseguite tutte le istruzioni prima dell'istruzione di errore.  
  
-   Vengono eseguite tutte le istruzioni, ad eccezione dell'istruzione di errore.  
  
 Nei primi due casi, **SQLExecute** e **SQLExecDirect** restituirà SQL_ERROR. Negli ultimi due casi, possono restituire SQL_SUCCESS_WITH_INFO o SQL_SUCCESS, a seconda dell'implementazione. In tutti i casi, ulteriori informazioni sull'errore possono essere recuperati con **SQLGetDiagField**, **SQLGetDiagRec**, o **SQLError**. Tuttavia, la natura e la profondità di queste informazioni è specifici dell'origine dati. Queste informazioni sono inoltre improbabile identificare esattamente l'istruzione in errore.

