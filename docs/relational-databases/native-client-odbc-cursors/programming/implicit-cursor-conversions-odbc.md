---
title: Conversioni implicite dei cursori (ODBC) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1f2e8c6ced47894e6e8737641eda36aa33e7d22
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="implicit-cursor-conversions-odbc"></a>Conversioni implicite dei cursori (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Le applicazioni possono richiedere un tipo di cursore tramite [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) e quindi eseguire un'istruzione SQL che non è supportata dai cursori server del tipo richiesto. Una chiamata a **SQLExecute** o **SQLExecDirect** restituisce SQL_SUCCESS_WITH_INFO e **SQLGetDiagRec** restituisce:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 L'applicazione può determinare il tipo di cursore viene ora utilizzato chiamando **SQLGetStmtOption** impostato su SQL_CURSOR_TYPE. La conversione del tipo di cursore viene applicata a una sola istruzione. Alla successiva **SQLExecDirect** o **SQLExecute** verrà eseguita utilizzando le impostazioni del cursore istruzione originale.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla programmazione dei cursori &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
