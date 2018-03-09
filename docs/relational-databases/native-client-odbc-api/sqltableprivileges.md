---
title: SQLTablePrivileges | Documenti Microsoft
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
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1b9a420498aef483f63f78e4a3c943c0201b4ea4
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="sqltableprivileges"></a>SQLTablePrivileges
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLTablePrivileges** può essere eseguito su un cursore statico. Un tentativo di eseguire **SQLTablePrivileges** su un cursore aggiornabile (dinamico o basati su keyset) restituirà SQL_SUCCESS_WITH_INFO che indica il tipo di cursore è stato modificato.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome composto da due parti per il *CatalogName* parametro: *linked_server_name*.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLTablePrivileges Function](http://go.microsoft.com/fwlink/?LinkId=59373\)   
 [Dettagli di implementazione di API ODBC](~/relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
