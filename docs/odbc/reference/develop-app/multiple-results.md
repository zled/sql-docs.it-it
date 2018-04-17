---
title: Più risultati | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLMoreResults function [ODBC], multiple results
- row counts [ODBC]
- multiple results [ODBC]
- result sets [ODBC], multiple results
- SQLGetInfo function [ODBC], multiple results
ms.assetid: a3c32e4b-8fe7-4a33-ae39-ae664001f315
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e408c76354f6a4c958ebd209bc3778d0175dcef0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="multiple-results"></a>Più risultati
Oggetto *risultato* è un valore restituito dall'origine dati dopo l'esecuzione di un'istruzione. ODBC sono disponibili due tipi di risultati: set di risultati e conteggio delle righe. *Conteggio delle righe* sono il numero di righe interessate da un'istruzione update, delete o insert di istruzione. Batch, descritto in [batch di istruzioni SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md), è possibile generare più risultati.  
  
 La tabella seguente elenca i **SQLGetInfo** opzioni un'applicazione utilizza per determinare se un'origine dati restituisce più risultati per ogni tipo di batch. In particolare, un'origine dati può restituire un conteggio delle righe solo per l'intero batch di istruzioni o conteggio delle righe singole per ogni istruzione nel batch. Nel caso di un'istruzione con di creazione di set di risultati eseguita con una matrice di parametri, l'origine dati può restituire un singolo set di risultati per tutti i set di parametri o singoli set di risultati per ogni set di parametri.  
  
|Tipo di batch|Conteggio delle righe|Set di risultati|  
|----------------|----------------|-----------------|  
|Batch esplicita|SQL_BATCH_ROW_COUNT [a]|-[b].|  
|Procedura|SQL_BATCH_ROW_COUNT [a]|-[b].|  
|Matrici di parametri|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] riga conteggio: generazione di istruzioni in un batch potrebbero essere più supportate, ma la restituzione dei conteggi delle righe non è supportato. L'opzione SQL_BATCH_SUPPORT in **SQLGetInfo** indica se sono consentite istruzioni di generazione: numero di righe in batch; l'opzione SQL_BATCH_ROW_COUNTS indica se i totali di riga vengono restituiti all'applicazione.  
  
 [b] batch esplicita e procedure restituiscono sempre più set di risultati quando si includono più istruzioni di creazione di set di risultati.  
  
> [!NOTE]  
>  L'opzione SQL_MULT_RESULT_SETS introdotta in ODBC 1.0 fornisce solo informazioni che possono essere restituiti più set di risultati. In particolare, è impostata su "Y" se vengono restituiti i bit SQL_BS_SELECT_EXPLICIT o SQL_BS_SELECT_PROC per SQL_BATCH_SUPPORT o se viene restituito SQL_PAS_BATCH per SQL_PARAM_ARRAYS_SELECT.  
  
 Per elaborare più risultati, un'applicazione chiama **SQLMoreResults**. Questa funzione Elimina il risultato corrente e rende disponibile il risultato successivo. Restituisce SQL_NO_DATA quando non sono più disponibili. Si supponga, ad esempio, che le istruzioni seguenti vengono eseguite come un batch:  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 Dopo l'esecuzione di queste istruzioni, l'applicazione recupera righe dal set di risultati creati il **selezionare** istruzione. Al termine, recupero di righe chiama **SQLMoreResults** per rendere disponibile il numero di parti che sono stati repriced. Se necessario, **SQLMoreResults** Elimina le righe non recuperate e chiude il cursore. L'applicazione chiama quindi **SQLRowCount** per determinare quante parti sono state repriced dal **aggiornamento** istruzione.  
  
 È specifico del driver è esecuzione dell'istruzione dell'intero batch prima che i risultati siano disponibili. In alcune implementazioni, questo è il caso: in altri, la chiamata **SQLMoreResults** attiva l'esecuzione dell'istruzione successiva nel batch.  
  
 Se una delle istruzioni in un batch ha esito negativo, **SQLMoreResults** restituirà SQL_ERROR o SQL_SUCCESS_WITH_INFO. Se il batch è stato interrotto quando l'istruzione non è riuscita o l'istruzione non riuscita era l'ultima istruzione nel batch, **SQLMoreResults** restituirà SQL_ERROR. Se il batch non è stato interrotto quando l'istruzione non è riuscita e l'istruzione non riuscita non è stata l'ultima istruzione nel batch, **SQLMoreResults** restituirà SQL_SUCCESS_WITH_INFO. SQL_SUCCESS_WITH_INFO indica che è stato generato almeno un set di risultati o conteggio e che il batch non è stato interrotto.
