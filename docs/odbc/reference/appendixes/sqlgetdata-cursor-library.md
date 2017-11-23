---
title: SQLGetData (libreria di cursori) | Documenti Microsoft
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
helpviewer_keywords: SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2024b9943f11877b38773cecaa59027867a31d1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLGetData** funzione nella libreria di cursori. Per informazioni generali su **SQLGetData**, vedere [funzione SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 La libreria di cursori implementa **SQLGetData** costruendo prima un **selezionare** istruzione con un **dove** clausola che enumera i valori memorizzati nella cache per ogni associazione colonna nella riga corrente. Viene quindi eseguita la **selezionare** selezionare di nuovo la riga e chiama l'istruzione **SQLGetData** nel driver per recuperare i dati dall'origine dati (a differenza della cache).  
  
> [!CAUTION]  
>  Il **dove** clausola costruito dalla libreria di cursori per identificare la riga corrente può avere esito negativo identificare le righe, identificare una riga diversa o più di una riga. Per ulteriori informazioni, vedere [la costruzione di istruzioni di ricerca](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Se l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS è impostato su SQL_UB_VARIABLE, **SQLGetData** può essere chiamato su una colonna 0 per restituire i dati di segnalibro.  
  
 Le chiamate a **SQLGetData** sono soggetti alle restrizioni seguenti:  
  
-   **SQLGetData** non può essere chiamato per i cursori forward-only.  
  
-   **SQLGetData** può essere chiamato solo quando vengono soddisfatte le condizioni seguenti: un **selezionare** istruzione ha generato il set di risultati; **selezionare** istruzione non contiene un join, un  **UNIONE** clausola, o un **GROUP BY** clausola; e le colonne di cui è utilizzato un alias o un'espressione nell'elenco di selezione non sono associate con **SQLBindCol**.  
  
-   Se il driver supporta solo un'istruzione attiva, la libreria di cursori recupera il resto del gruppo di risultati prima di eseguire il **selezionare** istruzione e la chiamata **SQLGetData**.
