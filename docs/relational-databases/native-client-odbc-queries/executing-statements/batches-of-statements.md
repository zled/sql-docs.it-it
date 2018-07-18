---
title: Batch di istruzioni | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 54714f81cd4145174b82e255fde683d2cc9ef4d9
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414920"
---
# <a name="batches-of-statements"></a>Batch di istruzioni
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Un batch di [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzioni contiene due o più istruzioni, separate da punto e virgola (;), incorporato in una singola stringa passata a **SQLExecDirect** oppure [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360). Esempio:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 I batch possono essere più efficienti rispetto all'invio separato delle istruzioni in quanto il traffico di rete viene spesso ridotto. Uso [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) per posizionarsi sul set al termine con il set di risultati corrente di risultati successivo.  
  
 I batch possono essere sempre utilizzati quando gli attributi del cursore ODBC sono impostati sui valori predefiniti di un cursore forward only in sola lettura con dimensioni del set di righe pari a 1.  
  
 Se un batch viene eseguito quando si utilizzano cursori del server in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], questi ultimi vengono convertiti implicitamente in set di risultati predefiniti. **SQLExecDirect** oppure **SQLExecute** restituisce SQL_SUCCESS_WITH_INFO, mentre una chiamata al **SQLGetDiagRec** restituisce:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di istruzioni &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
