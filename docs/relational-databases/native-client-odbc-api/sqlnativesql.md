---
title: SQLNativeSql | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2c32f7289dd6a57f142ca915cf0e921777152729
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlnativesql"></a>SQLNativeSql
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client soddisfa richieste di **SQLNativeSql** senza visitare il server. La funzione verifica in modo efficiente la sintassi di istruzioni SQL. Il controllo della sintassi non determina se gli identificatori o i risultati di espressioni nelle istruzioni SQL sono validi. È possibile che l'esecuzione del formato SQL nativo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito da **SQLNativeSql** non riesca.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLNativeSql](http://go.microsoft.com/fwlink/?LinkID=59358)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
