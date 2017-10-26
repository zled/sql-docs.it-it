---
title: Funzione SQLRemoveDefaultDataSource | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLRemoveDefaultDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDefaultDataSource
helpviewer_keywords:
- SQLRemoveDefaultDataSource function [ODBC]
ms.assetid: db803266-57df-4864-a41b-901247549c1f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ed4db21dce5cf5da5234f4906116c93f9a4ea735
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource (funzione)
**Conformità**  
 Introdotta: versione ODBC 1.0, deprecato  
  
 **Riepilogo**  
 In ODBC 3.0, il **SQLRemoveDefaultDataSource** funzione è stata sostituita da una chiamata a [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) con un *trattano* argomento di ODBC_REMOVE_DEFAULT_DSN. Se una di ODBC 2*x* programma di installazione chiama questa funzione, il programma di installazione ODBC verrà mappato al seguente **SQLConfigDataSource** chiamare:  
  
```  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```

