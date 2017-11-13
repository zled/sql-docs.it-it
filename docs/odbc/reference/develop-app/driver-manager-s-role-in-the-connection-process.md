---
title: Gestione driver &#39; s ruolo nel processo di connessione | Documenti Microsoft
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
- driver manager [ODBC], role in connection process
- connecting to data source [ODBC], driver manager
- connecting to driver [ODBC], driver manager
- ODBC driver manager [ODBC]
ms.assetid: 77c05630-5a8b-467d-b80e-c705dc06d601
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 32a6629892ad9667b7d56a6bb6752c68001dddc9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="driver-manager39s-role-in-the-connection-process"></a>Gestione driver &#39; s ruolo nel processo di connessione
Tenere presente che le applicazioni non chiamare direttamente le funzioni di driver. Invece che chiamano le funzioni di gestione Driver con lo stesso nome e di gestione Driver chiama le funzioni di driver. In genere, ciò si verifica quasi immediatamente. Ad esempio, l'applicazione chiama **SQLExecute** dopo alcuni controlli degli errori e gestione Driver, Driver Manager chiama **SQLExecute** nel driver.  
  
 Il processo di connessione è diverso. Quando l'applicazione chiama **SQLAllocHandle** con le opzioni impostato su SQL_HANDLE_ENV e impostato su SQL_HANDLE_DBC, la funzione esegue l'allocazione di handle solo in Gestione Driver. Gestione Driver non chiama questa funzione nel driver perché non conoscere il driver da chiamare. Analogamente, se l'applicazione passa l'handle di una connessione non è connessa al **SQLSetConnectAttr** o **SQLGetConnectAttr**, solo il Driver Manager esegue la funzione. Archivia o ottiene il valore dell'attributo dalla connessione gestisce e restituisce SQLSTATE 08003 (connessione non aperta) durante il recupero di un valore per un attributo non è stato impostato e per quale ODBC non definisce un valore predefinito.  
  
 Quando l'applicazione chiama **SQLConnect**, **SQLDriverConnect**, o **SQLBrowseConnect**, gestione Driver determina innanzitutto i driver da utilizzare. Quindi una verifica per determinare se un driver è attualmente caricato per la connessione:  
  
-   Se per la connessione non viene caricato alcun driver, Driver Manager controlla se viene caricato il driver specificato in un'altra connessione nello stesso ambiente. Se non, gestione Driver carica il driver in cui la connessione e chiama **SQLAllocHandle** nel driver con l'opzione impostato su SQL_HANDLE_ENV.  
  
     Gestione Driver chiama quindi **SQLAllocHandle** nel driver con l'opzione impostato su SQL_HANDLE_DBC o meno è stato appena caricato. Se l'applicazione di impostare gli attributi di connessione, gestione Driver chiama **SQLSetConnectAttr** nel driver; se si verifica un errore, la funzione di connessione di gestione Driver restituisce SQLSTATE IM006 (patente  **La funzione SQLSetConnectAttr** non riuscita). Infine, gestione Driver chiama la funzione di connessione nel driver.  
  
-   Se il driver specificato viene caricato per la connessione, gestione Driver chiama la funzione di connessione nel driver. In questo caso, il driver deve assicurarsi che tutti gli attributi di connessione per la connessione mantengono le impostazioni correnti.  
  
-   Se un altro driver viene caricato per la connessione, gestione Driver chiama **SQLFreeHandle** nel driver per liberare la connessione. Se non sono presenti altre connessioni che utilizzano il driver, Driver Manager chiamerà **SQLFreeHandle** nel driver per liberare l'ambiente e consente di scaricare il driver. Gestione Driver esegue quindi le stesse operazioni quando non viene caricato un driver per la connessione.  
  
 Gestione Driver bloccherà l'handle di ambiente (*henv*) prima di chiamare un driver **SQLAllocHandle** e **SQLFreeHandle** quando *HandleType* è impostato su **impostato su SQL_HANDLE_DBC**.  
  
 Quando l'applicazione chiama **SQLDisconnect**, le chiamate di gestione Driver **SQLDisconnect** nel driver. Tuttavia, lascia il driver caricato nel caso in cui l'applicazione si riconnette al driver. Quando l'applicazione chiama **SQLFreeHandle** con l'opzione impostato su SQL_HANDLE_DBC, gestione Driver chiama **SQLFreeHandle** nel driver. Se il driver non viene utilizzato da altre connessioni, gestione Driver chiama **SQLFreeHandle** nel driver con l'impostato su SQL_HANDLE_ENV opzione e scarica il driver.

