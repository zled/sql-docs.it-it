---
title: SQLEndTran | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc7ad74e92154dd9100836ab01361826bdde05ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47630259"
---
# <a name="sqlendtran"></a>SQLEndTran
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Per impostazione predefinita, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client chiude cursore associato dell'istruzione quando **SQLEndTran** esegue il commit o il rollback di un'operazione. I cursori del server vengono chiusi a meno che non siano statici. Quando **SQLEndTran** esegue il commit o il rollback di un'operazione, il comportamento del cursore associato dell'istruzione è determinato dal valore dell'attributo specifiche del driver di connessione ODBC SQL_COPT_SS_PRESERVE_CURSORS, imposta [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Funzione SQLEndTran](http://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
