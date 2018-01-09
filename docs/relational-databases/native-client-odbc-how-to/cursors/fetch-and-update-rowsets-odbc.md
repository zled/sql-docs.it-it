---
title: Recuperare e aggiornare i set di righe (ODBC) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6fb264cc841109a9bb7c973560e3c285b60e7d76
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="fetch-and-update-rowsets-odbc"></a>Recuperare e aggiornare set di righe (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-fetch-and-update-rowsets"></a>Per recuperare e aggiornare set di righe  
  
1.  È possibile chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) con SQL_ROW_ARRAY_SIZE per modificare il numero di righe (R) nel set di righe.  
  
2.  Chiamare [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) o [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) per ottenere un set di righe.  
  
3.  Se si utilizzano colonne associate, utilizzare i valori dei dati e le lunghezze dei dati disponibili nei buffer delle colonne associate per il set di righe.  
  
     Se si utilizzano colonne non associate, per ogni riga chiamare [SQLSetPos](http://go.microsoft.com/fwlink/?LinkId=58407) con SQL_POSITION per impostare la posizione del cursore; quindi, per ogni colonna non associata:  
  
    -   Chiamare [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) uno o più volte per ottenere i dati per le colonne non associate dopo l'ultima colonna del set di righe associata. Le chiamate a [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) deve essere in ordine crescente di numero di colonna.  
  
    -   Chiamare [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) più volte per ottenere dati da una colonna di tipo text o image.  
  
4.  Configurare tutte le colonne data-at-execution di tipo text o image.  
  
5.  Chiamare [SQLSetPos](http://go.microsoft.com/fwlink/?LinkId=58407) o [SQLBulkOperations](http://go.microsoft.com/fwlink/?LinkId=58398) per impostare la posizione del cursore, aggiornare, aggiornare, eliminare o aggiungere righe nel set di righe.  
  
     Se si utilizzano colonne data-at-execution di tipo text o image per un'operazione di aggiornamento o di aggiunta, è necessario gestirle.  
  
6.  Facoltativamente, eseguire un'istruzione di UPDATE o DELETE posizionata, specificando il nome del cursore (disponibile da [SQLGetCursorName](../../../relational-databases/native-client-odbc-api/sqlgetcursorname.md)) e l'utilizzo di un handle di istruzione diverso nella stessa connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle procedure per cursori &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)  
  
  
