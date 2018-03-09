---
title: SQLTables | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3f7a8146030e1001f6d3aa06b0215f95bd1885f1
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="sqltables"></a>SQLTables
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLTables può essere eseguito in un cursore server statico. Un tentativo di eseguire SQLTables su un cursore aggiornabile (dinamico o keyset) restituirà SQL_SUCCESS_WITH_INFO, che indica che il tipo di cursore è stato modificato.  
  
 SQLTables report delle tabelle di tutti i database quando il *CatalogName* parametro è SQL_ALL_CATALOGS e tutti gli altri parametri contengono i valori predefiniti (puntatori NULL).  
  
 Per segnalare i cataloghi disponibili, schemi e tipi di tabella, SQLTables utilizza stringhe vuote (puntatori di byte di lunghezza zero). Le stringhe vuote non sono valori predefiniti (puntatori NULL).  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome composto da due parti per il *CatalogName* parametro: *linked_server_name*.  
  
 SQLTables restituisce informazioni su qualsiasi tabella il cui nome corrisponde *TableName* e di proprietà dell'utente corrente.  
  
## <a name="sqltables-and-table-valued-parameters"></a>SQLTables e parametri con valori di tabella  
 Quando l'attributo dell'istruzione SQL_SOPT_SS_NAME_SCOPE è impostato sul valore SQL_SS_NAME_SCOPE_TABLE_TYPE, anziché il valore predefinito di SQL_SS_NAME_SCOPE_TABLE, SQLTables restituisce informazioni sui tipi di tabella. Il valore TABLE_TYPE restituito per un tipo di tabella nella colonna 4 del set di risultati restituito da SQLTables è il tipo di tabella. Per ulteriori informazioni su SQL_SOPT_SS_NAME_SCOPE, vedere [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Tabelle, viste e sinonimi condividono uno spazio dei nomi comune che è distinto dallo spazio dei nomi utilizzato dai tipi di tabella. Anche se non è possibile avere una tabella e una vista con lo stesso nome, è possibile avere una tabella e un tipo di tabella con lo stesso nome nello stesso catalogo e schema.  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [parametri con valori di tabella &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="example"></a>Esempio  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLTables](http://go.microsoft.com/fwlink/?LinkId=59374)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
