---
title: Handle di istruzione | Documenti Microsoft
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
- statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 64c949c8b3b3c794d6089ff159e597aeec02cfed
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="statement-handles"></a>Handle di istruzione
Oggetto *istruzione* è più facilmente considerato come un'istruzione SQL, ad esempio **selezionare \* dipendente da**. Tuttavia, un'istruzione è molto più di un'istruzione SQL, è costituito da tutte le informazioni associate a tale istruzione SQL, ad esempio qualsiasi set di risultati creati tramite l'istruzione e i parametri utilizzati durante l'esecuzione dell'istruzione. Un'istruzione non è nemmeno necessario disporre di un'istruzione SQL definita dall'applicazione. Ad esempio, quando una funzione di catalogo, ad esempio **SQLTables** viene eseguita in un'istruzione, viene eseguita un'istruzione SQL predefinita che restituisce un elenco di nomi di tabella.  
  
 Ogni istruzione è identificato da un handle di istruzione. Un'istruzione è associata a una singola connessione, e possono essere presenti più istruzioni in tale connessione. Alcuni driver limitare il numero di istruzioni attive che supportano; opzione di SQL_MAX_CONCURRENT_ACTIVITIES **SQLGetInfo** specifica il numero di istruzioni attive supporta un driver in un'unica connessione. Un'istruzione viene definita come *active* se è in attesa di risultati, in cui risultati sono un set di risultati o il numero di righe interessate da un **inserire**, **aggiornamento**, o **Eliminare** istruzione o i dati inviati con più chiamate a **SQLPutData**.  
  
 All'interno di un frammento di codice che implementa ODBC (Driver Manager o un driver), l'handle di istruzione identifica una struttura contenente informazioni sull'istruzione, ad esempio:  
  
-   Stato dell'istruzione  
  
-   La diagnostica a livello di istruzione corrente  
  
-   Gli indirizzi delle variabili di applicazione associate ai parametri dell'istruzione e generare un set di colonne  
  
-   Le impostazioni correnti di ogni attributo di istruzione  
  
 Handle di istruzione vengono utilizzati nella maggior parte delle funzioni ODBC. In particolare, vengono utilizzati nelle funzioni per i parametri di associazione e causare un set di colonne (**SQLBindParameter** e **SQLBindCol**), preparare ed eseguire le istruzioni (**SQLPrepare** **SQLExecute**, e **SQLExecDirect**), recuperare i metadati (**SQLColAttribute** e **SQLDescribeCol**), recupero risultati (**SQLFetch**) e recuperare dati diagnostici (**SQLGetDiagField** e **SQLGetDiagRec**). Vengono inoltre utilizzati nelle funzioni di catalogo (**SQLColumns**, **SQLTables**e così via) e un numero di altre funzioni.  
  
 Handle di istruzione vengono allocati con **SQLAllocHandle** e liberata con **SQLFreeHandle**.

