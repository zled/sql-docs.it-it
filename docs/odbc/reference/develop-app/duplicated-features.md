---
title: "Duplicare funzionalità | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5b27da2aac2c42987f6eeaba4f104b647912df0d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="duplicated-features"></a>Funzionalità di duplicati
Il seguente ODBC 2. *x* funzioni sono state duplicate da ODBC 3. *x* funzioni. Di conseguenza, l'API ODBC 2. *x* funzioni sono deprecate in ODBC 3. *x*. ODBC 3. *x* funzioni vengono dette funzioni di sostituzione.  
  
 Quando un'applicazione utilizza un deprecata di ODBC 2. *x* funzione e il driver sottostante è un'applicazione ODBC 3. *x* driver, Driver Manager esegue il mapping di chiamata di funzione alla funzione di sostituzione corrispondente. L'unica eccezione a questa regola è **SQLExtendedFetch**. (Vedere la nota alla fine della tabella seguente). Per ulteriori informazioni su tali mapping, vedere [Mapping funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
 Quando un'applicazione utilizza una funzione di sostituzione e il driver sottostante è un ODBC 2. *x* driver, Driver Manager esegue il mapping di chiamata di funzione alla funzione deprecata.  
  
|ODBC 2. *x* (funzione)|ODBC 3. *x* (funzione)|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLExtendedFetch**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**, **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] la funzione **SQLExtendedFetch** è una funzionalità duplicate; **SQLFetchScroll** fornisce la stessa funzionalità in ODBC 3. *x*. Tuttavia, gestione Driver non esegue il mapping **SQLExtendedFetch** a **SQLFetchScroll** quando in un'applicazione ODBC 3. *x* driver. Per ulteriori informazioni, vedere [the Driver Manager cosa](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti. Esegue il mapping di gestione Driver **SQLFetchScroll** a **SQLExtendedFetch** quando si passa un 2 di ODBC. *x* driver.  
  
> [!NOTE]  
>  La funzione **SQLBindParam** è un caso speciale. **SQLBindParam** è una funzionalità duplicate. Non è un'API ODBC 2*x* funzione, ma una funzione che è presente negli standard Open Group e ISO. Le funzionalità offerte da questa funzione sono completamente sostituita da quello del **SQLBindParameter**. Di conseguenza, il Driver Manager esegue il mapping di una chiamata a **SQLBindParam** a **SQLBindParameter** quando il driver sottostante è un'applicazione ODBC 3. *x* driver. Tuttavia, quando il driver sottostante è un ODBC 2*x* driver, Driver Manager non esegue il mapping.
