---
title: Funzione SQLSetConnectAttrForDbcInfo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 990c0074d7408d3b200bbff1ba1d43a46e77fd1e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 3,81 conformità: ODBC  
  
 **Riepilogo**  
 **SQLSetConnectAttrForDbcInfo** corrisponde al **SQLSetConnectAttr**, ma l'attributo viene impostato sul token di informazioni di connessione anziché nell'handle di connessione.  
  
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
  
 *Attributo*  
 [Input] Attributo da impostare. L'elenco di attributi validi è specifico di driver e le stesse di [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Input] Puntatore al valore da associare a *attributo*. A seconda del valore di *attributo*, *ValuePtr* sarà un valore intero senza segno a 32 bit o farà riferimento a una stringa di caratteri con terminazione null. Si noti che se il *attributo* argomento è un valore specifico del driver, il valore in *ValuePtr* potrebbe essere un intero con segno.  
  
 *stringLength*  
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
 Uguale a [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), ad eccezione del fatto che la gestione Driver utilizzerà un **HandleType** di SQL_HANDLE_DBC_INFO_TOKEN e **gestire** di *hDbcInfoToken* .  
  
## <a name="remarks"></a>Osservazioni  
 **SQLSetConnectAttrForDbcInfo** corrisponde al **SQLSetConnectAttr**, ma viene impostato l'attributo per il token di informazioni di connessione, anziché sull'handle di connessione. Ad esempio, se **SQLSetConnectAttr** non riconosce un attributo, **SQLSetConnectAttrForDbcInfo** deve restituire anche SQL_ERROR per l'attributo.  
  
 Ogni volta che i driver restituisce SQL_ERROR o SQL_INVALID_HANDLE, il driver deve ignorare questo attributo per calcolare l'ID del pool. Inoltre, gestione Driver otterrà le informazioni di diagnostica da *hDbcInfoToken*e restituisce SQL_SUCCESS_WITH_INFO all'applicazione in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) e [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Pertanto, un'applicazione può recuperare informazioni dettagliate sui motivi per cui non è possibile impostare alcuni attributi.  
  
 Le applicazioni non devono chiamare direttamente questa funzione. Un driver ODBC che supporta il pool di connessioni compatibile con il driver deve implementare questa funzione.  
  
 Includere sqlspi.h per lo sviluppo di driver ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Sviluppo del rilevamento di pool di connessioni in un driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
