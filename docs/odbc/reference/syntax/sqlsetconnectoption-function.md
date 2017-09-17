---
title: Funzione SQLSetConnectOption | Documenti Microsoft
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
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b5499852e3574c597e3a424347b22021d0887ca9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectoption-function"></a>Funzione SQLSetConnectOption
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: deprecato  
  
 **Riepilogo**  
 In ODBC 3*x*, la funzione ODBC 2.0 **SQLSetConnectOption** è stata sostituita da **SQLSetConnectAttr**. Per ulteriori informazioni, vedere [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]  
>  Per ulteriori informazioni su cosa the Driver Manager esegue il mapping di questa funzione per quando un ODBC 2*x* applicazione funziona con un'applicazione ODBC 3*x* driver, vedere [Mapping funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Osservazioni  
 Vedere [informazioni ODBC a 64 Bit](../../../odbc/reference/odbc-64-bit-information.md), se l'applicazione verrà eseguita in un sistema operativo a 64 bit.  
  
> [!NOTE]  
>  L'attributo SQL_ASYNC_DBC_FUNCTION_ENABLE introdotte in ODBC 3.8 non è supportato da **SQLSetConnectOption**. Applicazioni che utilizzano l'operazione asincrona su handle di connessione devono utilizzare **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
