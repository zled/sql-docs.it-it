---
title: Modalità asincrona e SQLCancel | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3f6f0e96ff0344a084b84098339687374ba18335
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32949906"
---
# <a name="creating-a-driver-application---asynchronous-mode-and-sqlcancel"></a>Creazione di un'applicazione Driver - modalità asincrona e SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Alcune funzioni ODBC possono essere utilizzate in modo sincrono o in modo asincrono. Le operazioni asincrone possono essere abilitate per un handle di istruzione o per un handle di connessione. Se l'opzione viene impostata per un handle di connessione, sarà valida per tutti gli handle di istruzione nell'handle di connessione. Per abilitare o disabilitare le operazioni asincrone vengono utilizzate le istruzioni seguenti:  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 Quando una funzione ODBC viene chiamata in modalità sincrona, il driver restituisce il controllo all'applicazione solo dopo la notifica del completamento del comando da parte del server.  
  
 In modalità asincrona, il driver restituisce immediatamente il controllo all'applicazione, anche prima dell'invio del comando al server. Il driver imposta il codice restituito su SQL_STILL_EXECUTING. È quindi possibile eseguire altre operazioni.  
  
 Durante il controllo del completamento del comando, viene effettuata la stessa chiamata di funzione con gli stessi parametri al driver. Se il driver non riceve una risposta dal server, restituirà nuovamente SQL_STILL_EXECUTING. È necessario controllare periodicamente il comando finché il codice restituito non sia diverso da SQL_STILL_EXECUTING. Quando si ottiene un codice restituito diverso, anche SQL_ERROR, è possibile determinare che il comando è stato completato.  
  
 A volte un comando rimane in attesa per molto tempo. Se l'applicazione deve annullare il comando senza attendere una risposta, è possibile eseguire una chiamata **SQLCancel** con la stessa istruzione handle del comando in attesa. Si tratta dell'unica volta **SQLCancel** deve essere utilizzato. Alcuni programmatori utilizzano **SQLCancel** durante l'elaborazione in attraverso il risultato di un set e si desidera annullare il resto del set di risultati. [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) oppure [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) deve essere utilizzato per annullare il resto di un set di risultati in attesa, non **SQLCancel**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'applicazione Driver ODBC di SQL Server Native Client](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
  
