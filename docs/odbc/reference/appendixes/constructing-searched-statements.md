---
title: La costruzione di istruzioni ricerca | Documenti Microsoft
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
- searched statements [ODBC]
- ODBC cursor library [ODBC], statement processing
- ODBC cursor library [ODBC], searched statements
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- cursor library [ODBC], searched statements
- SQL statements [ODBC], searched statements
ms.assetid: e429254c-c43f-4fbf-98b2-5f1ed53501ff
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 90464acc97539252ae24aa6f959c16f58465d715
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="constructing-searched-statements"></a>Costruzione di istruzioni di ricerca
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 Per il supporto per gli aggiornamenti posizionati e istruzioni delete, la libreria di cursori costruisce una ricerca **aggiornare** o **eliminare** istruzione dall'istruzione posizionato. Per supportare le chiamate a **SQLGetData** in un blocco di dati, la libreria di cursori costruisce una ricerca **selezionare** impostata di istruzione per creare un risultato che contiene la riga corrente di dati. In ognuna di queste istruzioni, il **in** clausola enumera i valori memorizzati nella cache per ogni colonna associata che restituisce SQL_PRED_SEARCHABLE o SQL_PRED_BASIC per l'identificatore di campo SQL_DESC_SEARCHABLE in ** SQLColAttribute**.  
  
> [!CAUTION]  
>  Il **dove** clausola costruito dalla libreria di cursori per identificare la riga corrente può avere esito negativo identificare le righe, identificare una riga diversa o più di una riga.  
  
 Se un'istruzione delete o un aggiornamento posizionato interessa più righe, la libreria di cursori Aggiorna la matrice di stato di riga solo per la riga in cui è posizionato il cursore e restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01001 (conflitto dell'operazione del cursore). Se l'istruzione non identifica tutte le righe, la libreria di cursori non aggiorna la matrice di stato di riga e restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01001 (conflitto dell'operazione del cursore). Un'applicazione può chiamare **SQLRowCount** per determinare il numero di righe che sono stati aggiornati o eliminati.  
  
 Se il **selezionare** clausola utilizzato per posizionare il cursore per una chiamata a **SQLGetData** identifica più di una riga, **SQLGetData** potrebbe non restituire i dati corretti. Se non identifica tutte le righe, **SQLGetData** restituisce SQL_NO_DATA.  
  
 Se un'applicazione è conforme alle seguenti linee guida, il **dove** clausola costruito dalla libreria di cursori deve identificare in modo univoco la riga corrente, tranne quando è possibile, ad esempio quando l'origine dati contiene duplicato righe.  
  
-   **Associare le colonne che identificano in modo univoco la riga.** Se le colonne associate non identificare in modo univoco la riga, il **dove** clausola costruito dalla libreria di cursori potrebbe identificare più di una riga. In un'istruzione delete o un aggiornamento posizionato, questa clausola può causare più di una riga deve essere aggiornato o eliminato. In una chiamata a **SQLGetData**, tale clausola potrebbe causare il driver restituire i dati per la riga non corretto. Associazione di tutte le colonne in una chiave univoca garantisce che ogni riga viene identificato in modo univoco.  
  
-   **Allocare buffer di dati sufficientemente grande che si verifica il troncamento non.** La cache della libreria di cursori è una copia dei valori nei buffer di set di righe associato al set di risultati con **SQLBindCol**. Quando viene inserito in questi buffer i dati vengono troncati, verrà troncato anche nella cache. Oggetto **dove** clausola costruito dai valori troncati potrebbe non identificare correttamente riga nell'origine dati sottostante.  
  
-   **Specificare il buffer di lunghezza non null per i dati binari di C.** La libreria di cursori alloca i buffer di lunghezza nella relativa cache solo se il *StrLen_or_IndPtr* argomento **SQLBindCol** è diverso da null. Quando il *TargetType* argomento SQL_C_BINARY, la libreria di cursori richiede la lunghezza dei dati binari per costruire un **dove** clausola dai dati. Se non vi è alcun buffer di lunghezza per una colonna SQL_C_BINARY e l'applicazione chiama **SQLGetData** o tenta di eseguire un aggiornamento posizionato o eliminare l'istruzione, la restituisce libreria cursore SQL_ERROR e SQLSTATE SL014 (un oggetto posizionato richiesta è stata rilasciata e non tutti i campi numero di colonna sono stati memorizzati nel buffer).  
  
-   **Specificare il buffer di lunghezza non null per le colonne che ammettono valori null.** La libreria di cursori alloca i buffer di lunghezza nella relativa cache solo se il *StrLen_or_IndPtr* argomento **SQLBindCol** è diverso da null. Poiché SQL_NULL_DATA viene memorizzata nel buffer di lunghezza, la libreria di cursori si presuppone che qualsiasi colonna per la cui lunghezza non viene specificato il buffer non nullable. Se per una colonna che ammette valori null non è specificata alcuna colonna di lunghezza, la libreria di cursori costruisce una **dove** clausola che utilizza il valore dei dati per la colonna. Questa clausola non identificherà correttamente la riga.

