---
title: Errori e batch | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: d00672166039421fb8518c52a58d19d73d02d477
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909356"
---
# <a name="errors-and-batches"></a>Errori e batch
Quando si verifica un errore durante l'esecuzione di un batch di istruzioni SQL, uno dei seguenti quattro risultati sono possibili. (Ogni risultato possibili è specifici dell'origine dati e può dipendere anche le istruzioni incluse nel batch).  
  
-   Viene eseguita alcuna istruzione nel batch.  
  
-   Viene eseguita alcuna istruzione nel batch e viene eseguito il rollback della transazione.  
  
-   Vengono eseguite tutte le istruzioni prima dell'istruzione di errore.  
  
-   Vengono eseguite tutte le istruzioni, ad eccezione dell'istruzione di errore.  
  
 Nei primi due casi, **SQLExecute** e **SQLExecDirect** restituirà SQL_ERROR. Negli ultimi due casi, possono restituire SQL_SUCCESS_WITH_INFO o SQL_SUCCESS, a seconda dell'implementazione. In tutti i casi, ulteriori informazioni sull'errore possono essere recuperati con **SQLGetDiagField**, **SQLGetDiagRec**, o **SQLError**. Tuttavia, la natura e la profondità di queste informazioni è specifici dell'origine dati. Queste informazioni sono inoltre improbabile identificare esattamente l'istruzione in errore.
