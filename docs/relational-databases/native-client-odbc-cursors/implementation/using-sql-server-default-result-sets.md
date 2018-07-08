---
title: Uso di set di risultati predefiniti SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9f5c1a93a64d3a087de4e07db62e1240c5c179cb
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425980"
---
# <a name="using-sql-server-default-result-sets"></a>Utilizzo dei set di risultati predefiniti di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Gli attributi predefiniti del cursore ODBC sono:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Ogni volta che questi attributi sono impostati sui valori predefiniti, il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client utilizza un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] set di risultati predefinito. I set di risultati predefiniti possono essere utilizzati per qualsiasi istruzione SQL supportata da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e rappresentano il metodo più efficiente per trasferire un intero set di risultati al client.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] introdotto il supporto per più set di risultati attivi (MARS); le applicazioni possono ora includere più di un set di risultati predefinito attivo per connessione. Per impostazione predefinita, la funzionalità MARS non è abilitata.  
  
 Prima di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], i set di risultati predefiniti non supportavano più istruzioni attive nella stessa connessione. Dopo l'esecuzione di un'istruzione SQL in una connessione, il server non accetta comandi dal client in tale connessione finché non sono state elaborate tutte le righe del set di risultati, ad eccezione di una richiesta per annullare il resto del set di risultati. Per annullare il resto di un set di risultati parzialmente elaborato, chiamare [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) oppure [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) con il *fOption* parametro impostato su SQL_CLOSE. Per completare un set di risultati parzialmente elaborato e verificare la presenza di un altro set di risultati, chiamare [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md). Se un'applicazione ODBC tenta di eseguire un comando su un handle di connessione prima di un set di risultati predefinito è stato completamente elaborato, la chiamata che genera l'errore SQL_ERROR e una chiamata a **SQLGetDiagRec** restituisce:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità di implementazione dei cursori](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
