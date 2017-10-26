---
title: Funzione SQLSetDriverConnectInfo | Documenti Microsoft
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
- SQLSetDriverConnectInfo function [ODBC]
ms.assetid: bfd4dfc2-fbca-4ef3-81e5-2706f2389256
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 970fec5219fed803439fc05c3f6fe56a300617f0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetdriverconnectinfo-function"></a>SQLSetDriverConnectInfo (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 3,81 conformità: ODBC  
  
 **Riepilogo**  
 **SQLSetDriverConnectInfo** utilizzato per impostare la stringa di connessione nel token di informazioni di connessione per un'applicazione **SQLDriverConnect** chiamare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>Argomenti  
 *TokenHandle*  
 [Input] Handle del token.  
  
 *InConnectionString*  
 [Input] Una stringa di connessione completa (vedere la sintassi "Commenti" in [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)), una stringa di connessione o una stringa vuota.  
  
 *StringLength1*  
 [Input] Lunghezza di **InConnectionString*, in caratteri, se la stringa è Unicode, o byte se stringa ANSI o DBCS.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Uguale a [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) correlati a qualsiasi errore di convalida dell'input, ad eccezione del fatto che la gestione Driver utilizzerà un **HandleType** di SQL_HANDLE_DBC_INFO_TOKEN e **gestire** di *hDbcInfoToken*.  
  
## <a name="remarks"></a>Osservazioni  
 Ogni volta che un driver restituisce SQL_ERROR o SQL_INVALID_HANDLE, gestione Driver restituisce l'errore all'applicazione (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) o [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Ogni volta che un driver restituisce SQL_SUCCESS_WITH_INFO, gestione Driver otterrà le informazioni di diagnostica da *hDbcInfoToken*e restituisce SQL_SUCCESS_WITH_INFO all'applicazione in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)e [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Le applicazioni non devono chiamare direttamente questa funzione. Un driver ODBC che supporta il pool di connessioni compatibile con il driver deve implementare questa funzione.  
  
 Includere sqlspi.h per lo sviluppo di driver ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Il pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Sviluppo di un Driver ODBC consapevolezza Pool di connessioni](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)

