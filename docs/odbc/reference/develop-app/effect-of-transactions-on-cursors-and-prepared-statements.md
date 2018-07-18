---
title: Effetto delle transazioni su cursori e le istruzioni preparate | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- cursors [ODBC], transaction commits or roll backs
- prepared statements [ODBC]
- transactions [ODBC], cursors
ms.assetid: 523e22a2-7b53-4c25-97c1-ef0284aec76e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ceb7aaae6967376c454d32633cda6043bc281825
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>Effetto delle transazioni su cursori e le istruzioni preparate
Il commit o il rollback di una transazione ha l'effetto seguente su cursori e i piani di accesso:  
  
-   Tutti i cursori vengono chiusi, e vengono eliminati i piani di accesso per le istruzioni preparate in tale connessione.  
  
-   Tutti i cursori vengono chiusi e i piani di accesso per le istruzioni preparate in tale connessione rimangono invariati.  
  
-   Tutti i cursori rimangono aperti e i piani di accesso per le istruzioni preparate in tale connessione rimangono invariati.  
  
 Si supponga, ad esempio, che un'origine dati mostra il comportamento prima nell'elenco di questi comportamenti più restrittivo. Ora si supponga che un'applicazione esegue le operazioni seguenti:  
  
1.  Imposta la modalità di commit di commit manuale.  
  
2.  Crea un set di risultati di ordini di vendita nell'istruzione 1.  
  
3.  Crea un set di risultati delle righe in un ordine di vendita nell'istruzione 2, quando l'utente evidenzia tale ordine.  
  
4.  Chiamate **SQLExecute** per eseguire un'istruzione di aggiornamento posizionato che è stata preparata l'istruzione 3, quando l'utente aggiorna una riga.  
  
5.  Chiamate **SQLEndTran** per eseguire il commit dell'istruzione di aggiornamento posizionato.  
  
 A causa di un comportamento dell'origine dati, la chiamata a **SQLEndTran** nel passaggio 5 provoca per chiudere i cursori nelle istruzioni 1 e 2 ed eliminare il piano di accesso su tutte le istruzioni. L'applicazione deve rieseguito il set di istruzioni 1 e 2 per ricreare il risultato e reprepare l'istruzione nell'istruzione 3.  
  
 In modalità autocommit, le funzioni diverse da **SQLEndTran** il commit delle transazioni:  
  
-   **SQLExecute** oppure **SQLExecDirect** nell'esempio precedente, la chiamata a **SQLExecute** nel passaggio 4 esegue il commit di una transazione. In questo modo l'origine dati chiudere i cursori nelle istruzioni 1 e 2 ed eliminare il piano di accesso su tutte le istruzioni in tale connessione.  
  
-   **SQLBulkOperations** oppure **SQLSetPos** nell'esempio precedente, si supponga che nel passaggio 4 l'applicazione chiama **SQLSetPos** con l'opzione SQL_UPDATE nell'istruzione 2, anziché eseguire una istruzione di aggiornamento posizionato nell'istruzione 3. Questo viene eseguito il commit di una transazione e fa sì che l'origine dati chiudere i cursori nelle istruzioni 1 e 2 ed Elimina tutti i piani di accesso su tale connessione.  
  
-   **SQLCloseCursor** nell'esempio precedente, si supponga che quando si evidenzia un ordine di vendita diverso, l'applicazione chiama **SQLCloseCursor** nell'istruzione 2 prima di creare un risultato delle righe per le nuove vendite ordine. La chiamata a **SQLCloseCursor** viene eseguito il commit di **selezionare** istruzione che creato il set di risultati delle righe e fa sì che l'origine dati chiudere il cursore sull'istruzione 1 e quindi rimuove tutti i piani di accesso su quel connessione.  
  
 Le applicazioni, specialmente su schermo in cui l'utente scorre il set di risultati e gli aggiornamenti o Elimina le righe, necessario prestare attenzione al codice questo comportamento.  
  
 Per determinare il comportamento di un'origine dati quando una transazione viene eseguito il commit o rollback, un'applicazione chiama **SQLGetInfo** con le opzioni SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR.
