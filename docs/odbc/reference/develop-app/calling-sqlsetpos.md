---
title: La funzione SQLSetPos | Documenti Microsoft
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
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9e7eeeaa8e2268256b103095ef0077329c52cc9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="calling-sqlsetpos"></a>La funzione SQLSetPos
In ODBC 2. *x*, il puntatore alla matrice di stato di riga è un argomento a **SQLExtendedFetch**. La matrice di stato di riga è stata aggiornata in un secondo momento da una chiamata a **SQLSetPos**. Alcuni driver si basavano sul fatto che questa matrice non viene modificato tra **SQLExtendedFetch** e **SQLSetPos**. In ODBC 3. *x*, il puntatore alla matrice di stato è un campo di descrizione e pertanto l'applicazione può facilmente modificarlo in modo che punti a un'altra matrice. Può trattarsi di un problema quando un'applicazione ODBC 3. *x* applicazione sta utilizzando un'API ODBC 2. *x* driver, ma viene eseguita la chiamata **SQLSetStmtAttr** per impostare il puntatore dello stato della matrice e chiama **SQLFetchScroll** per recuperare i dati. Gestione Driver ne esegue il mapping come una sequenza di chiamate a **SQLExtendedFetch**. Nel codice seguente, generato un errore verrebbe normalmente quando Gestione Driver viene eseguito il mapping del secondo **SQLSetStmtAttr** chiamare quando si lavora con un ODBC 2*x* driver:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Verrà generato l'errore se sono non stati è possibile modificare il puntatore dello stato della riga in ODBC 2. *x* tra le chiamate a **SQLExtendedFetch**. Al contrario, gestione Driver esegue la procedura seguente quando si lavora con un ODBC 2*x* driver:  
  
1.  Inizializza un flag interno di gestione Driver *fSetPosError* su TRUE.  
  
2.  Quando un'applicazione chiama **SQLFetchScroll**, gestione Driver imposta *fSetPosError* su FALSE.  
  
3.  Quando l'applicazione chiama **SQLSetStmtAttr** per impostare SQL_ATTR_ROW_STATUS_PTR, gestione Driver imposta *fSetPosError* toTRUE uguale.  
  
4.  Quando l'applicazione chiama **SQLSetPos**, con *fSetPosError* uguale a TRUE, il Driver Manager genera SQL_ERROR con SQLSTATE HY011 (Impossibile impostare l'attributo ora) per indicare che l'applicazione tentativo di chiamare **SQLSetPos** dopo aver modificato il puntatore dello stato della riga, ma prima di chiamare **SQLFetchScroll**.
