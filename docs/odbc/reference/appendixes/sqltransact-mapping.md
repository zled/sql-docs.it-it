---
title: Mapping SQLTransact | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 817e4115b1e84ad099a0eb8b7f586af506742b9b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqltransact-mapping"></a>Mapping di SQLTransact
**SQLTransact** è ora sostituita dalla **SQLEndTran**. La differenza principale tra le due funzioni è che **SQLEndTran** contiene un argomento *HandleType*, che consente di specificare l'ambito di lavoro da eseguire. Il *HandleType* argomento può specificare l'ambiente o l'handle di connessione. La seguente chiamata al **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 è stato eseguito il mapping a  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Se *ConnectionHandle* non è uguale a SQL_NULL_HDBC. Il *ConnectionHandle* argomento è impostato sul valore di *hdbc*.  
  
 **SQL_Transact** viene mappato a  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Se *ConnectionHandle* è uguale a SQL_NULL_HDBC. Il *EnvironmentHandle* argomento è impostato sul valore di *henv*.  
  
 In entrambi i casi precedenti, il *CompletionType* argomento è impostato sullo stesso valore di *fType*.
