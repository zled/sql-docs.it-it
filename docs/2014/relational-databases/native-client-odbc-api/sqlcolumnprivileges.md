---
title: SQLColumnPrivileges | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6462213fddd646c1461f0975dc89b151c192de3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425730"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **SQLColumnPrivileges** restituisce SQL_SUCCESS se esistono o meno valori per il*CatalogName*, *SchemaName*, *TableName*, o  *ColumnName* parametri. **SQLFetch** restituisce SQL_NO_DATA quando in questi parametri vengono utilizzati valori non validi.  
  
 **SQLColumnPrivileges** può essere eseguito su un cursore server statico. Un tentativo di eseguire **SQLColumnPrivileges** su un cursore aggiornabile (dinamico o keyset) restituirà SQL_SUCCESS_WITH_INFO che indica che il tipo di cursore è stato modificato.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome in due parti per il *CatalogName* parametro: *linked_server_name*.  
  
## <a name="see-also"></a>Vedere anche  
 [Sqlcolumnprivileges-funzione](http://go.microsoft.com/fwlink/?LinkId=59335)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
