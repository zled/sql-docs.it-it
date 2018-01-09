---
title: SQLPrimaryKeys | Documenti Microsoft
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
helpviewer_keywords: SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f8b0a3edcab4d46e2a1b8dcc4dbf5eb9a51bb45
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Una tabella può includere una o più colonne che possono essere utilizzato come identificatori di riga univoco e le tabelle create senza un vincolo PRIMARY KEY restituiscono un risultato vuoto impostato su SQLPrimaryKeys. La funzione ODBC [SQLSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md) report riga candidati identificatore per le tabelle senza chiavi primarie.  
  
 SQLPrimaryKeys restituisce SQL_SUCCESS indipendentemente dall'esistenza di valori per *CatalogName*, *SchemaName*, o *TableName* parametri. SQLFetch restituisce SQL_NO_DATA quando in questi parametri vengono utilizzati valori non validi.  
  
 SQLPrimaryKeys può essere eseguito in un cursore server statico. Un tentativo di eseguire SQLPrimaryKeys su un cursore aggiornabile (dinamico o keyset) restituirà SQL_SUCCESS_WITH_INFO, che indica che il tipo di cursore è stato modificato.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome composto da due parti per il *CatalogName* parametro: *linked_server_name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys e parametri con valori di tabella  
 Se l'attributo dell'istruzione SQL_SOPT_SS_NAME_SCOPE è impostato sul valore SQL_SS_NAME_SCOPE_TABLE_TYPE, anziché il valore predefinito di SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys restituirà informazioni sulle colonne di chiavi primarie dei tipi di tabella. Per ulteriori informazioni su SQL_SOPT_SS_NAME_SCOPE, vedere [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [parametri con valori di tabella &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLPrimaryKeys-funzione](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
