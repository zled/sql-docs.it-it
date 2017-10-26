---
title: Funzione SQLPoolConnect | Documenti Microsoft
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
- SQLPoolConnect function [ODBC]
ms.assetid: 41322737-890d-4a81-aed2-06cc3d546962
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8c0a82eecc733223442bc1cebf6da111397bca99
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlpoolconnect-function"></a>SQLPoolConnect (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.8 aderenza: ODBC  
  
 **Riepilogo**  
 **SQLPoolConnect** viene utilizzato per creare una nuova connessione se nessuna connessione nel pool può essere riutilizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SQLRETURN  SQLPoolConnect(  
                SQLHDBC              hDbc,  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              wszOutConnectString,  
                SQLSMALLINT          cchConnectStringBuffer,  
                SQLSMALLINT *        cchConnectStringLen );  
```  
  
## <a name="arguments"></a>Argomenti  
 *hDbc*  
 [Input] L'handle di connessione.  
  
 *hDbcInfoToken*  
 [Input] L'handle del token per la nuova richiesta di connessione dell'applicazione.  
  
 *wszOutConnectString*  
 [Output] Puntatore a un buffer per la stringa di connessione completata. Dopo la connessione all'origine dati di destinazione, questo buffer contiene la stringa di connessione completata. Le applicazioni è consigliabile allocare almeno 1024 caratteri per questo buffer.  
  
 Se *wszOutConnectString* è NULL, *cchConnectStringLen* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile per restituire il buffer a cui puntava *wszOutConnectString*.  
  
 *cchConnectStringBuffer*  
 [Input] Lunghezza di **wszOutConnectString* buffer, in caratteri.  
  
 *cchConnectStringLen*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di caratteri (escluso il carattere di terminazione null) disponibile per restituire \* *wszOutConnectString*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *cchConnectStringBuffer*, completare la stringa di connessione in \* *wszOutConnectString* viene troncato a *cchConnectStringBuffer* meno la lunghezza di un carattere di terminazione null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Simile a [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) per qualsiasi input di errore di convalida, ad eccezione del fatto che la gestione Driver utilizzerà un **HandleType** di SQL_HANDLE_DBC_INFO_TOKEN e **gestire** di *hDbcInfoToken*.  
  
## <a name="remarks"></a>Osservazioni  
 Gestione Driver garantisce che l'elemento padre HENV gestire di *hDbc* e *hDbcInfoToken* sono uguali.  
  
 A differenza di [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md), non esiste alcun *DriverCompletion* argomento per richiedere agli utenti di immettere le informazioni di connessione. Una finestra di dialogo di richiesta non è consentito nello scenario del pool di connessioni.  
  
 Le applicazioni non devono chiamare direttamente questa funzione. Un driver ODBC che supporta il pool di connessioni compatibile con il driver deve implementare questa funzione.  
  
 Ogni volta che un driver restituisce SQL_ERROR o SQL_INVALID_HANDLE, gestione Driver restituisce l'errore all'applicazione (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) o [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Ogni volta che un driver restituisce SQL_SUCCESS_WITH_INFO, gestione Driver otterrà le informazioni di diagnostica da *hDbcInfoToken*e restituisce SQL_SUCCESS_WITH_INFO all'applicazione in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)e [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Quando un'applicazione usa [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), *wszOutConnectString* sarà un buffer NULL (gli ultimi tre parametri verranno tutti impostati su NULL, 0, NULL). In caso contrario, il driver deve restituire la stringa di connessione di output, verrà restituita all'applicazione [funzione SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) chiamare.  
  
 Includere sqlspi.h per lo sviluppo di driver ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Il pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Sviluppo di un Driver ODBC consapevolezza Pool di connessioni](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)

