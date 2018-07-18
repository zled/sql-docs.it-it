---
title: Recuperare e aggiornare set di righe (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d41ba76ceaa157070fc2584c5ebd6d080f415420
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419470"
---
# <a name="fetch-and-update-rowsets-odbc"></a>Recuperare e aggiornare set di righe (ODBC)
    
### <a name="to-fetch-and-update-rowsets"></a>Per recuperare e aggiornare set di righe  
  
1.  Facoltativamente, è possibile chiamare [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) con SQL_ROW_ARRAY_SIZE per modificare il numero di righe (R) nel set di righe.  
  
2.  Chiamare [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) oppure [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) per ottenere un set di righe.  
  
3.  Se si utilizzano colonne associate, utilizzare i valori dei dati e le lunghezze dei dati disponibili nei buffer delle colonne associate per il set di righe.  
  
     Se si utilizzano colonne non associate, per ogni riga chiamare [SQLSetPos](http://go.microsoft.com/fwlink/?LinkId=58407) con SQL_POSITION per impostare la posizione del cursore; quindi, per ogni colonna non associata:  
  
    -   Chiamare [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) uno o più volte per ottenere i dati relativi alle colonne non associate dopo l'ultima colonna del set di righe associata. Le chiamate a [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) deve essere in ordine crescente numero di colonna.  
  
    -   Chiamare [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) più volte per ottenere dati da una colonna di tipo text o image.  
  
4.  Configurare tutte le colonne data-at-execution di tipo text o image.  
  
5.  Chiamare [SQLSetPos](http://go.microsoft.com/fwlink/?LinkId=58407) oppure [SQLBulkOperations](http://go.microsoft.com/fwlink/?LinkId=58398) per impostare la posizione del cursore, aggiornare, aggiornare, eliminare o aggiungere righe nel set di righe.  
  
     Se si utilizzano colonne data-at-execution di tipo text o image per un'operazione di aggiornamento o di aggiunta, è necessario gestirle.  
  
6.  Facoltativamente, eseguire un'istruzione di UPDATE o DELETE posizionata, specificando il nome del cursore (disponibile dal [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)) e l'utilizzo di un handle di istruzione diverso nella stessa connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Usando procedure per cursori &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)  
  
  
