---
title: SQLSetEnvAttr | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 84564e9e6007e6e5e2f97601061e0dfe51b19d41
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [riferimento per programmatori ODBC](http://go.microsoft.com/fwlink/?LinkId=45250) definisce l'interpretano di driver ODBC di **SQLSetEnvAttr** attributo specifiche dalle applicazioni scritte in ODBC 2. *x* o ODBC 3. *x* API. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client è conforme a tali regole.  
  
 Uno degli attributi controllati da **SQLSetEnvAttr** è se il pool di connessioni viene utilizzato. Se il pool di connessioni viene utilizzato con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client, il *DriverCompletion* parametro deve essere impostato su SQL_DRIVER_NOPROMPT quando ci si connette con [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) o **SQLConnect**.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLSetEnvAttr-funzione](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
