---
title: SQLFetchScroll | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ece42f98419e884d5458959112a0089b0c441ae
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLFetchScroll** restituisce un set di righe di dati per l'applicazione. Le dimensioni del set di righe vengono impostate utilizzando [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta tutte le istruzioni fetch definito (ad esempio SQL_FETCH_RELATIVE) con le limitazioni seguenti:  
  
-   Se per l'istruzione è definito un cursore forward-only, è necessario specificare SQL_FETCH_NEXT e qualsiasi tentativo di recupero effettuato con altre modalità comporterà la restituzione di un errore.  
  
-   SQL_FETCH_BOOKMARK è supportato solo per i cursori statici e gestiti da keyset.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Supporto di SQLFetchScroll per le caratteristiche avanzate di data e ora  
 Valori di colonna di risultati dei tipi di data/ora vengono convertiti come descritto in [le conversioni da SQL a C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Per ulteriori informazioni, vedere [data e ora miglioramenti &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Supporto SQLFetchScroll per i tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLFetchScroll** supporta i tipi CLR grandi dimensioni definito dall'utente (UDT). Per ulteriori informazioni, vedere [Large CLR User-Defined tipi &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLFetchScroll](http://go.microsoft.com/fwlink/?LinkId=59343)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
