---
title: Le transizioni di ambiente | Documenti Microsoft
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
- environment transitions [ODBC]
- transitioning states [ODBC], environment
- state transitions [ODBC], environment
ms.assetid: 9d11b1ab-f4c8-48ca-9812-8c04303f939d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 13d7b923f6fad42df791aa757d6c0349f58ad7d0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="environment-transitions"></a>Transizioni di ambiente
Gli ambienti di ODBC dispongono di tre stati seguenti.  
  
|State|Description|  
|-----------|-----------------|  
|E0|Ambiente non allocato|  
|E1|Ambiente allocato, non allocato connessione|  
|E2|Ambiente di connessione allocato allocato|  
  
 Le tabelle seguenti illustrano come ogni funzione ODBC interessa lo stato dell'ambiente.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|E1 [1]|--[4]|--[4]|  
|(QUALI) [2]|E2 [5]<br />(HY010) [6]|--[4]|  
|(QUALI) [3]|(QUALI)|--[4]|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_DBC.  
  
 [3] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC.  
  
 [4] chiamare il metodo **SQLAllocHandle** con *OutputHandlePtr* che punta a un handle valido sovrascrive tale handle. Potrebbe trattarsi di un errore di programmazione dell'applicazione.  
  
 [5] l'attributo di ambiente SQL_ATTR_ODBC_VERSION era stata impostata sull'ambiente.  
  
 [6] l'attributo di ambiente SQL_ATTR_ODBC_VERSION non fosse stato impostato nell'ambiente.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources e SQLDrivers  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(QUALI)|--[1]<br />(HY010) [2]|--[1]<br />(HY010) [2]|  
  
 [1] l'attributo di ambiente SQL_ATTR_ODBC_VERSION era stato impostato nell'ambiente.  
  
 [2] l'attributo di ambiente SQL_ATTR_ODBC_VERSION non fosse stato impostato nell'ambiente.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(QUALI) [1]|--[3]<br />(HY010) [4]|--[3]<br />(HY010) [4]|  
|(QUALI) [2]|(QUALI)|--|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_DBC.  
  
 [3] l'attributo di ambiente SQL_ATTR_ODBC_VERSION era stato impostato sull'ambiente.  
  
 [4] l'attributo di ambiente SQL_ATTR_ODBC_VERSION non fosse stato impostato nell'ambiente.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(QUALI) [1]|E0|(HY010)|  
|(QUALI) [2]|(QUALI)|--[4]<br />E1 [5]|  
|(QUALI) [3]|(QUALI)|--|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_DBC.  
  
 [3] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC.  
  
 [4] sono presenti altri handle di connessione allocato.  
  
 [5] l'handle di connessione specificato nel *gestire* è l'handle di connessione allocato solo.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField e SQLGetDiagRec  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(QUALI) [1]|--|--|  
|(QUALI) [2]|(QUALI)|--|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_ENV.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* era impostato su SQL_HANDLE_DBC, impostato su SQL_HANDLE_STMT o SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(QUALI)|--[1]<br />(HY010) [2]|--|  
  
 [1] l'attributo di ambiente SQL_ATTR_ODBC_VERSION era stato impostato nell'ambiente.  
  
 [2] l'attributo di ambiente SQL_ATTR_ODBC_VERSION non fosse stato impostato nell'ambiente.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(QUALI)|--[1]<br />(HY010) [2]|(HY011)|  
  
 [1] l'attributo di ambiente SQL_ATTR_ODBC_VERSION era stato impostato nell'ambiente.  
  
 [2] di *attributo* argomento non SQL_ATTR_ODBC_VERSION e l'attributo di ambiente SQL_ATTR_ODBC_VERSION ha non è stata impostata sull'ambiente.  
  
## <a name="all-other-odbc-functions"></a>Tutte le altre funzioni ODBC  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(QUALI)|(QUALI)|--|
