---
title: Elaborazione posizionato istruzioni Update e Delete | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- SQL statements [ODBC], cursor library
- ODBC cursor library [ODBC], positioned update or delete
- cursor library [ODBC], statement processing
ms.assetid: 2975dd97-48e6-4d0a-a9c7-40759a7d94c8
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1127c03853ab74cbd51368abb90c9581363f4bd0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="processing-positioned-update-and-delete-statements"></a>Elaborazione posizionato istruzioni Update e Delete
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 Supporta la libreria il cursore posizionato istruzioni update e delete sostituendo il **WHERE CURRENT OF** clausola in queste istruzioni con un **dove** clausola che enumera i valori memorizzati nella cache per ogni colonna associata. La libreria di cursori passa appena costruita **aggiornamento** e **eliminare** istruzioni per il driver per l'esecuzione. Per le istruzioni di aggiornamento posizionato, la libreria di cursori Aggiorna la cache dai valori nei buffer di set di righe e imposta il valore corrispondente nella matrice di stato di riga da SQL_ROW_UPDATED. Per le istruzioni delete posizionata, imposta il valore corrispondente nella matrice di stato di riga da SQL_ROW_DELETED.  
  
> [!CAUTION]  
>  Il **dove** clausola costruito dalla libreria di cursori per identificare la riga corrente può avere esito negativo identificare le righe, identificare una riga diversa o più di una riga. Per ulteriori informazioni, vedere [la costruzione di istruzioni di ricerca](../../../odbc/reference/appendixes/constructing-searched-statements.md), più avanti in questa appendice.  
  
 Posizionato update e delete istruzioni sono soggetti alle restrizioni seguenti:  
  
-   Posizionato update e delete istruzioni possono essere utilizzate solo nei seguenti casi: quando un **selezionare** istruzione ha generato il set di risultati; quando il **selezionare** istruzione non contiene un join, un  **UNIONE** clausola, o un **GROUP BY** clausola; e quando non sono associate le colonne di cui è utilizzato un alias o un'espressione nell'elenco di selezione con **SQLBindCol**.  
  
-   Se un'applicazione prepara un'istruzione delete o un aggiornamento posizionato, deve essere eseguita dopo aver chiamato **SQLFetch** o **SQLFetchScroll**. Anche se la libreria di cursori invia l'istruzione per il driver per la preparazione, chiude l'istruzione e viene eseguito direttamente quando l'applicazione chiama **SQLExecute**.  
  
-   Se il driver supporta solo un'istruzione attiva, le operazioni di recupero libreria cursore il resto del risultato set e recupera quindi nuovamente il set di righe corrente dalla cache prima di eseguire un posizionamento istruzioni update o delete. Se l'applicazione chiama quindi una funzione che restituisce i metadati in un set di risultati (ad esempio, **SQLNumResultCols** o **SQLDescribeCol**), la libreria di cursori restituisce un errore.  
  
-   Se un aggiornamento posizionato o l'istruzione delete viene eseguita su una colonna di una tabella che include una colonna timestamp viene aggiornata automaticamente ogni volta che viene eseguito un aggiornamento, tutte le successive per gli aggiornamenti posizionati o le istruzioni delete avrà esito negativo se la colonna timestamp associato. Questo errore si verifica perché la ricerca di Aggiorna o Elimina istruzione che crea la libreria di cursori non identifica in modo accurato la riga da aggiornare. Il valore viene eseguita l'istruzione per la colonna timestamp non corrisponderà al valore di aggiornamento automatico della colonna timestamp.
