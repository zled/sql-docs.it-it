---
title: SQLFetchScroll | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3b4c66991e69e9bdb8ca90d76aa81c5069c84f57
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169414"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
  **SQLFetchScroll** restituisce un set di righe di dati all'applicazione. Le dimensioni del set di righe vengono impostate utilizzando [SQLSetStmtAttr](sqlsetstmtattr.md). Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta tutte le istruzioni fetch definito (ad esempio SQL_FETCH_RELATIVE) con le limitazioni seguenti:  
  
-   Se per l'istruzione è definito un cursore forward-only, è necessario specificare SQL_FETCH_NEXT e qualsiasi tentativo di recupero effettuato con altre modalità comporterà la restituzione di un errore.  
  
-   SQL_FETCH_BOOKMARK è supportato solo per i cursori statici e gestiti da keyset.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Supporto di SQLFetchScroll per le caratteristiche avanzate di data e ora  
 I valori di colonna di risultati dei tipi data/ora vengono convertiti come descritto in [le conversioni da SQL a C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Per altre informazioni, vedere [data e ora miglioramenti &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Supporto SQLFetchScroll per i tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLFetchScroll** supporta grandi CLR tipi definiti dall'utente (UDT). Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLFetchScroll-funzione](http://go.microsoft.com/fwlink/?LinkId=59343)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  