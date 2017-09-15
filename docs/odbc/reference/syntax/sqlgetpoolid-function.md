---
title: Funzione SQLGetPoolID | Documenti Microsoft
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
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8db01749cf58e34c59294367b3e24105906b635
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 3,81 conformità: ODBC  
  
 **Riepilogo**  
 **SQLGetPoolID** recupera l'ID del pool.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Argomenti  
 *hDbcInfoToken*  
 [Input] Handle del token che contiene tutte le informazioni di connessione.  
  
 *pPoolID*  
 [Output] L'ID del pool, viene utilizzato per identificare un set di connessioni che possono essere usati indifferentemente (possibilmente che richiedono una reimpostazione aggiuntiva).  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetPoolID** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, gestione Driver utilizzerà un **HandleType** di SQL_HANDLE_DBC_INFO_TOKEN e **gestire** di *hDbcInfoToken*.  
  
## <a name="remarks"></a>Osservazioni  
 **SQLGetPoolID** viene utilizzata per ottenere l'ID del pool in base a un insieme di informazioni di connessione (da **SQLSetConnectAttrForDbcInfo**, **SQLSetDriverConnectInfo**, e ** SQLSetConnectInfo**). Questo pool di ID viene utilizzato per identificare un set di connessioni che possono essere usati indifferentemente (possibilmente che richiedono una reimpostazione aggiuntiva). L'ID del pool da utilizzare per identificare il pool di connessioni per il gruppo di connessioni.  
  
 Ogni volta che un driver restituisce SQL_ERROR o SQL_INVALID_HANDLE, gestione Driver restituisce l'errore all'applicazione (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) o [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Ogni volta che un driver restituisce SQL_SUCCESS_WITH_INFO, gestione Driver otterrà le informazioni di diagnostica da *hDbcInfoToken*e restituisce SQL_SUCCESS_WITH_INFO all'applicazione in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)e [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Le applicazioni non devono chiamare direttamente questa funzione. Un driver ODBC che supporta il pool di connessioni compatibile con il driver deve implementare questa funzione.  
  
 Includere sqlspi.h per lo sviluppo di driver ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Il pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Sviluppo di un Driver ODBC consapevolezza Pool di connessioni](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
