---
title: SQLColumnPrivileges | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a37fd03742ca672d70437057bac7dbf15a913918
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLColumnPrivileges** restituisce SQL_SUCCESS indipendentemente dall'esistenza di valori per il*CatalogName*, *SchemaName*, *TableName*, o  *Nome colonna* parametri. **SQLFetch** restituisce SQL_NO_DATA quando in questi parametri vengono utilizzati valori non validi.  
  
 **SQLColumnPrivileges** può essere eseguito su un cursore server statico. Un tentativo di eseguire **SQLColumnPrivileges** su un cursore aggiornabile (dinamico o keyset) restituirà SQL_SUCCESS_WITH_INFO che indica che il tipo di cursore è stato modificato.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome composto da due parti per il *CatalogName* parametro: *linked_server_name*.  
  
## <a name="see-also"></a>Vedere anche  
 [Sqlcolumnprivileges-funzione](http://go.microsoft.com/fwlink/?LinkId=59335)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
