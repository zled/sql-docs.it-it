---
title: 'Appendice f: libreria di cursori ODBC | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- cursor library [ODBC]
ms.assetid: a03084df-4e48-48ef-917d-4a3fae48a605
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8aafc1a3ce481e4777ea216057ef2c0b7b24a2e8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="appendix-f-odbc-cursor-library"></a>Appendice f: libreria di cursori ODBC
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 La libreria di cursori ODBC (Odbccr32) supporta i cursori scorrevoli di blocco per un driver conforme con il livello di conformità di API di livello 1 e può essere ridistribuita dagli sviluppatori con le applicazioni o i driver. La libreria di cursori supporta anche le istruzioni di eliminazione e aggiornamento posizionato per set di risultati generati da **selezionare** istruzioni. Anche se supporta solo cursori statici e forward-only, la libreria di cursori soddisfa le esigenze di molte applicazioni. Inoltre, può fornire buone prestazioni, soprattutto per i set di risultati di piccole e medie dimensioni medio-piccole e per le applicazioni che non dispongono di supporto del cursore valido.  
  
 La libreria di cursori è una libreria a collegamento dinamico (DLL) che si trova tra gestione Driver e il driver. Quando un'applicazione chiama una funzione, gestione Driver chiama la funzione nella libreria di cursore, che viene eseguita la funzione o chiama tale driver specificato. Per una determinata connessione, un'applicazione specifica se la libreria di cursori viene sempre utilizzata, utilizzata se il driver non supporta i cursori scorrevoli o mai utilizzata.  
  
 La libreria di cursori viene visualizzato come un driver a gestione Driver. Se la libreria di cursori si trova tra gestione Driver e una di ODBC 2. *x* driver, la libreria di cursori viene visualizzato come un ODBC 2. *x* driver. Se la libreria di cursori si trova tra gestione Driver e un'applicazione ODBC 3*x* driver, la libreria di cursori viene visualizzato come un'applicazione ODBC 3*x* driver. Comportamento anomalo dalla libreria di cursori dipende dalla versione del driver che funziona con, fatta eccezione per gli offset di associazione, è supportata per entrambi ODBC 2. *x* e ODBC 3. *x* driver.  
  
 Per implementare cursori a blocchi in **SQLFetch** e **SQLFetchScroll**, la libreria di cursori chiama ripetutamente **SQLFetch** nel driver. Per implementare lo scorrimento, memorizza nella cache i dati che sono recuperati in memoria e nei file su disco. Quando un'applicazione richiede un nuovo set di righe, la libreria di cursori recuperato in base alle esigenze dal driver o dalla cache.  
  
 Per implementare l'aggiornamento posizionato e istruzioni delete, la libreria di cursori costruisce un **aggiornare** o **eliminare** istruzione con un **dove** clausola che specifica memorizzato nella cache valore di ogni colonna associata nella riga. Quando viene eseguita un'istruzione di aggiornamento posizionato, la libreria di cursori Aggiorna la cache dai valori nei buffer di set di righe.  
  
 Per ulteriori informazioni sulla libreria di cursori ODBC, vedere le sezioni seguenti di questa appendice:  
  
-   [Uso della libreria di cursori ODBC](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [Esecuzione di istruzioni di eliminazione e aggiornamento posizionato](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [Esempio di codice della libreria di cursori](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [Note di implementazione](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [Codici di errore della libreria di cursori ODBC](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
