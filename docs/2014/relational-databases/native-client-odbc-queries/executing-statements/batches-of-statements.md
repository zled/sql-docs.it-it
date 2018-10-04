---
title: Batch di istruzioni | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa97baae4ad6331193cab16ae2609212753c5be0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051937"
---
# <a name="batches-of-statements"></a>Batch di istruzioni
  Un batch di [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzioni contiene due o più istruzioni, separate da punto e virgola (;), incorporato in una singola stringa passata a **SQLExecDirect** oppure [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360). Esempio:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 I batch possono essere più efficienti rispetto all'invio separato delle istruzioni in quanto il traffico di rete viene spesso ridotto. Uso [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) per posizionarsi sul set al termine con il set di risultati corrente di risultati successivo.  
  
 I batch possono essere sempre utilizzati quando gli attributi del cursore ODBC sono impostati sui valori predefiniti di un cursore forward only in sola lettura con dimensioni del set di righe pari a 1.  
  
 Se un batch viene eseguito quando si utilizzano cursori del server in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], questi ultimi vengono convertiti implicitamente in set di risultati predefiniti. **SQLExecDirect** oppure **SQLExecute** restituisce SQL_SUCCESS_WITH_INFO, mentre una chiamata al **SQLGetDiagRec** restituisce:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di istruzioni &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
