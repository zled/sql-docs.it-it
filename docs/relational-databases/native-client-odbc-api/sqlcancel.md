---
title: SQLCancel | Documenti Microsoft
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
helpviewer_keywords: SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b959ce4ef5f0eb7298f7203401fa6be6c96581d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) argomento indica che in ODBC 2. x, se un'applicazione chiama **SQLCancel** quando è viene eseguita alcuna elaborazione nell'istruzione **SQLCancel** ha lo stesso effetto  **SQLFreeStmt** con il **SQL_CLOSE** opzione; questo comportamento viene definito solo per completezza e le applicazioni devono chiamare **SQLFreeStmt** o  **SQLCloseCursor** per chiudere i cursori. Tuttavia, anche se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applicazioni Native Client imposta la versione dell'API ODBC 3.5. x o versioni successive, il **SQLCancel** funzione utilizzerà il comportamento ODBC 2. x.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
