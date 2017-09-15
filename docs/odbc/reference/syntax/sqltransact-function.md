---
title: Funzione SQLTransact | Documenti Microsoft
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
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1af98fb53aadf7ea6bb2253041c951481a019027
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqltransact-function"></a>SQLTransact (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: deprecato  
  
 **Riepilogo**  
 In ODBC 3. *x*, ODBC 2*x* funzione **SQLTransact** è stata sostituita da **SQLEndTran**. Per ulteriori informazioni, vedere [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  L'attributo SQL_ASYNC_DBC_FUNCTION_ENABLE, che è stata introdotta in ODBC 3.8, non è supportato da **SQLTransact**. Un'operazione asincrona su un handle di connessione utilizzando le applicazioni devono utilizzare **SQLEndTran**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
