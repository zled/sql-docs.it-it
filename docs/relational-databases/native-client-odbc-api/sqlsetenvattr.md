---
title: SQLSetEnvAttr | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b53db46db783bd55799c251d38d86d4479e7ee0f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47844409"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [riferimento per programmatori ODBC](http://go.microsoft.com/fwlink/?LinkId=45250) definisce come i driver ODBC è necessario interpretare il **SQLSetEnvAttr** attributo specifiche dalle applicazioni scritte in ODBC 2. *x* o ODBC 3. *x* API. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client è conforme a tali regole.  
  
 Uno degli attributi controllati da **SQLSetEnvAttr** se il pool di connessioni è utilizzabile. Se il pool di connessioni viene usato con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client, il *DriverCompletion* parametro deve essere impostato su SQL_DRIVER_NOPROMPT quando ci si connette con uno [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) o **SQLConnect**.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLSetEnvAttr-funzione](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
