---
title: "Prendere in considerazione le funzionalità di Database da utilizzare | Documenti Microsoft"
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
helpviewer_keywords: interoperability [ODBC], database features
ms.assetid: 59760114-508e-46c5-81d2-8f2498c0d778
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30b073e6bca1fee5b98ed835bcc72f127c9ad40c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="considering-database-features-to-use"></a>Prendere in considerazione le funzionalità di Database da utilizzare
Una volta noto il livello di base di interoperabilità, è necessario considerare le funzionalità del database utilizzate dall'applicazione. Ad esempio, le istruzioni SQL l'applicazione eseguirà? L'applicazione utilizzerà i cursori scorrevoli? Transazioni? Procedure? Dati di tipo Long? Per informazioni su quali funzionalità potrebbero non essere supportati da tutti i DBMS, vedere il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), e [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) le descrizioni delle funzioni e [ Appendice c: la grammatica SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Le funzionalità richieste da un'applicazione potrebbero eliminare alcuni DBMS dall'elenco di DBMS di destinazione. Si potrebbe anche essere indicato che l'applicazione può utilizzare facilmente DBMS più.  
  
 Ad esempio, se le funzionalità necessarie sono semplici, possono in genere essere implementate con un elevato livello di interoperabilità. Un'applicazione che esegue un semplice **selezionare** istruzione e recupera i risultati con cursori forward-only è probabile che sia estremamente interoperativi in virtù la semplicità: quasi tutti i driver e DBMS supportano la funzionalità, è necessario.  
  
 Tuttavia, se le funzionalità necessarie sono più complesse, ad esempio i cursori scorrevoli, per gli aggiornamenti posizionati e le istruzioni delete e procedure, vantaggi e svantaggi spesso dovuti. Esistono diverse possibilità:  
  
-   **Interoperabilità inferiore, altre funzionalità.** L'applicazione include le funzionalità ma funziona solo con DBMS che li supportano.  
  
-   **Maggiore interoperabilità, il numero di funzionalità.** L'applicazione elimina le funzionalità, ma può essere utilizzata con più DBMS.  
  
-   **Maggiore interoperabilità, le funzionalità facoltative.** L'applicazione include le funzionalità, ma sono disponibili solo con tali DBMS che li supportano.  
  
-   **Maggiore interoperabilità, altre funzionalità.** L'applicazione utilizza le caratteristiche con DBMS che li supportano e li emula per DBMS che non.  
  
 I primi due casi sono relativamente semplici da implementare, poiché le funzionalità vengono utilizzate con tutti i DBMS supportati o nessuna. Ultimi due casi, invece, sono più complessi. È necessario in entrambi i casi per verificare se il sistema DBMS supporta le funzionalità e nell'ultimo caso per scrivere una grande quantità di codice per emulare queste funzionalità. Di conseguenza, questi schemi sono potrebbe richiedere più tempo di sviluppo e potrebbero risultare più lenti in fase di esecuzione.  
  
 Si consideri un'applicazione di query generico in grado di connettersi a una singola origine dati. L'applicazione accetta una query da parte dell'utente e visualizza i risultati in una finestra. Ora si supponga che l'applicazione è una funzionalità che consente agli utenti di visualizzare i risultati di più query contemporaneamente. Ovvero sono può eseguire una query ed esaminare alcuni risultati eseguire una query diversa ed esaminare alcuni risultati del e quindi tornare alla prima query. Ciò rappresenta un problema di interoperabilità perché alcuni driver supporta solo una singola istruzione attiva.  
  
 L'applicazione dispone di un numero di scelte, in base a ciò che il driver restituisce per l'opzione SQL_MAX_CONCURRENT_ACTIVITIES in **SQLGetInfo**:  
  
-   **Supporta sempre più query.** Dopo la connessione a un driver, l'applicazione controlla il numero di istruzioni attive. Se il driver supporta solo un'istruzione attiva, l'applicazione chiude la connessione e avvisa l'utente che il driver non supporta la funzionalità richiesta. L'applicazione è facile da implementare e ha le funzionalità complete ma interoperabilità inferiore.  
  
-   **Non supporta più query.** L'applicazione elimina completamente la funzionalità. È facile da implementare e ha interoperabilità elevata ma dispone di meno funzionalità.  
  
-   **Supporta più query solo se il driver non.** Dopo la connessione a un driver, l'applicazione controlla il numero di istruzioni attive. L'applicazione consente all'utente di avviare una nuova istruzione quando è già attivo solo se il driver supporta più istruzioni attive. L'applicazione dispone di più funzionalità e l'interoperabilità, ma è più difficile da implementare.  
  
-   **Quando è necessario emulare sempre supporta più query.** Dopo la connessione a un driver, l'applicazione controlla il numero di istruzioni attive. Sempre l'applicazione consente all'utente di avviare una nuova istruzione quando è già attivo. Se il driver supporta solo un'istruzione attiva, l'applicazione apre una connessione aggiuntiva per il driver ed esegue l'istruzione di nuovo su tale connessione. L'applicazione dispone di funzionalità complete e interoperabilità elevata ma è più difficile da implementare.
