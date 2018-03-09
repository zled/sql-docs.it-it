---
title: SQLCancel | Microsoft Docs
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
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 997f0d47f29b6f45ae27dd827aa7fcdb21658223
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) argomento indica che in ODBC 2. x, se un'applicazione chiama **SQLCancel** quando è viene eseguita alcuna elaborazione nell'istruzione **SQLCancel** ha lo stesso effetto  **SQLFreeStmt** con il **SQL_CLOSE** opzione; questo comportamento viene definito solo per completezza e le applicazioni devono chiamare **SQLFreeStmt** o  **SQLCloseCursor** per chiudere i cursori. Tuttavia, anche se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applicazioni Native Client imposta la versione dell'API ODBC 3.5. x o versioni successive, il **SQLCancel** funzione utilizzerà il comportamento ODBC 2. x.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
