---
title: Funzione SQLSetConnectAttrForDbcInfo | Documenti Microsoft
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
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3ffe1bf224a28d7ff1151033576abcd5f10f56ed
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 3,81 conformità: ODBC  
  
 **Riepilogo**  
 **SQLSetConnectAttrForDbcInfo** equivale **SQLSetConnectAttr**, ma l'attributo viene impostato sul token di informazioni di connessione anziché nell'handle di connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Argomenti  
 *hDbcInfoToken*  
 [Input] Handle del token.  
  
 *Attribute*  
 [Input] Attributo da impostare. L'elenco di attributi validi è specifico di driver e le stesse di [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Input] Puntatore al valore da associare a *attributo*. A seconda del valore di *attributo*, *ValuePtr* sarà un valore intero senza segno a 32 bit o farà riferimento a una stringa di caratteri con terminazione null. Si noti che se il *attributo* argomento è un valore specifico del driver, il valore in *ValuePtr* potrebbe essere un intero con segno.  
  
 *StringLength*  
 [Input] Se *attributo* è un attributo basato su ODBC e *ValuePtr* punta a una stringa di caratteri o di un buffer binario, la lunghezza di questo argomento deve essere **ValuePtr*. Per i dati di stringa di caratteri, questo argomento deve contenere il numero di byte nella stringa.  
  
 Se *attributo* è un attributo basato su ODBC e *ValuePtr* è un numero intero, *StringLength* viene ignorato.  
  
 Se *attributo* è un attributo definito dal driver, l'applicazione indica la natura dell'attributo al Driver Manager impostando il *StringLength* argomento. *StringLength* può avere i valori seguenti:  
  
-   Se *ValuePtr* è un puntatore a una stringa di caratteri, quindi *StringLength* è la lunghezza della stringa o SQL_NTS.  
  
-   Se *ValuePtr* è un puntatore a un buffer binario, quindi viene visualizzato il risultato di SQL_LEN_BINARY_ATTR (*lunghezza*) (macro) in *StringLength*. In questo modo un valore negativo in *StringLength*.  
  
-   Se *ValuePtr* è un puntatore a un valore diverso da una stringa di caratteri o una stringa binaria, quindi *StringLength* deve avere il valore SQL_IS_POINTER.  
  
-   Se *ValuePtr* contiene un valore di lunghezza fissa, quindi *StringLength* è SQL_IS_INTEGER o SQL_IS_UINTEGER, come appropriato.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Uguale a [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), ad eccezione del fatto che la gestione Driver utilizzerà un **HandleType** di SQL_HANDLE_DBC_INFO_TOKEN e **gestire** di *hDbcInfoToken *.  
  
## <a name="remarks"></a>Osservazioni  
 **SQLSetConnectAttrForDbcInfo** equivale **SQLSetConnectAttr**, ma viene impostato l'attributo per il token di informazioni di connessione, anziché dell'handle di connessione. Ad esempio, se **SQLSetConnectAttr** non riconosce un attributo, **SQLSetConnectAttrForDbcInfo** deve restituire anche SQL_ERROR per l'attributo.  
  
 Ogni volta che i driver restituisce SQL_ERROR o SQL_INVALID_HANDLE, il driver deve ignorare questo attributo per calcolare l'ID del pool. Inoltre, gestione Driver otterrà le informazioni di diagnostica da *hDbcInfoToken*e restituisce SQL_SUCCESS_WITH_INFO all'applicazione in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) e [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Pertanto, un'applicazione può recuperare informazioni dettagliate sui motivi per cui non è possibile impostare alcuni attributi.  
  
 Le applicazioni non devono chiamare direttamente questa funzione. Un driver ODBC che supporta il pool di connessioni compatibile con il driver deve implementare questa funzione.  
  
 Includere sqlspi.h per lo sviluppo di driver ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Il pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Sviluppo di un Driver ODBC consapevolezza Pool di connessioni](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
