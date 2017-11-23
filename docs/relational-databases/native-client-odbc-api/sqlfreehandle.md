---
title: SQLFreeHandle | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e8561734f25fafdd1f97290cf192960ad9f87bef
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In modalità di commit manuale, la chiamata **SQLFreeHandle** in un'istruzione handle con una transazione aperta provoca un rollback delle modifiche in sospeso per il database. La chiamata **SQLFreeHandle** in un'istruzione handle sempre chiude tutti i cursori aperti ed elimina i risultati in sospeso, liberando tutte le risorse associate all'handle di istruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLFreeHandle-funzione](http://go.microsoft.com/fwlink/?LinkId=59345)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
