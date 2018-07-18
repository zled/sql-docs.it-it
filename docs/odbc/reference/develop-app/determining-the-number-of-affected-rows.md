---
title: Determinazione del numero di righe interessate | Documenti Microsoft
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
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3736f620e311f51ebd97ee99e71830722c2ee367
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="determining-the-number-of-affected-rows"></a>Determinazione del numero di righe interessate
Dopo che un'applicazione aggiorna, Elimina o inserisce righe, è possibile chiamare **SQLRowCount** per determinare il numero di righe interessato. **SQLRowCount** restituisce questo valore se non le righe sono state aggiornate, eliminate o inserite eseguendo un **aggiornamento**, **eliminare**, o **inserire** istruzione, tramite l'esecuzione di un oggetto posizionato aggiornare o istruzione delete o chiamando **SQLSetPos**.  
  
 Se viene eseguito un batch di istruzioni SQL, il conteggio delle righe interessate potrebbe essere un conteggio totale per tutte le istruzioni nel batch o conteggi singoli per ogni istruzione nel batch. Per ulteriori informazioni, vedere [batch di istruzioni SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) e [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Il numero di righe interessate viene restituito anche nel campo di intestazione diagnostica SQL_DIAG_ROW_COUNT nell'area di diagnostica associato all'handle di istruzione. Tuttavia, i dati in questo campo viene reimpostati dopo ciascuna funzione chiamata sullo stesso handle di istruzione, mentre il valore restituito da **SQLRowCount** rimane invariato fino a quando una chiamata a **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, o **SQLSetPos**.
