---
title: Liberare un Handle di istruzione | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9c82817d8c721777cdee8b23b7d199dd9faad4c2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="freeing-a-statement-handle"></a>Rilascio di un handle di istruzione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  È più efficiente riutilizzare handle di istruzione anziché eliminarli e allocarne di nuovi. Prima di eseguire una nuova istruzione SQL su un handle di istruzione, le applicazioni devono verificare che le impostazioni delle istruzioni correnti siano corrette. Tra le impostazioni sono inclusi gli attributi di istruzione, le associazioni di parametri e le associazioni dei set di risultati. In genere, i parametri e il risultato consente di impostare l'istruzione SQL precedente deve essere annullata chiamando [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) opzioni SQL_RESET_PARAMS e SQL_UNBIND e quindi nuovamente associato per la nuova istruzione SQL.  
  
 Quando l'applicazione ha terminato di utilizzare l'istruzione, chiama [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) per liberare l'istruzione. Si noti che **SQLDisconnect** libera automaticamente tutte le istruzioni in una connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query &#40; ODBC &#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
