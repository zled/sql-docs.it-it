---
title: Funzione SQLSetConnectInfo | Documenti Microsoft
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
- SQLSetConnectInfo function [ODBC]
ms.assetid: 0782a1c3-c5d1-499b-a8ba-134162db9990
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e4c974a8cf4bb46f955ec8f2bae0a766f58f692
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectinfo-function"></a>SQLSetConnectInfo (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 3,81 conformità: ODBC  
  
 **Riepilogo**  
 **SQLSetConnectInfo** utilizzato per impostare l'origine dati, l'ID utente e password nel token di informazioni di connessione per un'applicazione [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) chiamare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SQLRETURN  SQLSetConnectInfo(  
                SQLHDBC_INFO_TOKEN   TokenHandle,  
                WCHAR *              ServerName,  
                SQLSMALLINT          NameLength1,  
                WCHAR *              UserName,  
                SQLSMALLINT          NameLength2,  
                WCHAR *              Authentication,  
                SQLSMALLINT          NameLength3 );  
```  
  
## <a name="arguments"></a>Argomenti  
 *TokenHandle*  
 [Input] Handle del token.  
  
 *ServerName*  
 [Input] Nome dell'origine dati. I dati potrebbero trovarsi nello stesso computer del programma, o in un altro computer in un punto qualsiasi in una rete. Per informazioni su come un'applicazione sceglie un'origine dati, vedere [scelta di un'origine dati o il Driver](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Input] Lunghezza di **ServerName* in caratteri.  
  
 *UserName*  
 [Input] Identificatore dell'utente.  
  
 *NameLength2*  
 [Input] Lunghezza di **UserName* in caratteri.  
  
 *Autenticazione*  
 [Input] Stringa di autenticazione (in genere la password).  
  
 *NameLength3*  
 [Input] Lunghezza di **autenticazione* in caratteri.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Uguale a [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) per gli errori di convalida di input, ad eccezione del fatto che la gestione Driver utilizzerà un **HandleType** di SQL_HANDLE_DBC_INFO_TOKEN e **gestire** di *hDbcInfoToken*.  
  
## <a name="remarks"></a>Osservazioni  
 Ogni volta che un driver restituisce SQL_ERROR o SQL_INVALID_HANDLE, gestione Driver restituisce l'errore all'applicazione (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) o [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Ogni volta che un driver restituisce SQL_SUCCESS_WITH_INFO, gestione Driver otterrà le informazioni di diagnostica da *hDbcInfoToken*e restituisce SQL_SUCCESS_WITH_INFO all'applicazione in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)e [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Le applicazioni non devono chiamare direttamente questa funzione. Un driver ODBC che supporta il pool di connessioni compatibile con il driver deve implementare questa funzione.  
  
 Includere sqlspi.h per lo sviluppo di driver ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Il pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Sviluppo di un Driver ODBC consapevolezza Pool di connessioni](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
