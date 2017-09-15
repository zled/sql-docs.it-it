---
title: Determinazione del numero di righe interessate | Documenti Microsoft
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
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b2f030be011864be17c8539d8ab94f6980f0f791
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="determining-the-number-of-affected-rows"></a>Determinazione del numero di righe interessate
Dopo che un'applicazione aggiorna, Elimina o inserisce righe, è possibile chiamare **SQLRowCount** per determinare il numero di righe interessato. **SQLRowCount** restituisce questo valore se le righe sono state aggiornate, eliminate o inserite eseguendo un **aggiornamento**, **eliminare**, o **inserire** istruzione, eseguendo un'istruzione delete o un aggiornamento posizionato, oppure chiamando **SQLSetPos**.  
  
 Se viene eseguito un batch di istruzioni SQL, il conteggio delle righe interessate potrebbe essere un conteggio totale per tutte le istruzioni nel batch o conteggi singoli per ogni istruzione nel batch. Per ulteriori informazioni, vedere [batch di istruzioni SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) e [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Il numero di righe interessate viene restituito anche nel campo di intestazione diagnostica SQL_DIAG_ROW_COUNT nell'area di diagnostica associato all'handle di istruzione. Tuttavia, i dati in questo campo viene reimpostati dopo ciascuna funzione chiamata sullo stesso handle di istruzione, mentre il valore restituito da **SQLRowCount** rimane invariato fino a quando una chiamata a **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, o **SQLSetPos**.
