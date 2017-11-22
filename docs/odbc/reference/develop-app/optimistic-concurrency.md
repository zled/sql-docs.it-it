---
title: Concorrenza ottimistica | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- optimistic concurrency [ODBC]
ms.assetid: 9d71e09e-bc68-4c1f-9229-ed2a7be7d324
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 422f16155f79b61a7cc46516d8a4e7deb2fe19f9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="optimistic-concurrency"></a>Concorrenza ottimistica
*Concorrenza ottimistica* il relativo nome deriva dal presupposto ottimistico che raramente si verificheranno conflitti tra le transazioni, viene definito un conflitto si sono verificati quando un'altra transazione aggiorna o elimina una riga di dati tra il momento in cui è in lettura la transazione corrente e l'ora venga aggiornato o eliminato. È l'opposto di *concorrenza pessimistica,* o di blocco, in cui lo sviluppatore dell'applicazione ritiene che tali conflitti siano comuni.  
  
 Nella concorrenza ottimistica, una riga viene sbloccato fino a quando l'ora di aggiornare o eliminare. A questo punto, la riga viene letto nuovamente e controllata per verificare se è stato modificato dopo l'ultima lettura. Se la riga è stata modificata, l'aggiornamento o eliminazione di ha esito negativo e deve essere eseguito un nuovo tentativo.  
  
 Per determinare se una riga è stata modificata, la nuova versione viene confrontata con una versione della riga memorizzata nella cache. Questo controllo può essere basato sulla versione di riga, ad esempio la colonna timestamp SQL Server o i valori di ogni colonna nella riga. Molti DBMS non supportano le versioni di riga.  
  
 Concorrenza ottimistica può essere implementata da origine dati o l'applicazione. In entrambi i casi, l'applicazione deve utilizzare un livello di isolamento basso, ad esempio Read Committed; utilizzo di un livello superiore Nega l'aumento della concorrenza derivanti dall'uso della concorrenza ottimistica.  
  
 Se la concorrenza ottimistica viene implementata dall'origine dati, l'applicazione imposta l'attributo di istruzione SQL_ATTR_CONCURRENCY su SQL_CONCUR_ROWVER o SQL_CONCUR_VALUES. Per aggiornare o eliminare una riga, viene eseguito un aggiornamento posizionato o istruzione delete o chiamate **SQLSetPos** esattamente come con la concorrenza pessimistica; il driver o l'origine dati restituisce SQLSTATE 01001 (conflitto dell'operazione del cursore) se il Update o delete ha esito negativo a causa di un conflitto.  
  
 Se l'applicazione stessa implementa la concorrenza ottimistica, imposta l'attributo di istruzione SQL_ATTR_CONCURRENCY su SQL_CONCUR_READ_ONLY per leggere una riga. Se verranno confrontate le versioni di riga e non dispone di una colonna della versione di riga, chiama **SQLSpecialColumns** con l'opzione SQL_ROWVER per determinare il nome della colonna.  
  
 L'applicazione aggiorna o elimina la riga, aumentando la concorrenza SQL_CONCUR_LOCK (per ottenere l'accesso in scrittura per la riga) e l'esecuzione di un **aggiornamento** o **eliminare** istruzione con un **in**  clausola che specifica la versione o i valori della riga era quando l'applicazione leggerlo. Se la riga è stata modificata da allora, l'istruzione avrà esito negativo. Se il **dove** clausola non identifica in modo univoco la riga, l'istruzione può anche aggiornare o eliminare le altre righe mentre le versioni di riga identificano sempre in modo univoco le righe, ma i valori di riga identificano in modo univoco le righe solo se includono la chiave primaria.
