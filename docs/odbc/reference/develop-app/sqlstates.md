---
title: SQLSTATE | Documenti Microsoft
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
- diagnostic information [ODBC], sqlstates
- SQLSTATE [ODBC]
ms.assetid: f29fff2e-3d09-4a8c-a2f9-2059062cbebf
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9408522a47b442e3001e09cdca2d636063f73fb5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlstates"></a>SQLSTATE
SQLSTATE forniscono informazioni dettagliate sulla causa di un avviso o errore. SQLSTATE in questo manuale sono basati su quelli nella specifica ISO/IEF CLI, anche se tali SQLSTATE che iniziano con IM sono specifici per ODBC.  
  
 A differenza dei codici restituiti, SQLSTATE in questo manuale sono linee guida e i driver non è necessario ripristinare le. Pertanto, mentre il driver devono restituire il valore SQLSTATE appropriato per qualsiasi errore o avviso che sono in grado di rilevare, le applicazioni non devono influire su questo sempre che si verificano. I motivi per cui questa situazione sono due:  
  
-   **Incompletezza** Sebbene questo manuale vengono elencate in un numero elevato di errori e avvisi e le possibili cause per tali errori e avvisi, non è completo e non sarà probabilmente mai; le implementazioni di driver semplicemente variare troppo elevato. Qualsiasi driver specificato potrebbe non restituire tutte le SQLSTATE elencati in questo manuale e potrebbe restituire SQLSTATE non è elencati in questo manuale.  
  
-   **Complessità** alcuni motori di database, ovvero motori di database relazionale in particolare, ovvero restituiscono migliaia di errori e avvisi. I driver per i motori di questo tipo sono improbabile che eseguire il mapping di tutti gli errori e avvisi da SQLSTATE a causa dello sforzo coinvolti, inexactness dei mapping, le dimensioni del codice risulta e il valore del codice risulta, che spesso restituisce programmazione basso errori che non devono essere mai rilevati in fase di esecuzione. Di conseguenza, i driver devono eseguire il mapping di molti errori e avvisi come sembra ragionevole e assicurarsi di eseguire il mapping di tali errori e avvisi in cui la logica dell'applicazione potrebbero essere basati, quali SQLSTATE 01004 (dati troncati).  
  
 Poiché SQLSTATE non vengono restituiti in modo affidabile, la maggior parte delle applicazioni solo visualizzano all'utente con il messaggio di diagnostica associato, spesso personalizzata in base a un messaggio di errore o avviso che si sono verificati e codice di errore nativo. Si verifica raramente alcuna perdita di funzionalità in questo modo, poiché le applicazioni non è possibile basare la logica di programmazione SQLSTATE la maggior parte delle comunque. Si supponga ad esempio **SQLExecDirect** restituisce SQLSTATE 42000 (sintassi o violazione di accesso). Se l'istruzione SQL che ha causato l'errore è hardcoded o creato dall'applicazione, si tratta di un errore di programmazione e il codice deve essere corretto. Se l'istruzione SQL viene immesso dall'utente, si tratta di un errore dell'utente e l'applicazione ha eseguito tutto ciò che è possibile informa l'utente del problema.  
  
 Quando le applicazioni di basare la logica di programmazione SQLSTATE, deve essere preparati per il valore SQLSTATE non deve essere restituito o per un diverso valore SQLSTATE da restituire. Esattamente quali SQLSTATE vengono restituiti in modo affidabile può essere basato solo sull'esperienza con numerosi driver. Tuttavia, in generale è che SQLSTATE per gli errori che si verificano nel driver o di gestione Driver, a differenza dell'origine dati, più possono da restituire in modo affidabile. Ad esempio, la maggior parte dei driver potrebbe restituire HYC00 SQLSTATE (funzionalità facoltativa non implementata), mentre un numero inferiore di driver potrebbe restituire SQLSTATE 42021 (esiste già una colonna).  
  
 I seguente SQLSTATE indicano errori di run-time o avvisi, sono buoni candidati su cui basare la logica di programmazione. Tuttavia, non c'è garanzia che li restituiscono tutti i driver.  
  
-   01004 (dati troncati)  
  
-   01S02 (valore di opzione modificato)  
  
-   HY008 (operazione annullata)  
  
-   HYC00 (funzionalità facoltativa non implementata)  
  
-   HYT00 (Timeout scaduto)  
  
 SQLSTATE HYC00 (funzionalità facoltativa non implementata) è particolarmente importante perché è l'unico modo in cui un'applicazione può determinare se un driver supporta un particolare attributo di istruzione o una connessione.  
  
 Per un elenco completo di SQLState e restituiranno quali funzioni, vedere [codici di errore ODBC appendice a:](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md). Per una spiegazione dettagliata delle condizioni in cui ogni funzione potrebbe restituire un valore SQLSTATE specifico, vedere la funzione.
