---
title: Concorrenza dei cursori (ODBC) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fc203adcfde52484c013a4cda0483d95511e1cd9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="cursor-concurrency-odbc"></a>Concorrenza dei cursori (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Le operazioni dei cursori, come i tipi di cursore, sono influenzate dalle opzioni di concorrenza impostate dall'applicazione. Le opzioni di concorrenza vengono impostate utilizzando l'opzione SQL_ATTR_CONCURRENCY di [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). I tipi di concorrenza sono i seguenti:  
  
-   Di sola lettura (SQL_CONCUR_READONLY)  
  
-   Valori (SQL_CONCUR_VALUES)  
  
-   Versione di riga (SQL_CONCUR_ROWVER)  
  
-   Blocco (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del cursore](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
