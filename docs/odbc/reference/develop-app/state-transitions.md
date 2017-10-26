---
title: Transizioni di stato | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- state transitions [ODBC]
- unallocated state [ODBC]
- handles [ODBC], state transitions
- allocated state [ODBC]
- connection state [ODBC]
ms.assetid: fc741611-6535-43cc-8156-6d897d04664e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 42aedfe48871b04b311fb5de31fb9866e0e2468c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="state-transitions"></a>Transizioni di stato
ODBC definisce discreti *stati* per ogni ambiente, ogni connessione e ogni istruzione. Ad esempio, l'ambiente ha tre stati possibili: non allocato (in cui non è allocato alcun ambiente), allocato (in cui viene allocato un ambiente ma non le connessioni vengono allocate) e connessione (in cui un ambiente e una o più connessioni sono allocato). Le connessioni sono sette possibili stati; le istruzioni sono stati possibili 13.  
  
 Un particolare elemento, identificato dal relativo handle, viene spostato da uno stato a un altro quando l'applicazione chiama una determinata funzione o funzioni e passa l'handle a quell'elemento. Lo spostamento di questo tipo viene chiamato un *transizione dello stato*. Ad esempio, allocare un handle di ambiente con **SQLAllocHandle** Sposta l'ambiente da non allocata a allocato e liberare l'handle con **SQLFreeHandle** restituisce da allocato a Non allocato. ODBC definisce un numero limitato di transizioni di stato validi, ovvero in altre parole che funzioni devono essere chiamate in un determinato ordine.  
  
 Alcune funzioni, ad esempio **SQLGetConnectAttr**, influisce sullo stato affatto. Altre funzioni influenzano lo stato di un singolo elemento. Ad esempio, **SQLDisconnect** sposta una connessione da uno stato di connessione a uno stato allocato. Infine, alcune funzioni influenzano lo stato di più di un elemento. Ad esempio, allocare un handle di connessione con **SQLAllocHandle** sposta di una connessione da un non allocata a uno stato allocato e lo sposta da un allocato a uno stato di connessione.  
  
 Se un'applicazione chiama una funzione non in ordine, la funzione restituisce un *errore transizione di stato*. Ad esempio, se un ambiente è in uno stato di connessione e l'applicazione chiama **SQLFreeHandle** con tale handle di ambiente, **SQLFreeHandle** restituisce SQLSTATE HY010 (funzione di errore nella sequenza), Poiché può essere chiamato solo quando l'ambiente è in uno stato allocato. Definendo ciò come una transizione di stato non valido, ODBC impedisce all'applicazione di liberare l'ambiente mentre vi sono connessioni attive.  
  
 Alcune transizioni di stato sono inerenti la progettazione di ODBC. Non è ad esempio, possibile allocare un handle di connessione senza prima di allocare un handle di ambiente, perché la funzione che consente di allocare un handle di connessione richiede un handle di ambiente. Altre transizioni di stato vengono applicate da Gestione Driver e i driver. Ad esempio, **SQLExecute** esegue un'istruzione preparata. Se l'handle di istruzione passato a non è in uno stato preparato, **SQLExecute** restituisce SQLSTATE HY010 (funzione di errore nella sequenza).  
  
 Dal punto di vista dell'applicazione, le transizioni di stato sono in genere semplici: le transizioni di stato validi tendono a passare in mano a mano con il flusso di un'applicazione ben scritta. Transizioni di stato sono più complesse per la gestione di Driver e i driver in quanto è necessario tenere traccia dello stato dell'ambiente, ogni connessione e ogni istruzione. La maggior parte di queste operazioni viene eseguita da Gestione Driver; la maggior parte del lavoro che deve essere eseguita dai driver si verifica con le istruzioni con risultati in sospeso.  
  
 Parti 1 e 2 del manuale ("Introduzione a ODBC" e "Sviluppo di applicazioni e i driver") non tendono a specificare esplicitamente le transizioni di stato. Al contrario, vengono descritte l'ordine in cui devono essere chiamate funzioni. Ad esempio, "Esecuzione di istruzioni" indica che un'istruzione deve essere preparata con **SQLPrepare** prima che possa essere eseguito con **SQLExecute**. Per una descrizione completa degli Stati e transizioni di stato, tra cui le transizioni vengono controllati da Gestione Driver e che devono essere controllate dal driver, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).

